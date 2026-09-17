# QueryParamValue

```TypeScript
export type QueryParamValue = string | number | boolean | null | undefined
```

Defines the single-value type that can be used in **QueryParamObject**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

| Type | Description |
| --- | --- |
| string | String type. |
| int | Number type, which is converted into a string before being encoded. |
| boolean | Boolean type, which is converted into a string before being encoded. |
| null | Null type, which is serialized in the format of only the key without the = value. |
| undefined | Undefined type, which is serialized in the format of only the key without the = value. |
