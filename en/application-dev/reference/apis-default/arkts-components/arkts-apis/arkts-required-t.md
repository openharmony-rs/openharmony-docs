# Required

```TypeScript
type Required<T> = {
    [P in keyof T]-?: T[P];
}
```

Make all properties in T required

**Type:** {
    [P in keyof T]-?: T[P];
}
