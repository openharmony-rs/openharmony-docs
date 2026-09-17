# Extract

```TypeScript
type Extract<T, U> = T extends U ? T : never
```

Extract from T those types that are assignable to U

**Type:** T extends U ? T : never
