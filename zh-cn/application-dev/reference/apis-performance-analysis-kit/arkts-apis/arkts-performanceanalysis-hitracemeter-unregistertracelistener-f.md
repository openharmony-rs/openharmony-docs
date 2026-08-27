# unregisterTraceListener

## 导入模块

```TypeScript
```

## unregisterTraceListener

```TypeScript
function unregisterTraceListener(index: number): number
```

注销通过registerTraceListener()注册的trace捕获开关通知回调函数。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 已注册回调函数索引，取值范围[0, 9]，即 [registerTraceListener()](arkts-performanceanalysis-hitracemeter-registertracelistener-f.md)调用成功时的返回值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 回调注销状态。 0：注销成功； -1：目标索引的回调函数未注册； -2：无效索引，参数index值不在[0, 9]范围内。 |

**示例**

```TypeScript
// 注销应用trace捕获开关通知回调，index为hiTraceMeter.registerTraceListener返回的回调索引
let ret = hiTraceMeter.unregisterTraceListener(index);
if (ret < 0) {
  // 异常处理......
}
```
