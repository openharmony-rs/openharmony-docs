# 验证示例代码同源正常场景--应用地址需要替换--格式验证

前提：应用地址需要替换

## 引用全量代码

### ID无嵌套，代码完全一致

替换后的链接`https://gitcode.com/HarmonyOS_Samples/guide-snippets/blob/master/UserAuthentication/entry/src/main/ets/pages/Index.ets#L171-L217`

<!--@[authentication_example2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication/entry/src/main/ets/pages/Index.ets)-->
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

### ID无嵌套，列表中

* list 1,缺少内容

    替换后的链接`https://gitcode.com/HarmonyOS_Samples/guide-snippets/blob/master/UserAuthentication/entry/src/main/ets/pages/Index.ets#L120-L163`
    
    <!--@[authentication_example1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication/entry/src/main/ets/pages/Index.ets)-->
    
    ```ts
    initiatingUserAuthentication1() {
      try {
        const randData = getRandData();
        if (!randData) {
          return;
        }
        // 设置认证参数
        const authParam: userAuth.AuthParam = {
          challenge: randData,
          authType: [userAuth.UserAuthType.PIN, userAuth.UserAuthType.FACE, userAuth.UserAuthType.FINGERPRINT],
          authTrustLevel: userAuth.AuthTrustLevel.ATL3,
        };
        // 获取认证对象
        const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
        Logger.info('get userAuth instance success');
        // 订阅认证结果
        userAuthInstance.on('result', {
          onResult: (result: userAuth.UserAuthResult) => {
            try {
              Logger.info(`userAuthInstance callback result: ${JSON.stringify(result)}`);
              this.result[ResultIndex.EXAMPLE_1] = (`${result.result}`);
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
* list 2，缩进不一致

    替换后的链接`https://gitcode.com/HarmonyOS_Samples/guide-snippets/blob/master/UserAuthentication/entry/src/main/ets/pages/Index.ets#L100-L111`
    <!--@[obtain_supported_capabilities](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication/entry/src/main/ets/pages/Index.ets)-->
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
* list 3，含include字段

    替换后的链接`https://gitcode.com/HarmonyOS_Samples/guide-snippets/blob/master/UserAuthentication/entry/src/main/ets/pages/Index.ets#L327-L393`

    <!--@[cancel_authentication](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication/entry/src/main/ets/pages/Index.ets)-->
    ```ts
    handleAuthResultAndCanceling(userAuthInstance: userAuth.UserAuthInstance, exampleNumber: number) {
      try {
        // userAuthInstance.on异常抛出层
        userAuthInstance.on('result', {
          onResult: (result: userAuth.UserAuthResult) => {
            try {
              Logger.info(`userAuthInstance callback result: ${JSON.stringify(result)}`);
              this.result[exampleNumber] = (`${result.result}`);
              // 认证完成后取消订阅
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
    }

    /*
    * cancel-authentication.md
    * 发起认证可信等级≥ATL3的人脸+锁屏密码认证后，取消认证请求
    * */
    cancelingUserAuthentication() {
      try {
        const randData = getRandData();
        if (!randData) {
          return;
        }
        // 设置认证参数
        const authParam: userAuth.AuthParam = {
          challenge: randData,
          authType: [userAuth.UserAuthType.PIN, userAuth.UserAuthType.FACE, userAuth.UserAuthType.FINGERPRINT],
          authTrustLevel: userAuth.AuthTrustLevel.ATL3,
        };
        // 配置认证界面
        const widgetParam: userAuth.WidgetParam = {
          title: resourceToString($r('app.string.title')),
        };
        // 获取认证对象
        const userAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
        Logger.info('get userAuth instance success');
        this.handleAuthResultAndCanceling(userAuthInstance, ResultIndex.CANCEL);
      } catch (error) {
        const err: BusinessError = error as BusinessError;
        Logger.error(`auth catch error, code is ${err?.code as number}, message is ${err?.message}`);
      }
    }
    ```
    
  * list 4，缩进不一致
    替换后的链接`https://gitcode.com/HarmonyOS_Samples/guide-snippets/blob/master/UserAuthentication/entry/src/main/ets/pages/Index.ets#L100-L111`
    
    <!--@[obtain_supported_capabilities](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication/entry/src/main/ets/pages/Index.ets)-->
    
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


### ID存在嵌套




## 引用部分代码（Exclude字段）
