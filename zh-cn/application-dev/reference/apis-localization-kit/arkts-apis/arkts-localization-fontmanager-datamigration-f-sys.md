# dataMigration（系统接口）

## 导入模块

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## dataMigration

```TypeScript
function dataMigration(callback: DataMigrationCallback): number
```

设备升级时使用的数据迁移接口，用于拉起迁移任务。

**起始版本：** 23

**需要权限：** ohos.permission.UPDATE_FONT

<!--Device-fontManager-function dataMigration(callback: DataMigrationCallback): int--><!--Device-fontManager-function dataMigration(callback: DataMigrationCallback): int-End-->

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [DataMigrationCallback](arkts-localization-fontmanager-datamigrationcallback-i-sys.md) | 是 | 数据迁移的回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回拉起数据迁移任务结果。返回为0表示拉起成功，否则拉起失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system application. |
| [31100110](../errorcode-font-manager.md#31100110-系统异常导致接口调用失败) |  |
| [31100111](../errorcode-font-manager.md#31100111-迁移任务执行中) |  |

