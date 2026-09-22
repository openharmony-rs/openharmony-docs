# OnErrorFn (System API)

```TypeScript
type OnErrorFn = (code: number, name: string, message: string) => void
```

Defines a OnError function.

@typedef { function } OnErrorFn

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppExtension.VerticalPanel

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | The code returned if the UIAbility or UIExtensionAbility failed to start. |
| name | string | Yes | The name returned if the UIAbility or UIExtensionAbility failed to start. |
| message | string | Yes | The message returned if the UIAbility or UIExtensionAbility failed to start. |

**Examples**

```TypeScript
let callback: verticalPanelManager.PanelStartCallback = {
  onError: (code: number, name: string, message: string): void => {
    console.info(`startVerticalPanel onError code ${code} name: ${name} message: ${message}`);
  },
  onResult: (result: common.AbilityResult):void => {
    console.info(`startVerticalPanel onResult result ${JSON.stringify(result)}`);
  },
}
```
