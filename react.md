## Hooks

### useEffect

```js
 useEffect(() => {
        document.title = `You clicked ${count} times`;
  }, []);
```

第一个参数是函数，当页面渲染时会自动调用一次，第二个参数是一个空数组，如果第二个参数存在，那么第一个参数只会被执行一次

### useSearchParams()

见路由参数

### useParams()

见路由参数

### useLocation()

见路由参数

### useInRouterContext()

路由上下文，只要某个组件被BrowserRouter或者是HashRouter包裹，都会返回true

### useNavigationType()

1. 作用:返回当前的导航类型（用户如何来到当前页面的）

2. 返回值`POP`、`PUSH`、`REPLACE`

   备注：`POP`是指在浏览器中打开了这个路由组件，当再次刷新时，就是`POP`

### useOutLet()

找出当前组件中的渲染的嵌套路由

### useResolvedPath()

类似useLocation()

```tsx
 const resolvePath = useResolvedPath('/func/id=21')

 console.log(resolvePath);
```

## react-router v6

分别使用类组件和函数式组件来记录

### 路由参数

#### params参数

`router.tsx`

定义FuncComponent组件需要接收的参数 id

![image-20221226210157967](asset/react/pic/image-20221226210157967.png)

在Call组件分别调用函数式组件和类组件。路由跳转的时候将id传递给FuncComponent路由

```html  
<Link to={'/func/2'}><Button type='primary'>GO FUNC</Button></Link>|
<Link to={'/class/2'}><Button type="primary">GO CLASS</Button></Link>

```



1. 函数式组件FuncComponent

   使用hooks为` react-router-dom`的`useParams()`

```javascript
const params = useParams()
console.log(params.id);
```

2. 类组件ClassComponent

   // TODO 待查资料

#### search参数

不需要路由参数占位

![image-20221226211334871](asset/react/pic/image-20221226211334871.png)

在Call组件分别调用函数式组件和类组件。路由跳转的时候将id传递给`FuncComponent`路由

```html
<Link to={'/func?id=21'}><Button type='primary'>GO FUNC</Button></Link>|
<Link to={'/class?id=21'}><Button type="primary">GO CLASS</Button></Link>
```



1. 函数式组件`FuncComponent`

   使用hooks为` react-router-dom`的`useSearchParams()`

```javascript
const [search, setSearch] = useSearchParams()
console.log(search.get("id"));
```
`setSearch()`方法可以设置参数id的值：当点击 `setSearch`按钮时，路径参数的id变为34

```javascript

export default function FuncComponent() {
    const [search, setSearch] = useSearchParams()
    console.log(search.get("id"));
    return (
        <div>
            <Button  type='primary' onClick={() => setSearch('id=34')}>setSearch</Button>
        </div>
    )
}

```

2. 类组件`ClassComponent`

   // TODO 待查资料

#### state参数

不需要路由参数占位

![image-20221226211334871](asset/react/pic/image-20221226211334871.png)

在Call组件分别调用函数式组件和类组件。路由跳转的时候将id传递给FuncComponent路由

```html
<Link to={'/func'}><Button type='primary'>GO FUNC</Button></Link>|
<Link to={'/class'}><Button type="primary">GO CLASS</Button></Link>
```



1. 函数式组件FuncComponent

   使用hooks为`react-router-dom`的useLocation()

```javascript
const location = useLocation()
console.log(location.state.id);
```
location的属性![微信截图_20221226212901](asset/react/pic/微信截图_20221226212901.png)

可以通过解构赋值来获取state中的id属性。

`  const { state: { id } } = useLocation()`

也可以通过.的方式获取


2. 类组件ClassComponent

   // TODO 待查资料

### 编程式导航

编程式导航(不需要点击操作的路由跳转)。

| html标签 | react-ROuter6 | React-Router-5 |
| -------- | ------------- | -------------- |
| \<a>     | \<Link>       | \<Link>        |
| \<a>     | \<NavLink>    | \<NavLink>     |
|          | \<Navigate>   |                |

\<Navigate>  需要写在html标签中

在`js`中使用`react-router-dom`的`useNavigate()`

`  const navigate = useNavigate()`

navigate 可以接收两个参数`to`和`NavigateOptions`类型的`options`

navigate (to,options)

```typescript
/**
 * The interface for the navigate() function returned from useNavigate().
 */
export interface NavigateFunction {
    (to: To, options?: NavigateOptions): void;
    (delta: number): void;
}
```
options的类型有4个属性
```typescript
export interface NavigateOptions {
    replace?: boolean;
    //传递给组件的state，可以获取值
    state?: any;
    preventScrollReset?: boolean;
    relative?: RelativeRoutingType;
}
```

使用栗子，跳转到`/func`路由时，使用**state参数**携带参数id=22

```tsx
import React from 'react'
import { NavigateOptions, useLocation } from 'react-router-dom';
import { useNavigate } from 'react-router-dom';
import { Button } from 'antd';
export default function FuncComponent() {
    const navigate = useNavigate()
    const option: NavigateOptions = {
        replace: false,
        state: {
            id: 222
        }
    }
    return (
        <div>
            <Button onClick={() => navigate('/func', option)}>GO FUNC</Button>
        </div>
    )
}
```

FuncComponent

```tsx
import React from 'react'
import { useLocation } from 'react-router-dom';
export default function FuncComponent() {
    const location = useLocation()
    console.log(location.state);
    return (
        <div>
        </div>
    )
}
```

`tips`:使用param参数和search参数，可以直接使用`navigate('/func/2')`或者`navigate('/func?id=2')`传递

## Redux

状态管理js库，Vue也可以使用，如vuex或者pinia,redux。

redux管理多个组件的共享数据

![image-20221226224110447](asset/react/pic/image-20221226224110447.png)

### Redux 三大原则

理解好 Redux 有助于我们更好的理解接下来的 React -Redux

##### 第一个原则

**单向数据流**：整个 Redux 中，数据流向是单向的

UI 组件 ---> action ---> store ---> reducer ---> store

##### 第二个原则

**state 只读**：在 Redux 中不能通过直接改变 state ，来控制状态的改变，如果想要改变 state ，则需要触发一次 action。通过 action 执行 reducer

##### 第三个原则

**纯函数执行**：每一个reducer 都是一个纯函数，不会有任何副作用，返回是一个新的 state，state 改变会触发 store 中的 subscribe