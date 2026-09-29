# ConstructorParameters

```TypeScript
type ConstructorParameters<T extends abstract new (...args: any) => any> = T extends abstract new (...args: infer P) => any ? P : never
```

Obtain the parameters of a constructor function type in a tuple

<!--Device-unnamed-type ConstructorParameters<T extends abstract new (...args: any) => any> = T extends abstract new (...args: infer P) => any ? P : never--><!--Device-unnamed-type ConstructorParameters<T extends abstract new (...args: any) => any> = T extends abstract new (...args: infer P) => any ? P : never-End-->

**Type:** T extends abstract new (...args: infer P) =&gt; any ? P : never
