# isTraceEnabled

## 导入模块

```TypeScript
```

## isTraceEnabled

```TypeScript
function isTraceEnabled(): boolean
```

判断当前是否开启应用trace捕获。

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 使用[hitrace](../../../dfx/hitrace.md)命令行工具等方式开启采集时返回true。未开启采集或停止采集后返回 false，此时调用HiTraceMeter性能跟踪打点接口无效。 |

**示例**

```TypeScript
if (hiTraceMeter.isTraceEnabled()) {
  // 业务流程......
} else {
  // 业务流程......
}
```
