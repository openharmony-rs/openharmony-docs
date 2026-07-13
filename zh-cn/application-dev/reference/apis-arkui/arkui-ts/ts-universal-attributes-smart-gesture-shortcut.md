# 智慧手势响应
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

智慧手势响应的行为配置，并设置其响应优先级。

> **说明：**
>
> 该属性仅用于声明组件是否响应智慧手势，不会直接触发点击、滚动、翻页或返回等动作。

**起始版本：** 26.0.0

## smartGestureShortcut

smartGestureShortcut(options?: SmartGestureShortcutOptions): T

设置组件智慧手势响应行为配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| options | [SmartGestureShortcutOptions](#smartgestureshortcutoptions) | 否 | 组件智慧手势响应配置。<br/>SmartGestureShortcutOptions中enabled用于配置组件是否响应智慧手势。<br/>selectable用于设置组件被智慧手势操作选中后是否展示并保留选中态。<br/>action用于设置智慧手势响应优先级，当前仅支持GestureShortcut.PRIMARY，会使组件在智慧手势的滑动，点击等操作中作为首选响应目标。<br/>建议显式传入，避免因缺省配置导致预期不一致，缺省配置处理参考[SmartGestureShortcutOptions](#smartgestureshortcutoptions)。|

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| T | 返回当前组件。 |

**示例：**

参考智慧手势控制器[示例1（启用智慧手势并自定义动作处理）](../arkts-apis-uicontext-smartgesturecontroller.md#示例1启用智慧手势并自定义动作处理)。

## SmartGestureShortcutOptions

智慧手势响应行为配置对象。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| action | [GestureShortcut](ts-appendix-enums.md#gestureshortcut) | 否 | 是 | 智慧手势响应优先级。当前仅支持GestureShortcut.PRIMARY，表示组件在智慧手势的滑动，点击等操作中作为首选响应目标。<br/>默认值为GestureShortcut.PRIMARY。 |
| enabled | boolean | 否 | 是 | 当前组件是否响应智慧手势。<br/>true表示组件响应智慧手势，false表示组件不响应智慧手势。<br/>默认值为false。 |
| selectable | boolean | 否 | 是 | 组件被智慧手势操作选中后是否展示并保留选中态。<br/>true表示显示选中框，false表示不显示选中框。<br/>当enabled为true时，默认值为true；当enabled为false时，默认值为false。 |