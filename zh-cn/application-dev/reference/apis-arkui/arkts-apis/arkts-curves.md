# @ohos.curves

/*
 Copyright (c) 2025 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License"),
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /


**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace curves--><!--Device-unnamed-declare namespace curves-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cubicBezierCurve](arkts-arkui-curves-cubicbeziercurve-f.md#cubicBezierCurve) | 构造三阶贝塞尔曲线对象，确保曲线的值在0到1之间。 |
| [customCurve](arkts-arkui-curves-customcurve-f.md#customCurve) | 构造自定义曲线对象。 |
| [initCurve](arkts-arkui-curves-initcurve-f.md#initCurve) | 插值曲线的初始化函数，可以根据入参创建一个插值曲线对象。 |
| [interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md#interpolatingSpring) | 构造插值器弹簧曲线对象，生成一条从0到1的动画曲线，实际动画值根据曲线进行插值计算。动画时间由曲线参数决定，不受animation、animateTo中的duration参数控制。 |
| [responsiveSpringMotion](arkts-arkui-curves-responsivespringmotion-f.md#responsiveSpringMotion) | 构造弹性跟手动画曲线对象，是springMotion的一种特例，仅默认 参数不同，可与springMotion混合使用。 |
| [springCurve](arkts-arkui-curves-springcurve-f.md#springCurve) | 构造弹簧曲线对象，曲线形状由弹簧参数决定，动画时长受animation、animateTo中的duration参数控制。 |
| [springMotion](arkts-arkui-curves-springmotion-f.md#springMotion) | 构造弹性动画曲线对象。如果对同一对象的同一属性进行多个弹性动画，每个动画会替换掉前一个动画，并继承之前的速度。 |
| [stepsCurve](arkts-arkui-curves-stepscurve-f.md#stepsCurve) | 构造阶梯曲线对象。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ICurve](arkts-arkui-curves-icurve-i.md) | 曲线对象，支持通过本模块中的 curves.cubicBezierCurve、 curves.interpolatingSpring等 方法创建不同类型的曲线对象，并可通过曲线对象调用其interpolate的成员方法。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Curve](arkts-arkui-curves-curve-e.md) | 插值曲线和动效请参考&lt;!--RP1--&gt;[贝塞尔曲线](../../../../design/ux-design/animation-attributes.md)&lt;!--RP1End--&gt;。 \| 名称 \| 值 \| 说明 \| \| ------------------- \| -- \| ------------------------------ \| \| Linear \| 0 \| 表示动画从头到尾的速度都是相同的。 \| \| Ease \| 1 \| 表示动画以低速开始，然后加快，在结束前变慢，cubic-bezier(0.25, 0.1, 0.25, 1.0)。 \| \| EaseIn \| 2 \| 表示动画以低速开始，cubic-bezier(0.42, 0.0, 1.0, 1.0)。 \| \| EaseOut \| 3 \| 表示动画以低速结束，cubic-bezier(0.0, 0.0, 0.58, 1.0)。 \| \| EaseInOut \| 4 \| 表示动画以低速开始和结束，cubic-bezier(0.42, 0.0, 0.58, 1.0)。 \| \| FastOutSlowIn \| 5 \| 标准曲线，cubic-bezier(0.4, 0.0, 0.2, 1.0)。 \| \| LinearOutSlowIn \| 6 \| 减速曲线，cubic-bezier(0.0, 0.0, 0.2, 1.0)。 \| \| FastOutLinearIn \| 7 \| 加速曲线，cubic-bezier(0.4, 0.0, 1.0, 1.0)。 \| \| ExtremeDeceleration \| 8 \| 急缓曲线，cubic-bezier(0.0, 0.0, 0.0, 1.0)。 \| \| Sharp \| 9 \| 锐利曲线，cubic-bezier(0.33, 0.0, 0.67, 1.0)。 \| \| Rhythm \| 10 \| 节奏曲线，cubic-bezier(0.7, 0.0, 0.2, 1.0)。 \| \| Smooth \| 11 \| 平滑曲线，cubic-bezier(0.4, 0.0, 0.4, 1.0)。 \| \| Friction \| 12 \| 阻尼曲线，cubic-bezier(0.2, 0.0, 0.2, 1.0)。 \| |

