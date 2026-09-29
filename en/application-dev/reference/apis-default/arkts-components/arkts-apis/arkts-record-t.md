# Record

```TypeScript
type Record<K extends keyof any, T> = {
    [P in K]: T;
}
```

Construct a type with a set of properties K of type T

<!--Device-unnamed-type Record<K extends keyof any, T> = {    [P in K]: T;}--><!--Device-unnamed-type Record<K extends keyof any, T> = {    [P in K]: T;}-End-->

**Type:** {
    [P in K]: T;
}
