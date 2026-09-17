# MethodDecorator

```TypeScript
declare type MethodDecorator = <T>(target: Object, propertyKey: string | symbol, descriptor: TypedPropertyDescriptor<T>) => TypedPropertyDescriptor<T> | void
```

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | Object | Yes |  |
| propertyKey | string &#124; symbol | Yes |  |
| descriptor | [TypedPropertyDescriptor](arkts-lib-es5-typedpropertydescriptor-i.md)&lt;T&gt; | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [TypedPropertyDescriptor](arkts-lib-es5-typedpropertydescriptor-i.md)&lt;T&gt; &#124; void | - |
