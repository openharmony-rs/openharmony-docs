# Partial

```TypeScript
type Partial<T> = {
    [P in keyof T]?: T[P];
}
```

Make all properties in T optional

**Type:** {
    [P in keyof T]?: T[P];
}
