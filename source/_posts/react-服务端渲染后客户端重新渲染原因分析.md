---
title: react 服务端渲染后客户端重新渲染原因分析
date: 2017-08-25 19:40:28
tags: react-server-render
categories: react
---

### 1. 问题描述：

当我们使用react进行服务端渲染的时候常会遇到在客户端又重新渲染（非期望的重复渲染）的问题，react提示如下：
```
React attempted to reuse markup in a container but the checksum was invalid. This generally means that you are using server rendering and the markup generated on the server was not what the client was expecting. React injected new markup to compensate which works but you have lost many of the benefits of server rendering. Instead, figure out why the markup being generated is different on the client or server:
 (client) <!-- react-empty: 1 -
 (server) <div class="castboxGl
```
### 2.产生该问题的原因：
  1. 两端渲染的数据源不一致：通常我们会将服务端渲染时的使用的数据同样传递到客户端，两端共用同一组数据渲染确保一致性。常见代码如下：
    ```js
    // server side:
    const store = createStore(initialData)
    const content = renderToString(
      <Provider store={store}>
        <RouterContext {...renderProps}/>
      </Provider>
    )
    ...
    <div id="root">${content}</div>
    <!-- 下面将state传递到客户端 -->
    <script>window.__INITIAL_STATE__ = ${JSON.stringify(state)};</script>

    // client side:

    const store = createStore(window.__INITIAL_STATE__)
    ...
    ReactDOM.render(
      <Provider store={store}>
        <Router history={getHistory(store)} onUpdate={logPageView} routes={rootRoute} />
      </Provider>, rootElement
    )

    ```
  2. maybe it's just because there is an additional wrapper <div> with devTools enabled?
    [https://github.com/Hashnode/mern-starter/issues/139](https://github.com/Hashnode/mern-starter/issues/139)

  3.  after implementing react-router code splitting
    [https://github.com/Hashnode/mern-starter/issues/149](https://github.com/Hashnode/mern-starter/issues/149)

  4. and so on...
