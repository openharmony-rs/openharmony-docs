# Readonly

```TypeScript
type Readonly<T> = {
    readonly [P in keyof T]: T[P];
}
```

Make all properties in T readonly

<!--Device-unnamed-type Readonly<T> = {    readonly [P in keyof T]: T[P];}--><!--Device-unnamed-type Readonly<T> = {    readonly [P in keyof T]: T[P];}-End-->

**Type:** {
    readonly [P in keyof T]: T[P];
}
