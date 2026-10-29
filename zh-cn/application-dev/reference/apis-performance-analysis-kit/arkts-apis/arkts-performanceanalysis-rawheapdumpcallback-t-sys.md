# RawHeapDumpCallback（系统接口）

```TypeScript
type RawHeapDumpCallback = (code: number) => void
```

导出堆快照的回调函数

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type RawHeapDumpCallback = (code: int) => void--><!--Device-unnamed-type RawHeapDumpCallback = (code: int) => void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 导出结果码。取值限定为整数 |
