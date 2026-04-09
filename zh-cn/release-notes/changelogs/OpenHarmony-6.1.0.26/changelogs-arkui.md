# ArkUI子系统变更说明

## cl.arkui.1 UIExtensionComponent 获焦能力变更

**访问级别**

公共能力

**变更原因**

UIExtensionComponent获焦后，其拉起的UIExtensionAbility窗口内焦点不会停留在根容器，会下发到第一个可获焦子节点，根据第一个可获焦子节点的类型，可能出现软键盘拉起的情况。

**变更影响**

此变更为不兼容变更，涉及系统应用适配。

- 变更前：当UIExtensionComponent获焦，其拉起的UIExtensionAbility窗口内焦点不会停留在根容器，会下发到第一个可获焦子节点

- 变更后：外部走焦到UIExtensionAbility需要进行下发；跳焦到UIExtensionAbility时与UIAbility保持统一规则，即：在拉起一个层级页面且该页面未设置defaultFocus、未通过API请求焦点时，焦点能够停留在根容器。

**起始 API Level**

18

**变更发生版本**

从OpenHarmony SDK 6.1.0.26开始。

**变更的接口/组件**

涉及组件：[UIExtensionComponent](../../../application-dev/ui/arkts-ui-extension-components-sys.md)。

该变更可能导致：

在UIExtensionAbility内，层级页面未设置defaultFocus、未通过API请求焦点时，焦点停留在根容器，第一个可获焦子组件未获焦。

**适配指导**

给第一个可获焦子组件设置defaultFocus，或通过API为第一个可获焦子组件请求焦点。
