# ICurve

曲线对象。

**起始版本：** 9

<!--Device-unnamed-interface ICurve--><!--Device-unnamed-interface ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## interpolate

```TypeScript
interpolate(fraction : number) : number
```

插值曲线的插值计算函数，可以通过传入的归一化时间参数返回当前的插值

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ICurve-interpolate(fraction : number) : number--><!--Device-ICurve-interpolate(fraction : number) : number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fraction | number | 是 | 当前的归一化时间参数。<br/>取值范围：[0,1]<br/>**说明：** <br/>设置的值小于0时，按0处理；设置的值大于1时，按1处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回归一化time时间点对应的曲线插值。 |

