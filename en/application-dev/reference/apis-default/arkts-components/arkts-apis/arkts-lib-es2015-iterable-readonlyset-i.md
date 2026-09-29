# ReadonlySet

```TypeScript
interface ReadonlySet<T>
```

## Modules to Import

```TypeScript
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<T>
```

Iterates over values in the set.

<!--Device-ReadonlySet-[Symbol.iterator](): IterableIterator<T>--><!--Device-ReadonlySet-[Symbol.iterator](): IterableIterator<T>-End-->

## entries

```TypeScript
entries(): IterableIterator<[T, T]>
```

Returns an iterable of [v,v] pairs for every value `v` in the set.

<!--Device-ReadonlySet-entries(): IterableIterator<[T, T]>--><!--Device-ReadonlySet-entries(): IterableIterator<[T, T]>-End-->

## keys

```TypeScript
keys(): IterableIterator<T>
```

Despite its name, returns an iterable of the values in the set.

<!--Device-ReadonlySet-keys(): IterableIterator<T>--><!--Device-ReadonlySet-keys(): IterableIterator<T>-End-->

## values

```TypeScript
values(): IterableIterator<T>
```

Returns an iterable of values in the set.

<!--Device-ReadonlySet-values(): IterableIterator<T>--><!--Device-ReadonlySet-values(): IterableIterator<T>-End-->
