# AbilityComponent (System API)

**AbilityComponent** is a container for independently displaying an ability.

> **NOTE:** 
> 
> This component is deprecated since API version 10. You are advised to use
> [UIExtensionComponent](arkts-arkui-uiextensioncomponent-comp-sys.md) instead.
> 
> The APIs provided by this component are system APIs.

## Constraints

**AbilityComponent** is rendered at an independent layer and cannot be overlaid by other display content.

**AbilityComponent** does not support input event processing. Events are not routed through the current ability but are instead distributed directly to the internal ability for processing.

For **AbilityComponent**, only **width** and **height** must be set and can be set. Furthermore, they do not support dynamic updates.

The started ability must inherit from [WindowExtension](../arkts-apis/arkts-arkui-application-windowextensionability-windowextensionability-c-sys.md).

## Child Components

Not supported

## AbilityComponent

```TypeScript
AbilityComponent(value: { want: import('../api/@ohos.app.ability.Want').default })
```

Construct the ability component. Called when the ability component is used.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [UIExtensionComponentInterface](arkts-arkui-uiextensioncomponent-comp-sys.md#uiextensioncomponentinterface)

<!--Device-AbilityComponentInterface-(value: { want: import('../api/@ohos.app.ability.Want').default }): AbilityComponentAttribute--><!--Device-AbilityComponentInterface-(value: { want: import('../api/@ohos.app.ability.Want').default }): AbilityComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | { want: import('../api/@ohos.app.ability.Want').default } | Yes | Description of the ability to be loaded by default. |

## Summary

## Examples

```TypeScript
// xxx.ets
@Entry
@Component
struct MyComponent {

  build() {
      Column() {
          AbilityComponent({
              want: {
                  bundleName: '',
                  abilityName: ''
              },
          })
          .onConnect(() => {
              console.log('AbilityComponent connect')
          })
          .onDisconnect(() => {
              console.log('AbilityComponent disconnect')
          })
      }
  }
}
```
