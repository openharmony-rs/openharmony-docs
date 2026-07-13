# @ohos.curves

本模块提供设置动画插值曲线功能，用于构造阶梯曲线对象、三阶贝塞尔曲线对象和弹簧曲线对象。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cubicBezier](arkts-arkui-cubicbezier-f.md#cubicbezier-1) | 构造三阶贝塞尔曲线对象，曲线的值必须处于0-1之间。@link curves.cubicBezierCurve}替代。 |
| [cubicBezierCurve](arkts-arkui-cubicbeziercurve-f.md#cubicbeziercurve-1) | 构造三阶贝塞尔曲线对象，确保曲线的值在0到1之间。 |
| [customCurve](arkts-arkui-customcurve-f.md#customcurve-1) | 构造自定义曲线对象。 |
| [init](arkts-arkui-init-f.md#init-1) | 插值曲线的初始化函数，可以根据入参创建一个插值曲线对象。@link curves.initCurve}替代。 |
| [initCurve](arkts-arkui-initcurve-f.md#initcurve-1) | 插值曲线的初始化函数，可以根据入参创建一个插值曲线对象。 |
| [interpolatingSpring](arkts-arkui-interpolatingspring-f.md#interpolatingspring-1) | 构造插值器弹簧曲线对象，生成一条从0到1的动画曲线，实际动画值根据曲线进行插值计算。动画时间由曲线参数决定，不受animation、animateTo中的duration参数控制。 |
| [responsiveSpringMotion](arkts-arkui-responsivespringmotion-f.md#responsivespringmotion-1) | 构造弹性跟手动画曲线对象，是[springMotion](arkts-arkui-springmotion-f.md#springmotion-1)的一种特例，仅默认参数不同，可与springMotion混合使用。 |
| [spring](arkts-arkui-spring-f.md#spring-1) | 构造弹簧曲线对象。@link curves.springCurve}替代。 |
| [springCurve](arkts-arkui-springcurve-f.md#springcurve-1) | 构造弹簧曲线对象，曲线形状由弹簧参数决定，动画时长受animation、animateTo中的duration参数控制。 |
| [springMotion](arkts-arkui-springmotion-f.md#springmotion-1) | 构造弹性动画曲线对象。如果对同一对象的同一属性进行多个弹性动画，每个动画会替换掉前一个动画，并继承之前的速度。 |
| [steps](arkts-arkui-steps-f.md#steps-1) | 构造阶梯曲线对象。@link curves.stepsCurve}替代。 |
| [stepsCurve](arkts-arkui-stepscurve-f.md#stepscurve-1) | 构造阶梯曲线对象。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ICurve](arkts-arkui-icurve-i.md) | 曲线对象，支持通过本模块中的[curves.cubicBezierCurve](arkts-arkui-cubicbeziercurve-f.md#cubicbeziercurve-1)、[curves.interpolatingSpring](arkts-arkui-interpolatingspring-f.md#interpolatingspring-1)等方法创建不同类型的曲线对象，并可通过曲线对象调用其[interpolate](arkts-arkui-icurve-i.md#interpolate-1)的成员方法。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Curve](arkts-arkui-curve-e.md) | 插值曲线和动效请参考&lt;!--RP1--&gt;[贝塞尔曲线](../../../../../design/ux-design/animation-attributes.md)&lt;!--RP1End--&gt;。\| 名称 \| 值 \| 说明 \|\| ------------------- \| -- \| ------------------------------------------------------------ \|\| Linear \| 0 \| 表示动画从头到尾的速度都是相同的。 \|\| Ease \| 1 \| 表示动画以低速开始，然后加快，在结束前变慢，cubic-bezier(0.25, 0.1, 0.25, 1.0)。 \|\| EaseIn \| 2 \| 表示动画以低速开始，cubic-bezier(0.42, 0.0, 1.0, 1.0)。 \|\| EaseOut \| 3 \| 表示动画以低速结束，cubic-bezier(0.0, 0.0, 0.58, 1.0)。 \|\| EaseInOut \| 4 \| 表示动画以低速开始和结束，cubic-bezier(0.42, 0.0, 0.58, 1.0)。 \|\| FastOutSlowIn \| 5 \| 标准曲线，cubic-bezier(0.4, 0.0, 0.2, 1.0)。 \|\| LinearOutSlowIn \| 6 \| 减速曲线，cubic-bezier(0.0, 0.0, 0.2, 1.0)。 \|\| FastOutLinearIn \| 7 \| 加速曲线，cubic-bezier(0.4, 0.0, 1.0, 1.0)。 \|\| ExtremeDeceleration \| 8 \| 急缓曲线，cubic-bezier(0.0, 0.0, 0.0, 1.0)。 \|\| Sharp \| 9 \| 锐利曲线，cubic-bezier(0.33, 0.0, 0.67, 1.0)。 \|\| Rhythm \| 10 \| 节奏曲线，cubic-bezier(0.7, 0.0, 0.2, 1.0)。 \|\| Smooth \| 11 \| 平滑曲线，cubic-bezier(0.4, 0.0, 0.4, 1.0)。 \|\| Friction \| 12 \| 阻尼曲线，cubic-bezier(0.2, 0.0, 0.2, 1.0)。 \| |

