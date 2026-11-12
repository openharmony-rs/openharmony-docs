# QueryParamObject

```TypeScript
export type QueryParamObject = Record<string, QueryParamValue | QueryParamValue[]>
```

用于构造URL查询参数的键值对象类型。

**说明：** 

(1) 对象的每个属性名作为URL参数的key，属性值作为参数值。例如`{ scene: 'demo', page: 1 }`会序列化为`scene=demo&page=1`。

(2) 当属性值为数组时，会展开为同名多参数。例如`{ tag: ['a', 'b'] }`会序列化为`tag=a&tag=b`。

(3) key和value由系统自动进行URL编码，开发者应传入原始未编码内容。

(4) 如需严格控制参数顺序或重复键顺序，建议直接使用queryParams的string形式。

**类型：** Record&lt;string, [QueryParamValue](arkts-network-http-queryparamvalue-t.md) | [QueryParamValue](arkts-network-http-queryparamvalue-t.md)[]&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-http-export type QueryParamObject = Record<string, QueryParamValue | QueryParamValue[]>--><!--Device-http-export type QueryParamObject = Record<string, QueryParamValue | QueryParamValue[]>-End-->

**系统能力：** SystemCapability.Communication.NetStack
