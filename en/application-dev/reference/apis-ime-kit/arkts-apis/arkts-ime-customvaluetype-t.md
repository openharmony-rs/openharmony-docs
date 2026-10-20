# CustomValueType

```TypeScript
export type CustomValueType = number | string | boolean
```

Represents the value type of extension information. The specific type of the parameter depends on its function. You can select an appropriate value type based on the meaning of the configuration item: numeric configurations (such as font size and weight coefficient) use the number type; text configurations (such as input mode name and theme identifier) use the string type; switch configurations (such as whether to enable a feature and whether to display a panel) use the boolean type.

**Since:** 22

<!--Device-unnamed-export type CustomValueType = int | string | boolean--><!--Device-unnamed-export type CustomValueType = int | string | boolean-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

| Type | Description |
| --- | --- |
| int | Number. |
| string | String. |
| boolean | Boolean. |
