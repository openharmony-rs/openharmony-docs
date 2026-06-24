# @ohos.curves

本模块提供设置动画插值曲线功能，用于构造阶梯曲线对象、三阶贝塞尔曲线对象和弹簧曲线对象。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cubicBezier](arkts-arkui-curves-cubicbezier-f.md#cubicBezier-1) | 构造三阶贝塞尔曲线对象，曲线的值必须处于0-1之间。<br/><br/>&gt; **说明：**  <br/>&gt;<br/>&gt; 从API version 7开始支持，从API version 9开始废弃。建议使用[Curves.cubicBezierCurve](arkts-arkui-curves-cubicbeziercurve-f.md#cubicBezierCurve-1)替代。<br/> |
| [cubicBezierCurve](arkts-arkui-curves-cubicbeziercurve-f.md#cubicBezierCurve-1) | 构造三阶贝塞尔曲线对象，确保曲线的值在0到1之间。<br/> |
| [customCurve](arkts-arkui-curves-customcurve-f.md#customCurve-1) | 构造自定义曲线对象。<br/> |
| [init](arkts-arkui-curves-init-f.md#init-1) | 插值曲线的初始化函数，可以根据入参创建一个插值曲线对象。<br/><br/>&gt; **说明：**  <br/>&gt;<br/>&gt; 从API version 7开始支持，从API version 9开始废弃。建议使用[Curves.initCurve](arkts-arkui-curves-initcurve-f.md#initCurve-1)替代。<br/> |
| [initCurve](arkts-arkui-curves-initcurve-f.md#initCurve-1) | 插值曲线的初始化函数，可以根据入参创建一个插值曲线对象。<br/> |
| [interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md#interpolatingSpring-1) | 构造插值器弹簧曲线对象，生成一条从0到1的动画曲线，实际动画值根据曲线进行插值计算。动画时间由曲线参数决定，不受animation、animateTo中的duration参数控制。<br/> |
| [responsiveSpringMotion](arkts-arkui-curves-responsivespringmotion-f.md#responsiveSpringMotion-1) | 构造弹性跟手动画曲线对象，是[springMotion](arkts-arkui-curves-springmotion-f.md#springMotion-1)的一种特例，仅默认参数不同，可与springMotion混合使用。<br/> |
| [spring](arkts-arkui-curves-spring-f.md#spring-1) | 构造弹簧曲线对象。<br/><br/>&gt; **说明：**  <br/>&gt;<br/>&gt; 从API version 7开始支持，从API version 9开始废弃。建议使用[Curves.springCurve](arkts-arkui-curves-springcurve-f.md#springCurve-1)替代。<br/> |
| [springCurve](arkts-arkui-curves-springcurve-f.md#springCurve-1) | 构造弹簧曲线对象，曲线形状由弹簧参数决定，动画时长受animation、animateTo中的duration参数控制。<br/> |
| [springMotion](arkts-arkui-curves-springmotion-f.md#springMotion-1) | 构造弹性动画曲线对象。如果对同一对象的同一属性进行多个弹性动画，每个动画会替换掉前一个动画，并继承之前的速度。<br/> |
| [steps](arkts-arkui-curves-steps-f.md#steps-1) | 构造阶梯曲线对象。<br/><br/>&gt; **说明：**  <br/>&gt;<br/>&gt; 从API version 7开始支持，从API version 9开始废弃。建议使用[Curves. stepsCurve](arkts-arkui-curves-stepscurve-f.md#stepsCurve-1)替代。<br/> |
| [stepsCurve](arkts-arkui-curves-stepscurve-f.md#stepsCurve-1) | 构造阶梯曲线对象。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ICurve](arkts-arkui-curves-icurve-i.md) | 曲线对象，支持通过本模块中的[curves.cubicBezierCurve](arkts-arkui-curves-cubicbeziercurve-f.md#cubicBezierCurve-1)、<br/>[curves.interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md#interpolatingSpring-1)等方法创建不同类型的曲线对象，并可通过曲线对象调用其<br/>[interpolate](arkts-arkui-curves-icurve-i.md#interpolate-1)的成员方法。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Curve](arkts-arkui-curves-curve-e.md) | 插值曲线和动效请参考&lt;!--RP1--&gt;[贝塞尔曲线](../../../../../design/ux-design/animation-attributes.md)&lt;!--RP1End--&gt;。<br/><br/>\| 名称                \| 值 \| 说明                                                         \|<br/>\| ------------------- \| -- \| ------------------------------------------------------------ \|<br/>\| Linear              \| 0 \| 表示动画从头到尾的速度都是相同的。                           \|<br/>\| Ease                \| 1 \| 表示动画以低速开始，然后加快，在结束前变慢，cubic-bezier(0.25, 0.1, 0.25, 1.0)。 \|<br/>\| EaseIn              \| 2 \| 表示动画以低速开始，cubic-bezier(0.42, 0.0, 1.0, 1.0)。       \|<br/>\| EaseOut             \| 3 \| 表示动画以低速结束，cubic-bezier(0.0, 0.0, 0.58, 1.0)。       \|<br/>\| EaseInOut           \| 4 \| 表示动画以低速开始和结束，cubic-bezier(0.42, 0.0, 0.58, 1.0)。 \|<br/>\| FastOutSlowIn       \| 5 \| 标准曲线，cubic-bezier(0.4, 0.0, 0.2, 1.0)。                 \|<br/>\| LinearOutSlowIn     \| 6 \| 减速曲线，cubic-bezier(0.0, 0.0, 0.2, 1.0)。                 \|<br/>\| FastOutLinearIn     \| 7 \| 加速曲线，cubic-bezier(0.4, 0.0, 1.0, 1.0)。                 \|<br/>\| ExtremeDeceleration \| 8 \| 急缓曲线，cubic-bezier(0.0, 0.0, 0.0, 1.0)。                 \|<br/>\| Sharp               \| 9 \| 锐利曲线，cubic-bezier(0.33, 0.0, 0.67, 1.0)。               \|<br/>\| Rhythm              \| 10 \| 节奏曲线，cubic-bezier(0.7, 0.0, 0.2, 1.0)。                 \|<br/>\| Smooth              \| 11 \| 平滑曲线，cubic-bezier(0.4, 0.0, 0.4, 1.0)。                 \|<br/>\| Friction            \| 12 \| 阻尼曲线，cubic-bezier(0.2, 0.0, 0.2, 1.0)。                  \|<br/> |

