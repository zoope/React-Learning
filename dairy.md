## **3.18**  
昨天晚上搞到很晚也没解决的一个坑  
```js
import React from 'react';
import ReactDOM from 'react-dom';
import { Router, Route, hashHistory } from 'react-router';

import UserAdd from './component/UserAdd';

ReactDOM.render((
  <Router history={hashHistory}>
    <Route path="/user/add" component={UserAdd}/>
  </Router>
), document.getElementById('root'));
```  
这段代码和阮一峰老师的 [`教程`](http://www.ruanyifeng.com/blog/2016/05/react_router.html?utm_source=tool.lu) 基本内容是一致的，但是却出现了悲惨的报错结果
```warning
The prop `history` is marked as required in `Router`, but its value is `undefined`
```
这里吐槽一句，百度找不到结果，国人压根没多少人问或者是百度压根搜索出了无关结果，总之，就是解决不了，期间去github关于react-router的页面浏览了一下，隐隐觉得是最新版本的api改动了，找到 [`docs`](https://reacttraining.com/react-router/)结果自己压根没仔细看，找不到原因  
今天，烦躁了一天回家，翻过墙，google了一下，第一条就给了我回答
```answer
version 4 of React Router changed things around a bit.
```
心中万千草泥马崩腾而过，然后回去继续翻V4的文档，总算是找到新版的写法了，但是介于自己对于V4之前版本的react-router理解基本是一张白纸，所以感觉非常吃力，调回3.x版本，继续原来的project，只不过，这里也算给自己填一个坑好了，详见[ `todos.md` ](./todos.md)