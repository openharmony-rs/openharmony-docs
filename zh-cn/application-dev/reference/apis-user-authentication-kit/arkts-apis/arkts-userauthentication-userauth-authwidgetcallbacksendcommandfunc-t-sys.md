# AuthWidgetCallbackSendCommandFunc（系统接口）

```TypeScript
type AuthWidgetCallbackSendCommandFunc = (cmdData: string) => void
```

回调函数，身份认证框架向控件发送命令。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-userAuth-type AuthWidgetCallbackSendCommandFunc = (cmdData: string) => void--><!--Device-userAuth-type AuthWidgetCallbackSendCommandFunc = (cmdData: string) => void-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cmdData | string | 是 | 用户身份认证框架向控件发送的命令。 |

