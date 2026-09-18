# OmitThisParameter

```TypeScript
type OmitThisParameter<T> = unknown extends ThisParameterType<T> ? T : T extends (...args: infer A) => infer R ? (...args: A) => R : T
```

Removes the 'this' parameter from a function type.

**Type:** unknown extends ThisParameterType&lt;T&gt; ? T : T extends (...args: infer A) =&gt; infer R ? (...args: A) =&gt; R : T
