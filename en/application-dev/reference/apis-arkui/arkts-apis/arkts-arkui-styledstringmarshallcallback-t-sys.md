# StyledStringMarshallCallback (System API)

```TypeScript
declare type StyledStringMarshallCallback = (marshallableVal: StyledStringMarshallingValue) => ArrayBuffer
```

Defines a callback for marshalling [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md).

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare type StyledStringMarshallCallback = (marshallableVal: StyledStringMarshallingValue) => ArrayBuffer--><!--Device-unnamed-declare type StyledStringMarshallCallback = (marshallableVal: StyledStringMarshallingValue) => ArrayBuffer-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| marshallableVal | [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md) | Yes | UserDataSpan object in the styled string that requires custom serialization. In the callback function, the developer selects the corresponding serialization API based on the type of this parameter to convert it into an ArrayBuffer. |

**Return value:**

| Type | Description |
| --- | --- |
| ArrayBuffer | Marshaled data of [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md). |
