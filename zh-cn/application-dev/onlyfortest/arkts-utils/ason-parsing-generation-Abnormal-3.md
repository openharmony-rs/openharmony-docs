# 验证示例代码同源--引用写法错误-无codeid

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->

## 引用中无codeid

<!--@[null](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication/entry/src/main/ets/pages/Index.ets)-->
```ts
  initiatingUserAuthentication2() {
    // 设置认证参数
    let reuseUnlockResult: userAuth.ReuseUnlockResult = {
      reuseMode: userAuth.ReuseMode.AUTH_TYPE_RELEVANT,
      reuseDuration: userAuth.MAX_ALLOWABLE_REUSE_DURATION,
    };
    try {
      const randData = getRandData();
      if (!randData) {
        return;
      }
      const authParam: userAuth.AuthParam = {
        challenge: randData,
        authType: [userAuth.UserAuthType.PIN, userAuth.UserAuthType.FACE, userAuth.UserAuthType.FINGERPRINT],
        authTrustLevel: userAuth.AuthTrustLevel.ATL3,
        reuseUnlockResult: reuseUnlockResult,
      };
      // 配置认证界面
      const widgetParam: userAuth.WidgetParam = {
        title: resourceToString($r('app.string.title')),
      };
      // 获取认证对象
      const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
      Logger.info('get userAuth instance success');
      // 订阅认证结果
      userAuthInstance.on('result', {
        onResult: (result: userAuth.UserAuthResult) => {
          try {
            Logger.info(`userAuthInstance callback result: ${JSON.stringify(result)}`);
            this.result[ResultIndex.EXAMPLE_2] = (`${result.result}`);
            // 可在认证结束或其他业务需要场景，取消订阅认证结果。
            userAuthInstance.off('result');
          } catch (error) {
            const err: BusinessError = error as BusinessError;
            Logger.error(`onResult catch error. Code: ${err?.code}, Message: ${err?.message}`);
          }
        }
      });
      // 启动认证
      userAuthInstance.start();
      Logger.info('auth start success');
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      Logger.error(`auth catch error, code is ${err?.code}, message is ${err?.message}`);
    }
  }
```