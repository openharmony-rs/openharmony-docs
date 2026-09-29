# Required

```TypeScript
type Required<T> = {
    [P in keyof T]-?: T[P];
}
```

Make all properties in T required

<!--Device-unnamed-type Required<T> = {    [P in keyof T]-?: T[P];}--><!--Device-unnamed-type Required<T> = {    [P in keyof T]-?: T[P];}-End-->

**Type:** {
    [P in keyof T]-?: T[P];
}
