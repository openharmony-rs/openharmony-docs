# Readonly

```TypeScript
type Readonly<T> = {
    readonly [P in keyof T]: T[P];
}
```

Make all properties in T readonly

**Type:** {
    readonly [P in keyof T]: T[P];
}
