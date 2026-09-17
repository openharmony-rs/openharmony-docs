# AbilityComponent (System API)

**AbilityComponent** is a container for independently displaying an ability.

## AbilityComponent

```TypeScript
AbilityComponent(value: { want: import('../api/@ohos.app.ability.Want').default })
```

Construct the ability component. Called when the ability component is used.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** UIExtensionComponentInterface

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | { want: import('../api/@ohos.app.ability.Want').default } | Yes |  |

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
