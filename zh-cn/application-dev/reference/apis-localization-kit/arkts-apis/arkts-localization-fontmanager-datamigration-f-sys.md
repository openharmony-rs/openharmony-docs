# dataMigration（系统接口）

## dataMigration

```TypeScript
function dataMigration(callback: DataMigrationCallback): int
```

设备升级时使用的数据迁移接口，用于启动迁移任务，通过回调函数实时反馈迁移进度和结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

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
| int | 迁移任务启动结果。 &lt;br&gt;- 0：迁移任务启动成功，迁移任务将在后台执行并通过回调通知进度和结果。 &lt;br&gt;- 其他值：迁移任务启动失败，请根据错误码排查原因。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [31100110](../errorcode-font-manager.md#31100110-系统异常导致接口调用失败) | Call failed due to system error. |
| [31100111](../errorcode-font-manager.md#31100111-迁移任务执行中) | Data migration is in progress. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

