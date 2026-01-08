# 验证示例代码同源--引用写法错误-无地址


<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->

## 引用中无地址

<!--@[obtain_supported_capabilities](http)-->
```ts
obtainingSupported() {
  try {
    // 查询认证能力是否支持
    userAuth.getAvailableStatus(userAuth.UserAuthType.PIN, userAuth.AuthTrustLevel.ATL1);
    Logger.info('current auth trust level is supported');
    return true;
  } catch (error) {
    const err: BusinessError = error as BusinessError;
    Logger.error(`current auth trust level is not supported, code is ${err?.code}, message is ${err?.message}`);
    return false;
  }
}
```