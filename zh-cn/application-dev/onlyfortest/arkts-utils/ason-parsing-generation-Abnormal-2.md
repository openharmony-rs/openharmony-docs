# 验证示例代码同源异常场景--替换后的codeid不存在

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->

## 替换后的codeid不存在-1

替换后的链接`https://gitcode.com/HarmonyOS_Samples/guide-snippets/blob/master/UserAuthentication/entry/src/main/ets/pages/Index.ets#L100-L111`，需要报错

<!--@[obtain_supported_capabilities-1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication/entry/src/main/ets/pages/Index.ets)-->

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

## 替换后的codeid不存在-2

替换后的链接`https://gitcode.com/HarmonyOS_Samples/guide-snippets/blob/master/UserAuthentication/entry/src/main/ets/pages/Index.ets#L100-L111`需要报错
<!--@[not-exsit-codeId](https://gitcode.com/HarmonyOS_Samples/guide-snippets/blob/master/UserAuthentication/entry/src/main/ets/pages/Index.ets)-->
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