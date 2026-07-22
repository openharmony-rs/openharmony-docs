# ScrollMotion（系统接口）

滚动动画模型。可以根据初始位置、初始速度、边界位置和弹簧属性构建滚动动画。

**起始版本：** 7

**废弃版本：** 22

<!--Device-unnamed-declare class ScrollMotion--><!--Device-unnamed-declare class ScrollMotion-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## constructor

```TypeScript
constructor(position: number, velocity: number, min: number, max: number, prop: SpringProp)
```

构造器参数。

**起始版本：** 7

**废弃版本：** 22

<!--Device-ScrollMotion-constructor(position: number, velocity: number, min: number, max: number, prop: SpringProp)--><!--Device-ScrollMotion-constructor(position: number, velocity: number, min: number, max: number, prop: SpringProp)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | number | 是 |  |
| velocity | number | 是 |  |
| min | number | 是 |  |
| max | number | 是 |  |
| prop | [SpringProp](arkts-arkui-springprop-c-sys.md) | 是 |  |

