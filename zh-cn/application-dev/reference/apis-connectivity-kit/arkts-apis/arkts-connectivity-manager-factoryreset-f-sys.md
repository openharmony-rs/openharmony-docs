# factoryReset（系统接口）

## 导入模块

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## factoryReset

```TypeScript
function factoryReset(): Promise<void>
```

恢复星闪设置。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-manager-function factoryReset(): Promise<void>--><!--Device-manager-function factoryReset(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 返回promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| 36100099 | Operation failed. |

