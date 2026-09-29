# Omit

```TypeScript
type Omit<T, K extends keyof any> = Pick<T, Exclude<keyof T, K>>
```

Construct a type with the properties of T except for those in type K.

<!--Device-unnamed-type Omit<T, K extends keyof any> = Pick<T, Exclude<keyof T, K>>--><!--Device-unnamed-type Omit<T, K extends keyof any> = Pick<T, Exclude<keyof T, K>>-End-->

**Type:** Pick&lt;T, Exclude&lt;keyof T, K&gt;&gt;
