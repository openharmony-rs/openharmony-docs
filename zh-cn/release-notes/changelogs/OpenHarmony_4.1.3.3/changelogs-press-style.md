# ArkUI变更说明
## cl.ArkUI.1 多态样式属性中组件按下状态的样式行为变更

**访问级别**
公开接口

**变更原因**
优化多态样式属性中的按压态状态样式能力，方便开发者进行状态样式开发。

**变更影响**
该变更为兼容性变更，会影响组件设置了多态样式属性按压态的生效/取消行为。

**变更发生版本**
从OpenHarmony SDK 4.1.3.3开始。

**变更的接口/组件**

API 11之前组件按压态样式行为：

* 手指按压组件后出现按压态效果，在手指滑动出组件的区域时，按压态仍然保持，在手指抬起后按压态取消。
* 如果多指按下，组件出现按压态效果后，部分手指抬起，按压态会取消。
* 如果设置按压态的组件在List等滚动类容器组件中，在组件上滑动，组件会出现按压态后立即取消。

API 11及之后组件按压态样式行为：

* 手指按压组件后会立即出现按压态效果，在手指滑动出组件的区域时，按压态取消。
* 如果多指按下，组件出现按压态效果后，部分手指抬起，按压态会保持；所有手指抬起时，按压态取消。
* 如果设置按压态的组件在List等滚动类容器中，在组件上滑动，组件不出现按压态效果。

**适配指导**
默认行为变更，不涉及适配。
