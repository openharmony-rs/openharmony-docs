# setRecoverDisposedRule（系统接口）

## 导入模块

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## setRecoverDisposedRule

```TypeScript
function setRecoverDisposedRule(rule: RecoverDisposedRule): void
```

设置当前用户的恢复处置规则。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-appControl-function setRecoverDisposedRule(rule: RecoverDisposedRule): void--><!--Device-appControl-function setRecoverDisposedRule(rule: RecoverDisposedRule): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | [RecoverDisposedRule](arkts-ability-appcontrol-recoverdisposedrule-i-sys.md) | 是 | 恢复处置规则。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission denied. A non-system application is not allowed to call a system API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [17700075](../errorcode-bundle.md#17700075-want指定的bundlename与调用方不符) | The specified bundleName of want is not the same with caller. |
| [17700101](../errorcode-bundle.md#17700101-包管理服务异常) | Bundle manager service exception. |
