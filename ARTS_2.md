# ARTS - 2
> Tue, Nov 13, 2018 - Zhang Yangyang

## Algorithm
### [300. Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)
**Description**
Given an unsorted array of integers, find the length of longest increasing subsequence.
求数组中的最长递增子序列的长度。考察的知识点主要是动态规划。

**Solution**
时间复杂度为 O(n^2) 的解法。通过两个指针来实现。
```js
function lengthOfLIS(array) {
  let len = array.length
  // create an array named dp, the length is array's length and fill with 1.
  let dp = new Array(len).fill(1)
  let res = 0
  for (let i = 0; i < len; i++) {
    for (let j = 0; j < i; j++) {
      if (array[j] < array[i]) {
        dp[i] = Math.max(dp[i], dp[j] + 1)
      }
    }
    res = Math.max(res, dp[i])
  }
  return res
}
```
时间复杂度为 O(nlogn) 的解法
```js
function lengthOfLIS2(nums) {
  if (nums.length <= 1) return nums.length

  let res = [nums[0]]
  for (let i = 1; i < nums.length; i++) {
    if (nums[i] < res[0]) {
      res[0] = nums[i]
    } else if (nums[i] > res[res.length - 1]) {
      res.push(nums[i])
    } else {
      let index = binarySearch(res, nums[i]) 
      res[index] = nums[i]
    }
  }
  return res.length
}
function binarySearch(array, target) {
  let left = 0
  let right = array.length - 1
  while (left < right) {
    let mid = Math.floor((left + right) / 2)
    if (target > array[mid]) {
      left = mid + 1
    } else {
      right = mid
    }
  }
  return right
}
```

## Review
[How to write a good software design doc](https://medium.freecodecamp.org/how-to-write-a-good-software-design-document-66fcf019569c)

文章主要分为四个部分：
- **为什么**好写设计文档
- 设计文档应该包括**什么**
- **怎么**去写
- 围绕它有哪些**过程**

### 为什么
**设计文档是确保正确完成工作的最有效的工具**

### 写什么
设计文档时描述解决问题的方法。书写的内容至少以下要被考虑：
- 标题和人员
- 大纲
- 背景
- 能实现的目标和不能实现的目标
- 里程碑
- 现有解决方案
- 解决草案
- 可替代解决方案
- 可测试性、监控和警告
- 跨团队影响力
- 开放问题
- 详细内容和时间表

### 怎么写
- 尽可能的简单
- 使用图表
- 使用具体的数字
- 尽可能有趣
- 测试

## Tip
### HTTPS
[HTTPS](https://zh.wikipedia.org/wiki/HTTPS)经由HTTP进行通信，但利用SSL/TLS来加密数据包。HTTPS开发的主要目的，是提供对网站服务器的身份认证，保护交换数据的隐私与完整性。

#### 加密
对称加密，加密和解密使用同一把密钥；非对称加密，加密和解密使用不同的密钥，即公钥和私钥。
举个例子，有两个人，A 和 B，A 有公钥 `p1` 和私钥 `s1`， B 有公钥 `p2` 和私钥 `s2`。A 是如何将数据 `v` 传输给 B 的呢？因为公钥是可以共享的，所以 A 和 B 都有对方的公钥，A 会用 `p2` 和 `s1` 对 数据进行加密，B 会用 `s2` 和 `p1` 进行解密。
```
A:
v + p2 -> v'
v' + s1 -> v''
B:
v'' + p1 -> v'
v' + s2 -> v
``` 

#### CA 认证
但这样还是有问题的，A 是如何确定是将数据传输给 B 的呢？
解决的办法就是使用证书，证书是由第三方权威机构进行颁发的。
证书同时是使用公私钥加密来实现的，证书机构(CA)会对自己的证书用自己的私钥进行加密，生成签名。客户端就会用它配对的公钥来进行解密。总之，需要证书颁发机构和 DNS 服务器解析正确的保证。

## Share
[API之下](http://www.ruanyifeng.com/blog/2018/08/api-below.html)

API 即应用程序接口(Application Programming Interface)。个人比较熟悉的就是前后端进行交互时，数据的传输就是通过接口，可以更好的实现前后端分离。
通过 API 能够提供更高的效率。例如一些科技公司正在使用 API 替代了中层干部，上层领导直接将命令传达给下层工作人员，例如钉钉软件扮演的就是这种角色，可以极大的降低公司的管理成本。
以这种趋势发展下去，**长期来看，未来只有两种工作：API 之上的工作和 API 之下的工作**。API 之上就是制定 API 规则、给 API 下达指令的人。API 之下就是接受 API 指令进行工作的人。
看到文章的最后，让人有焦虑了许多。
软件正在变得越来越强大，用途越来越广，那么 API 层将越来越厚。未来的年轻人生活在 API 之下，抬头向上看，只会看到一个无边无际的软件层，根本不知道如何爬到云端，去做那些 API 之上的工作。

