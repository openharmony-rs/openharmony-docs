# QueryParamObject

```TypeScript
export type QueryParamObject = Record<string, QueryParamValue | QueryParamValue[]>
```

Defines the key-value object type used to construct URL query parameters.

> **NOTE:** 
> 
> (1) The property name is used as the key of the **QueryParamObject** parameter. The corresponding property value
> can be a single **QueryParamValue** or a **QueryParamValue** array.

> (2) The array will be expanded into multiple parameters with the same name. For example, **{ tag: ['a', 'b'] }**
> will be serialized into **tag=a&tag=b**.

> (3) The key and value are automatically URL-encoded by the system. You should pass the original, unencoded
> content.

> (4) To strictly control the parameter sequence or repeat the key sequence, you are advised to use the **string**
> of **queryParams**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

**Type:** Record&lt;string, [QueryParamValue](arkts-network-http-queryparamvalue-t.md) | [QueryParamValue](arkts-network-http-queryparamvalue-t.md)[]&gt;
