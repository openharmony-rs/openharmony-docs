# WeakRef

```TypeScript
interface WeakRef<T extends object>
```

## Modules to Import

```TypeScript
```

## deref

```TypeScript
deref(): T | undefined
```

Returns the WeakRef instance's target object, or undefined if the target object has been reclaimed.

<!--Device-WeakRef-deref(): T | undefined--><!--Device-WeakRef-deref(): T | undefined-End-->

## [Symbol.toStringTag]

```TypeScript
readonly [Symbol.toStringTag]: "WeakRef"
```

**Type:** "WeakRef"
