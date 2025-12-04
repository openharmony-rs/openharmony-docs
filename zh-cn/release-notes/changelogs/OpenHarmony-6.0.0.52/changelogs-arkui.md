# ArkUI子系统Changelog

## cl.arkui.1 onVisibleAreaApproximateChange接口返回值类型由void改为T

**访问级别**

公开接口

**变更原因**

通用事件onVisibleAreaApproximateChange接口返回值类型为void不支持链式调用。

**变更影响**

此变更不涉及应用适配。

变更前：onVisibleAreaApproximateChange接口返回值类型为void，不支持链式调用。
  
变更后：onVisibleAreaApproximateChange接口返回值类型为T，支持链式调用。

**起始API Level**

17

**变更发生版本**

从OpenHarmony SDK 6.0.0.52开始。

**变更的接口/组件**

[onVisibleAreaApproximateChange](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-component-visible-area-change-event.md#onvisibleareaapproximatechange17)

**适配指导**

返回值改为T，不影响接口功能，无需适配。