# Partial

```TypeScript
type Partial<T> = {
    [P in keyof T]?: T[P];
}
```

Make all properties in T optional

<!--Device-unnamed-type Partial<T> = {    [P in keyof T]?: T[P];}--><!--Device-unnamed-type Partial<T> = {    [P in keyof T]?: T[P];}-End-->

**Type:** {
    [P in keyof T]?: T[P];
}
