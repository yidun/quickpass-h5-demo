# 本机校验H5使用手册

## 引入SDK
1. npm引入
```js
  npm install --save netease-quickpass-sdk
```

2. script引入

netease-quickpass-sdk.umd.js将暴露`NEQuickPass`变量，引入方式如下：
```js
  <script src="./yourPath/netease-quickpass-sdk.umd.js"></script>
```

*注意：* 生产上有https访问的，https请求跨域，会导致上报的referer为空，请在head中添加代码： 
```js
  <meta content="always" name="referrer">
```

## 初始化

```js
  var sdk = new NEQuickPass('从易盾申请到的appId');
```

## 获取秘钥
调用实例的getToken方法可获取验证秘钥。getToken支持回调函数和promise。

```js
  sdk.getToken(mobile, function (err, data) {
    if (err) {
      // 获取秘钥发生错误，请处理
      return
    }
    // 取号流程完成，等待验证，data为{ accessToken: 'xxx...', token: 'xxx...' }
  })
```

## 上传秘钥
将获取到的accessToken、token上传至客户服务端，由服务端调用本机校验服务提供的相应接口