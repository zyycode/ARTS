# ARTS-1
> Thu, Nov 01, 2018 - Zhang Yangyang

## Algorithm

### [100. Same Tree](https://leetcode.com/problems/same-tree/description/)
**Description**

Given two binary trees, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical and the nodes have the same value.

**Solution**

判断两棵树是否相同，通过递归来实现，主要符合两个条件：
1. 两棵树的结点都为空；或不为空时，但是值相等
2. 两棵树的结点都不为空，左右子树对应相等

```javascript
var isSameTree = function(p, q) {
  if (p === null && q === null) return true
  if (p === null || q === null) return false
  // 值不相等时，可以减少递归次数
  if (p.val === q.val) {
    return isSameTree(p.left, q.left) && isSameTree(p.right, q.right) 
  }
  return false
}
```

## Review
[NodeJS: In Three(ish) Minutes](https://medium.com/@kieranmaher13/nodejs-in-three-ish-minutes-4c4401b43b2c)

这篇文章主要介绍了很火的NodeJS。
- **NodeJS的由来**
NodeJS是由[Ryan Dahl](https://en.wikipedia.org/wiki/Ryan_Dahl)在2009年创建的，思路是来自于当时他在一个图片上传网站看见一个进度条显示当前图片上传的进度。现在这种进度条是很常见的，但在当时没有后端的年代还是十分稀有新奇的。因为在当时服务器还没有能力去处理并发情况，比如当用户同时上传文件和发其它请求。
- **NodeJS的设计**
NodeJS最初的目的就是处理这种并发情况，web服务器能够同时处理多个请求并及时回应。NodeJS是基于Google的V8引擎，因为V8引擎编译JavaScript是最快的
- **NPM**
npm是NodeJS自带的包管理器，开发者只需要下载引入该包就可以使用相关的功能，十分方便，极大提高了开发效率。

总言而之，NodeJS是基于V8引擎的JavaScript运行环境，使用事件驱动、非阻塞I/O和异步输入输出模型等技术来提高性能。
## Tip

### 使用鼠标手势提高效率
**手势软件有很多可自行搜索**，我用的是[WGestures](http://www.yingdev.com/projects/wgestures)
在 Windows 通过手势可以简化很多操作，例如：
当鼠标触碰窗口的四个角可以快速切换上下标签页，不同桌面；
使用手势可以快速完成常用操作，刷新、打开控制台、新建(关闭)标签页、切换桌面等等，可以自定义设置

![](https://i.loli.net/2018/11/01/5bdacc9306d10.gif)
![](https://i.loli.net/2018/11/01/5bdacb3fa0136.png)

## Share

### [一个前端必会的 Nginx免费教程 (共11集)](http://jspang.com/post/nginx.html)

个人觉得写得很好，还有对应的视频教程。看完之后可以轻松的在在自己的 VPS 上搭建 Nginx 并可以通过不同的端口、子域名来划分虚拟主机。
