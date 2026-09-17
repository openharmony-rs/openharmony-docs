# StyledStringUnmarshallCallback (System API)

```TypeScript
declare type StyledStringUnmarshallCallback = (buf: ArrayBuffer) => StyledStringMarshallingValue
```

Defines a callback for unmarshalling an ArrayBuffer to obtain [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md).

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buf | ArrayBuffer | Yes | Marshaled data of [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md) | [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md) obtained after unmarshalling. |
