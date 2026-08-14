# onSystemAutoStartup（系统接口）

## onSystemAutoStartup

```TypeScript
function onSystemAutoStartup(callback: AutoStartupCallback): void
```

注册监听应用组件开机自启动状态变化的回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_APP_BOOT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-autoStartupManager-function onSystemAutoStartup(callback: AutoStartupCallback): void--><!--Device-autoStartupManager-function onSystemAutoStartup(callback: AutoStartupCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AutoStartupCallback](arkts-ability-autostartupcallback-i-sys.md) | 是 | 监听应用组件开机自启动状态变化的回调对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Connect to system server failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied, interface caller does not have permission "ohos.permission.MANAGE_APP_BOOT". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

