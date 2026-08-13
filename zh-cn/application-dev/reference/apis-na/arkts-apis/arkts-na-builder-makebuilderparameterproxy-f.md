# makeBuilderParameterProxy

## makeBuilderParameterProxy

```TypeScript
export declare function makeBuilderParameterProxy<T>(
    instance: T,
    propertyGetters: Map<string, BuilderParameterCallback>,
    initializer?: Callback<T>
): T
```

Make Proxy for Builder parameter.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function makeBuilderParameterProxy<T>(    instance: T,    propertyGetters: Map<string, BuilderParameterCallback>,    initializer?: Callback<T>): T--><!--Device-unnamed-export declare function makeBuilderParameterProxy<T>(    instance: T,    propertyGetters: Map<string, BuilderParameterCallback>,    initializer?: Callback<T>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | T | 是 | Builder parameter instance |
| propertyGetters | Map&lt;string, [BuilderParameterCallback](arkts-na-builderparametercallback-t.md)&gt; | 是 | getter callbacks for each property name |
| initializer | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;T&gt; | 否 | optional callback to initialize proxied instance |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | proxied parameter instance |

