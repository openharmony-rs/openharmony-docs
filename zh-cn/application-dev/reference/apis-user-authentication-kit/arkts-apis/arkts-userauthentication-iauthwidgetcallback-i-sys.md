# IAuthWidgetCallback（系统接口）

身份认证组件回调接口。认证组件通过该回调接口获取用户认证框架发送的命令，并根据命令内容执行相应的认证操作。

**起始版本：** 10

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

## sendCommand

```TypeScript
sendCommand(cmdData: string): void
```

回调函数，用于接收来自用户认证框架的命令。用户认证框架通过此回调向身份认证组件发送命令，控件需解析命令内容并执行相应操作。

**起始版本：** 10

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cmdData | string | 是 | 命令数据。JSON格式的字符串，包含用户认证框架向身份认证控件发送的具体命令内容，如认证类型切换、认证结果返回等指令。控件需解析此数据并执行相应操作。 |

**示例：**

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

const userAuthWidgetMgrVersion = 1;
try {
  let userAuthWidgetMgr = userAuth.getUserAuthWidgetMgr(userAuthWidgetMgrVersion);
  console.info('get userAuthWidgetMgr instance successfully.');
  userAuthWidgetMgr.on('command', {
    sendCommand(cmdData) {
      console.info(`The cmdData is ${cmdData}`);
    }
  })
  console.info('subscribe authentication event successfully.');
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`userAuth widgetMgr failed. Code is ${err?.code}, message is ${err?.message}`);
}

```

