# Vue

## 概念

### `:`和`@`符号

“:” 是指令 “v-bind”的缩写，“@”是指令“v-on”的缩写；

`v-bind` 指令可以用于响应式地更新 HTML 特性：

​	和script中定义的变量双向绑定

```vue
<!-- 完整语法 -->
<a v-bind:href="url">...</a>
<!-- 缩写 -->
<a :href="url">...</a>
```



`v-on` 指令，它用于监听 DOM 事件：

​	如点击事件click

```vue
<!-- 完整语法 -->
<a v-on:click="doSomething">...</a>
<!-- 缩写 -->
<a @click="doSomething">...</a>
```

### `v-model`

`<input  v-model="mes">`等价于 `<input v-bind:value="mes"/>`

# vue-router

### 1、嵌套路由

```js
import { createRouter, createWebHistory } from 'vue-router'
import MainPage from '../views/MainPage.vue'
import Home from '../views/Home/index.vue'
import Business from '../views/Business/index.vue'
const router = createRouter({
  history: createWebHistory(import.meta.env.BASE_URL),
  routes: [
    {
      path: '/',
      name: 'main',
      component: MainPage,
      children: [
        {
          path: 'home',
          component: Home
        },
        {
          path: 'honors',
          name: 'honors',
          component: () => import('/src/views/Suhe/Honors.vue')
        }
      ]
    },
  ]
})

export default router

```



App.vue

第一层路由会路由到App.vue的`<router-view />` ,也可以写成`<RouterView/>`。上面路由文件中 ，当访问`/`路径时，会显示MainPage组件

```vue
<script setup>
	import { RouterView } from 'vue-router'
</script>
<template>
    <router-view />
</template>

```



MainPage.vue

二级路由的入口处，当访问`/honors时，会显示在Honors组件会显示在MainPage的`<router-view/>`中

```vue
<template>
  <el-container class="el-container ">
    <!-- 顶栏容器 -->
    <el-header>
      <Header />
    </el-header>
    <!-- 主要区域容器 -->
    <el-main>
      <div class="carouse">
        <router-view />
      </div>
    </el-main>
    <!-- 底栏容器 -->
    <el-footer>
      <Footer />
    </el-footer>
  </el-container>
</template>
```

### 2、路由跳转

1. useRouter

   useRouter 相当于vue2的this.$router全局的路由实例

   ```js
   const rt = useRouter(router)
   //跳转到honors页面
   rt.push('/honors')
   ```

   

# css

## div水平居中

`justify-content: center;`

```html
<!DOCTYPE html>
<html>
<head>
<style> 
#main {
  width: 400px;
  height: 100px;
  border: 1px solid #c3c3c3;
  display: flex;
  justify-content: center;
}

#main div {
  width: 70px;
  height: 70px;
}
</style>
</head>
<body>

<h1>justify-content 属性</h1>

<p>The "justify-content: center;" 在容器中央对齐弹性项目：</p>

<div id="main">
  <div style="background-color:coral;">1</div>
  <div style="background-color:lightblue;">2</div>
  <div style="background-color:pink;">3</div>
</div>

<p><b>注释：</b>Internet Explorer 10 以及更早的版本不支持 justify-content 属性。</p>

</body>
</html>

```



## video变成响应式

```html
    <video src="/src/assets/video/2.mp4" style="max-width: 100%; height: auto; " controls
                                    autoplay data-v-e0480da5="">您的浏览器不支持 video
                                    标签。 </video>
```





# 遇到的坑

### 1路由

![image-20221026000246910](asset/v3/pic/image-20221026000246910.png)

路由错误写法

```javascript
 {
              path: 'test',
              component: () => { import('/src/views/Suhe/Test.vue') },
              meta: {
                title: 'test'
              },
  }
```

正确写法

`component: () => import('/src/views/Suhe/Test.vue'),`

### 2日期格式化

*//获取当前时间*

`let deadTime: any = ref(new Date)`

//格式化当前时间

`deadTime = deadTime.value.toLocaleDateString()`

### 3、reactive 手动赋值后响应式丢失

#### 问题复现

定义

```javascript
var jobs = reactive({

    "records": [
        {
            "username": "liumingming@hq.cmcc",
            "priCode": "DTGH_ITGH_COMMON63"
        }
    ],
    "total": 13750,
    "size": 10,
    "current": 2,
    "orders": [],
    "optimizeCountSql": true,
    "hitCount": false,
    "countId": null,
    "maxLimit": null,
    "searchCount": true,
    "pages": 1375
})
```

引用地方，就是将这个数据中的records进行遍历，当按钮触发reload事件时会调用reload方法

```javascript
const reload = (pageNo?: number) => {
    console.log(pageNo);
    console.log(JSON.stringify(jobs));
    jobs = {
        "records": [
            {
                "username": "julun@hq.cmcc",
                "priCode": "DTGH_ITGH_COMMON63"
            }
        ],
        "total": 13750,
        "size": 10,
        "current": 3,
        "orders": [],
        "optimizeCountSql": true,
        "hitCount": false,
        "countId": null,
        "maxLimit": null,
        "searchCount": true,
        "pages": 1375
    }
    console.log(pageNo);
    console.log(JSON.stringify(jobs));
}
```



现在调用了reload方法，但是页面却没有自动刷新，还是老样子



#### 解决方法

在真实数据的外层包裹一层

```javascript
var jobs = reactive({
    data: {
        "records": [
            {
                "username": "liumingming@hq.cmcc",
                "priCode": "DTGH_ITGH_COMMON63"
            }
        ],
        "total": 13750,
        "size": 10,
        "current": 2,
        "orders": [],
        "optimizeCountSql": true,
        "hitCount": false,
        "countId": null,
        "maxLimit": null,
        "searchCount": true,
        "pages": 1375

    }
})
```

当需要改动时，改动 jobs.data的属性就可以完成响应式的数据了

