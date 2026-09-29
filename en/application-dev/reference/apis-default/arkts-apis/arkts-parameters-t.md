# Parameters

```TypeScript
type Parameters<T extends (...args: any) => any> = T extends (...args: infer P) => any ? P : never
```

Obtain the parameters of a function type in a tuple

<!--Device-unnamed-type Parameters<T extends (...args: any) => any> = T extends (...args: infer P) => any ? P : never--><!--Device-unnamed-type Parameters<T extends (...args: any) => any> = T extends (...args: infer P) => any ? P : never-End-->

**Type:** T extends (...args: infer P) =&gt; any ? P : never
