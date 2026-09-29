# Pick

```TypeScript
type Pick<T, K extends keyof T> = {
    [P in K]: T[P];
}
```

From T, pick a set of properties whose keys are in the union K

<!--Device-unnamed-type Pick<T, K extends keyof T> = {    [P in K]: T[P];}--><!--Device-unnamed-type Pick<T, K extends keyof T> = {    [P in K]: T[P];}-End-->

**Type:** {
    [P in K]: T[P];
}
