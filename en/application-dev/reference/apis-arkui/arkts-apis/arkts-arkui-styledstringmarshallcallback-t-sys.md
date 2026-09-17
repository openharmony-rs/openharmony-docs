# StyledStringMarshallCallback (System API)

```TypeScript
declare type StyledStringMarshallCallback = (marshallableVal: StyledStringMarshallingValue) => ArrayBuffer
```

Defines a callback for marshalling [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md).

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| marshallableVal | [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md) | Yes | Object to be marshaled. |

**Return value:**

| Type | Description |
| --- | --- |
| ArrayBuffer | Marshaled data of [StyledStringMarshallingValue](arkts-arkui-styledstringmarshallingvalue-t-sys.md). |
