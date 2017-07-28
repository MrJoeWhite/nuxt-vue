# PAGES

This directory contains your Application Views and Routes.
The framework reads all the .vue files inside this directory and create the router of your application.

More information about the usage of this directory in the documentation:
https://nuxtjs.org/guide/routing

###set pages like:

```
pages/  
--| _slug/  
-----| comments.vue  
-----| index.vue  
--| users/  
-----| _id.vue  
--| index.vue
```

###will get:
```code
router: {
  routes: [
    {
      name: 'index',
      path: '/',
      component: 'pages/index.vue'
    },
    {
      name: 'users-id',
      path: '/users/:id?',
      component: 'pages/users/_id.vue'
    },
    {
      name: 'slug',
      path: '/:slug',
      component: 'pages/_slug/index.vue'
    },
    {
      name: 'slug-comments',
      path: '/:slug/comments',
      component: 'pages/_slug/comments.vue'
    }
  ]
}
```

##路由参数校验

####Nuxt.js 可以让你在动态路由组件中定义参数校验方法。

#####举个例子： pages/users/_id.vue
```code
export default {
  validate ({ params }) {
    // Must be a number
    return /^\d+$/.test(params.id)
  }
}
```
##嵌套路由

####假设文件结构如：
```code
pages/
--| users/
-----| _id.vue
-----| index.vue
--| users.vue
```
####Nuxt.js 自动生成的路由配置如下：
```code
router: {
  routes: [
    {
      path: '/users',
      component: 'pages/users.vue',
      children: [
        {
          path: '',
          component: 'pages/users/index.vue',
          name: 'users'
        },
        {
          path: ':id',
          component: 'pages/users/_id.vue',
          name: 'users-id'
        }
      ]
    }
  ]
}
```
