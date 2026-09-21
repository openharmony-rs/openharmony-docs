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

## entries

```TypeScript
entries(): IterableIterator<[T, T]>
```

Returns an iterable of [v,v] pairs for every value `v` in the set.

## keys

```TypeScript
keys(): IterableIterator<T>
```

Despite its name, returns an iterable of the values in the set.

## values

```TypeScript
values(): IterableIterator<T>
```

Returns an iterable of values in the set.
