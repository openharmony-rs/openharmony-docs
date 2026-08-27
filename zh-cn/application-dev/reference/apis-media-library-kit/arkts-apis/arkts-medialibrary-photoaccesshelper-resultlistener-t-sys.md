# ResultListener（系统接口）

```TypeScript
type ResultListener = (result: ResultInfo) => void
```

表示复制操作结果的监听类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | [ResultInfo](arkts-medialibrary-photoaccesshelper-resultinfo-i-sys.md) | 是 | 结果回调信息。 |
