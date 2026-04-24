# ArkUI子系统变更说明

## cl.arkui.1 UIExtensionComponent获焦能力变更

**访问级别**

公共能力

**变更原因**

UIExtensionComponent获焦后，其拉起的UIExtensionAbility窗口内焦点不会停留在Scope类型的根容器，而是下发到第一个Node类型的可获焦子节点。当获焦子节点为TextInput时，会出现软键盘被意外拉起的情况。

**变更影响**

此变更涉及应用适配。

- 变更前：UIExtensionComponent获焦时，其拉起的UIExtensionAbility窗口内焦点直接下发到第一个可获焦子节点。

- 变更后：UIExtensionComponent获焦时，
1. 如果外部走焦到UIExtensionAbility，焦点正常下发到第一个可获焦子节点。
2. 如果跳焦到UIExtensionAbility，则与UIAbility保持统一规则。两者在拉起一个层级页面且该页面未设置[defaultFocus](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-focus.md#defaultfocus9)、未[主动请求焦点](../../../application-dev/ui/arkts-common-events-focus-event.md#主动获焦失焦)时，焦点均停留在根容器，不下发到子节点。

**起始 API Level**

18

**变更发生版本**

从OpenHarmony SDK 6.1.0.26开始。

**变更的接口/组件**

[UIExtensionComponent](../../../application-dev/ui/arkts-ui-extension-components-sys.md)。

**适配指导**

在跳焦到UIExtensionAbility的场景下，若期望第一个可获焦子组件自动获焦，需显式进行焦点设置：

- 方式一：在UIExtensionAbility的页面中，将第一个可获焦子组件[defaultFocus](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-focus.md#defaultfocus9)设置为true，使其成为层级页面的默认焦点。

```ts
@Entry
@Component
struct UIExtensionPage {
  build() {
    Column({ space: 20 }) {
      TextInput({ placeholder: 'Input something...' })
        .width(300)
        .height(50)
        .defaultFocus(true)

      Button('Submit')
        .width(200)
        .height(50)
    }.width('100%').height('100%').justifyContent(FlexAlign.Center)
  }
}
```

- 方式二：在UIExtensionAbility的页面中，通过[requestFocus](../../../application-dev/ui/arkts-common-events-focus-event.md#主动获焦失焦)主动为第一个可获焦子组件请求焦点。

```ts
@Entry
@Component
struct UIExtensionPage {
  build() {
    Column({ space: 20 }) {
      TextInput({ placeholder: 'Input something...' })
        .width(300)
        .height(50)
        .id('targetInput')

      Button('Submit')
        .width(200)
        .height(50)
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
    .onAppear(() => {
      this.getUIContext().getFocusController().requestFocus('targetInput');
    })
  }
}
```
