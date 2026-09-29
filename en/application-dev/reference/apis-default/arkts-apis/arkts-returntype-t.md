# ReturnType

```TypeScript
type ReturnType<T extends (...args: any) => any> = T extends (...args: any) => infer R ? R : any
```

Obtain the return type of a function type

<!--Device-unnamed-type ReturnType<T extends (...args: any) => any> = T extends (...args: any) => infer R ? R : any--><!--Device-unnamed-type ReturnType<T extends (...args: any) => any> = T extends (...args: any) => infer R ? R : any-End-->

**Type:** T extends (...args: any) =&gt; infer R ? R : any
