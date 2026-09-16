# @ohos.curves(插值计算)

本模块提供设置动画插值曲线功能，用于构造阶梯曲线对象、三阶贝塞尔曲线对象、弹簧曲线对象、弹性动画曲线对象、弹性跟手动画曲线对象、插值器弹簧曲线对象和自定义曲线对象。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cubicBezier](arkts-arkui-curves-cubicbezier-f.md) | 构造三阶贝塞尔曲线对象，曲线的两个控制点横坐标x1、x2的取值范围限定在0到1之间。 |
| [cubicBezierCurve](arkts-arkui-curves-cubicbeziercurve-f.md) | 构造三阶贝塞尔曲线对象，曲线的两个控制点横坐标x1、x2的取值范围限定在0到1之间。 |
| [customCurve](arkts-arkui-curves-customcurve-f.md) | 构造自定义曲线对象，用户通过自定义插值函数决定曲线的形状。 |
| [init](arkts-arkui-curves-init-f.md) | 插值曲线的初始化函数，可以根据入参创建一个插值曲线对象。 |
| [initCurve](arkts-arkui-curves-initcurve-f.md) | 插值曲线的初始化函数，可以根据入参创建一个插值曲线对象。 |
| [interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md) | 构造插值器弹簧曲线对象，生成一条从0到1的动画曲线，实际动画值根据曲线进行插值计算。动画时间由曲线参数决定，不受动画参数中的时长参数控制。 |
| [responsiveSpringMotion](arkts-arkui-curves-responsivespringmotion-f.md) | 构造弹性跟手动画曲线对象，是[springMotion](arkts-arkui-curves-springmotion-f.md)的一种特例，仅默认参数不同，可与springMotion混合使用。 |
| [spring](arkts-arkui-curves-spring-f.md) | 构造弹簧曲线对象，曲线形状由弹簧参数决定，动画时长受animation、animateTo中的duration参数控制。与[interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md)相比，两者参数签名相同但行为不同：springCurve适用于需要固定动画时长的弹簧动画场景；interpolatingSpring适用于由弹簧参数自然决定动画时长的物理弹簧动画场景。 |
| [springCurve](arkts-arkui-curves-springcurve-f.md) | 构造弹簧曲线对象，曲线形状由弹簧参数决定，动画时长受动画参数中的时长参数控制。 |
| [springMotion](arkts-arkui-curves-springmotion-f.md) | 构造弹性动画曲线对象。与使用弹簧物理参数的[curves.springCurve](arkts-arkui-curves-springcurve-f.md)不同，springMotion使用响应式参数构造曲线，且支持动画间的速度继承，需要速度继承的连续弹性动画建议使用springMotion。如果对同一对象的同一属性进行多个弹性动画，每个动画会替换掉前一个动画，并继承之前的速度。 |
| [steps](arkts-arkui-curves-steps-f.md) | 构造阶梯曲线对象，阶梯曲线将动画时间等分为指定数量的间隔，在每个间隔内属性值保持不变，在间隔边界处发生阶跃变化。 |
| [stepsCurve](arkts-arkui-curves-stepscurve-f.md) | 构造阶梯曲线对象，将动画过程划分为若干等距间隔，在每个间隔的起点或终点发生阶跃变化。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [trailOptimizedInterpolatingSpring](arkts-arkui-curves-trailoptimizedinterpolatingspring-f-sys.md) | 在[interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md)基础上新增尾迹优化参数，构造带尾迹优化的插值器弹簧曲线对象，生成一条从0到1的动画曲线，实际动画值根据曲线进行插值计算。动画时间由曲线参数决定，不受动画参数中的时长参数控制。 |
| [trailOptimizedResponsiveSpringMotion](arkts-arkui-curves-trailoptimizedresponsivespringmotion-f-sys.md) | 在[responsiveSpringMotion](arkts-arkui-curves-responsivespringmotion-f.md)基础上新增尾迹优化参数，构造带尾迹优化的弹性跟手动画曲线对象。 |
| [trailOptimizedSpringMotion](arkts-arkui-curves-trailoptimizedspringmotion-f-sys.md) | 在[springMotion](arkts-arkui-curves-springmotion-f.md)基础上新增尾迹优化参数，构造带尾迹优化的弹性动画曲线对象。如果对同一对象的同一属性进行多个弹性动画，每个动画会替换掉前一个动画，并继承之前的速度。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [ICurve](arkts-arkui-curves-icurve-i.md) | 曲线对象，支持通过本模块中的[curves.initCurve](arkts-arkui-curves-initcurve-f.md)、[curves.stepsCurve](arkts-arkui-curves-stepscurve-f.md)、[curves.cubicBezierCurve](arkts-arkui-curves-cubicbeziercurve-f.md)、[curves.springCurve](arkts-arkui-curves-springcurve-f.md)、[curves.springMotion](arkts-arkui-curves-springmotion-f.md)、[curves.responsiveSpringMotion](arkts-arkui-curves-responsivespringmotion-f.md)、[curves.interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md)、[curves.customCurve](arkts-arkui-curves-customcurve-f.md)方法创建不同类型的曲线对象，并可通过曲线对象调用其[interpolate](arkts-arkui-curves-icurve-i.md#interpolate)的成员方法。其中springMotion、responsiveSpringMotion、interpolatingSpring创建的弹性动画曲线为物理曲线，时间不能归一，不能通过interpolate函数获得插值。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [TrailOptimization](arkts-arkui-curves-trailoptimization-i-sys.md) | 弹簧动画尾迹优化配置。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Curve](arkts-arkui-curves-curve-e.md) | 插值曲线和动效请参考&lt;!--RP1--&gt;[贝塞尔曲线](arkts-arkui-curves.md)&lt;!--RP1End--&gt;。 |
