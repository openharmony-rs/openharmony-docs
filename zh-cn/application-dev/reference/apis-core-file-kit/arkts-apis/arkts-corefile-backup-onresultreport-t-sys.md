# OnResultReport（系统接口）

```TypeScript
type OnResultReport = (bundleName: string, result: string) => void
```

备份服务返回结果信息时触发的回调。 第一个字符串参数表示触发回调的应用名称。 第二个字符串参数表示应用的处理结果。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-backup-type OnResultReport = (bundleName: string, result: string) => void--><!--Device-backup-type OnResultReport = (bundleName: string, result: string) => void-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 触发回调的应用名称。 |
| result | string | 是 | 应用备份或恢复的结果信息。 |

