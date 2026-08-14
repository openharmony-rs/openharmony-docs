# abort

## abort

```TypeScript
function abort(): void
```

该方法会导致进程立即退出并生成一个核心文件，谨慎使用。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-process-function abort(): void--><!--Device-process-function abort(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

## 示例

```TypeScript
process.abort();
```

