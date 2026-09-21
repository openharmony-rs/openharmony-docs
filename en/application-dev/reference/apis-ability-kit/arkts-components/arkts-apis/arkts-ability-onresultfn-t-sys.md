# OnResultFn (System API)

```TypeScript
type OnResultFn = (parameter: AbilityResult) => void
```

Defines a onResult function.

@typedef { function } OnResultFn

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppExtension.VerticalPanel

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [AbilityResult](arkts-ability-abilityresult-abilityresult-i.md) | Yes | The Parameter returned if the UIExtensionAbility call terminateSelfWithResult. |

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
