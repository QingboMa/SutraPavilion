基于umi4 `https://umijs.org/docs/max/access`

## umijs的菜单配置

方式一在`.umirc.ts`中配置菜单

路由格式：

```ts
 {
      name: '反馈',
      path: '/feedback',
      component: './Feedback',
      // 新页面打开
      target: '_blank',
      // icon: 'testicon',
      // // 不展示顶栏
      // headerRender: false,
      // // 不展示页脚
      // footerRender: false,
      // // 不展示菜单,为false时，整个页面显示
      // menuRender: false,
      // // 不展示菜单顶栏
      // menuHeaderRender: false,
      // // 权限配置，需要与 plugin-access 插件配合使用
      // access: 'canRead',
      // 隐藏子菜单
      // hideChildrenInMenu: true,
      // 隐藏自己和子菜单
      hideInMenu: true,
      // // 在面包屑中隐藏
      // hideInBreadcrumb: true,
      // // 子项往上提，仍旧展示,
      // flatMenu: true,
    },
```



```ts
import { defineConfig } from '@umijs/max';

export default defineConfig({

  hash: true,
  antd: {

  },
  access: {},
  model: {

  },
  initialState: {

  },
  request: {},
  layout: {
    title: '永劫无间',

  },
  links: [
    {
      rel: 'icon',
      href: 'https://img.yostatic.com/ouyaoxiazai/202104/164d8e864c26d484b4b0749d42601300.png',
    },
  ],
  fastRefresh: true,
  title: '永劫无间赛季',
  routes: [
    {
      path: '/',
      redirect: '/competition/season',
    },
    {
      name: '赛季',
      path: '/competition/season',
      component: './CompetitionSeason',
      routes: [{ path: ':s', component: './CompetitionSeason/JkzEvent/S2' }],
    },
    {
      name: '英雄',
      path: '/heroes',
      // component: './Heroes',
      component: './Heroes/HeroLayout',
      routes: [
        { path: '/heroes/', component: './Heroes' },
        { path: '/heroes/info/:id', component: './Heroes/HeroInfo' },
      ]
    },
    {
      name: '武器',
      path: '/weapon',
      access: 'canRead',
      component: './Weapon',
    },
    {
      name: '反馈',
      path: '/feedback',
      component: './Feedback',
      // 新页面打开
      target: '_blank',
      // icon: 'testicon',
      // // 不展示顶栏
      // headerRender: false,
      // // 不展示页脚
      // footerRender: false,
      // // 不展示菜单,为false时，整个页面显示
      // menuRender: false,
      // // 不展示菜单顶栏
      // menuHeaderRender: false,
      // // 权限配置，需要与 plugin-access 插件配合使用
      // access: 'canRead',
      // 隐藏子菜单
      // hideChildrenInMenu: true,
      // 隐藏自己和子菜单
      hideInMenu: true,
      // // 在面包屑中隐藏
      // hideInBreadcrumb: true,
      // // 子项往上提，仍旧展示,
      // flatMenu: true,
    },
    {
      path: '/admin',
      redirect: '/admin/login',
    },
    {
      name: '系统配置',
      path: '/admin',
      component: './Admin',
      menuRender: false,
      // hideInMenu: true,
      routes: [
        { path: 'login', component: './Admin/Login' },
      ]
    }
  ],
  npmClient: 'yarn',
  proxy: {
    '/api': {
      'target': 'http://localhost:8080',
      'changeOrigin': true,
      'pathRewrite': { '^/api': '' },
    },
  },
});

```

### 菜单的权限

栗子：当当前用户角色为管理员时，系统配置菜单才可见

在src下新建`access.ts`(必须是src/access.ts)

```ts
// src/access.ts
/**
 * 
 * @param initialState initialState从app.ts接收
 * @returns 
 */
export default function (initialState: any) {
    const { userId, role } = initialState;

    return {
        //当role为admin时才可具有可读权限
        canRead: role === 'admin',
         //当role为admin时才可具有修改权限
        canUpdate: role === 'admin',
        canDeleteFoo: (foo: any) => {
            return foo.ownerId === userId;
        },
    };
}
```

access.ts中的初始化参数来自于app.ts的getInitialState函数的返回值。

```tsx
// 运行时配置
// 全局初始化数据配置，用于 Layout 用户信息和权限初始化
// 更多信息见文档：https://next.umijs.org/docs/api/runtime-config#getinitialstate

import { Button } from "antd";
import { FeedbackIcon } from "./components/Icon/FeedbackIcon";
import { useNavigate } from "@umijs/max";

export const layout = () => {
  const navigate = useNavigate()
  return {
    logo: 'https://img.yostatic.com/ouyaoxiazai/202104/164d8e864c26d484b4b0749d42601300.png',
    menu: {
      locale: true,
    },
    rightRender: () => <Button type="primary" onClick={() => { navigate('/feedback') }} style={{ "width": "100%" }}>反馈</Button>,
  };
};

// src/app.ts
/**
 * 
 * @returns https://v3.umijs.org/zh-CN/plugins/plugin-initial-state
 */
export async function getInitialState() {
  const data = await xxx()
  return data;
}
```

