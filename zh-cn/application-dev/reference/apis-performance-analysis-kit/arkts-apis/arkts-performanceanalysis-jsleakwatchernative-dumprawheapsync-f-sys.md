# dumpRawHeapSync（系统接口）

## 导入模块

```TypeScript
```

## dumpRawHeapSync

```TypeScript
function dumpRawHeapSync(filePath: string): void
```

同步导出ArkTS堆快照。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-jsLeakWatcherNative-function dumpRawHeapSync(filePath: string): void--><!--Device-jsLeakWatcherNative-function dumpRawHeapSync(filePath: string): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 堆快照的目标文件路径。 |
