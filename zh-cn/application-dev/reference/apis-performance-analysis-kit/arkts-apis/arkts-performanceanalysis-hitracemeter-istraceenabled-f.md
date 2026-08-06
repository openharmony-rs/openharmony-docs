# isTraceEnabled

## isTraceEnabled

```TypeScript
function isTraceEnabled(): boolean
```

判断当前是否开启应用trace捕获。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-hiTraceMeter-function isTraceEnabled(): boolean--><!--Device-hiTraceMeter-function isTraceEnabled(): boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 使用\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_命令行工具等方式开启采集时返回true。未开启采集或停止采集后返回 |

**示例：**

```TypeScript
if (hiTraceMeter.isTraceEnabled()) {
  // 业务流程......
} else {
  // 业务流程......
}
```

