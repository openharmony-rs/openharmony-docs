# AbilityComponent (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zjsxstar-->
<!--Designer: @sunbees-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!--deprecated_code_no_check-->

**AbilityComponent** is a container for independently displaying an ability.

>  **NOTE**
>
>  This component is deprecated since API version 10. You are advised to use [UIExtensionComponent](ts-container-ui-extension-component-sys.md) instead.
>
>  This component is supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
>  The APIs provided by this component are system APIs.

## Constraints

**AbilityComponent** is rendered at an independent layer and cannot be overlaid by other display content.

**AbilityComponent** does not support input event processing. Events are not routed through the current ability but are instead distributed directly to the internal ability for processing.

For **AbilityComponent**, only **width** and **height** must be set and can be set. Furthermore, they do not support dynamic updates.

The started ability must inherit from [WindowExtension](../js-apis-application-windowExtensionAbility-sys.md).

## Child Components

Not supported


## APIs

AbilityComponent(value: {want: Want})

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                  | Mandatory| Description               |
| ------ | ---------------------------------------------------------- | ---- | ----------------------- |
| want   | [Want](../../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | Description of the ability to be loaded by default.|


## Events

### onConnect

onConnect(callback:()&nbsp;=&gt;&nbsp;void)

Called when the **AbilityComponent** environment is started. After the callback, the methods of **AbilityComponent** can be used.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### onDisconnect

onDisconnect(callback:()&nbsp;=&gt;&nbsp;void)

Called when the **AbilityComponent** environment is destroyed.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## Example

```ts
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
