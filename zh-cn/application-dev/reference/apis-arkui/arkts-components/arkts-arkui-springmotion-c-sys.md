# SpringMotion（系统接口）

弹簧动画模型。可以基于起点、终点、初始速度和弹簧属性构建弹簧动画。

**起始版本：** 7

**废弃版本：** 22

<!--Device-unnamed-declare class SpringMotion--><!--Device-unnamed-declare class SpringMotion-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## constructor

```TypeScript
constructor(start: number, end: number, velocity: number, prop: SpringProp)
```

构造器参数。

**起始版本：** 7

**废弃版本：** 22

<!--Device-SpringMotion-constructor(start: number, end: number, velocity: number, prop: SpringProp)--><!--Device-SpringMotion-constructor(start: number, end: number, velocity: number, prop: SpringProp)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 |  |
| end | number | 是 |  |
| velocity | number | 是 |  |
| prop | [SpringProp](arkts-arkui-springprop-c-sys.md) | 是 |  |

