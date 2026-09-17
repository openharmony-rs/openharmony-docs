# SymbolConstructor

## Modules to Import

```TypeScript
```

## hasInstance

```TypeScript
readonly hasInstance: unique symbol
```

A method that determines if a constructor object recognizes an object as one of the constructor’s instances. Called by the semantics of the instanceof operator.

**Type:** unique symbol

## isConcatSpreadable

```TypeScript
readonly isConcatSpreadable: unique symbol
```

A Boolean value that if true indicates that an object should flatten to its array elements by Array.prototype.concat.

**Type:** unique symbol

## match

```TypeScript
readonly match: unique symbol
```

A regular expression method that matches the regular expression against a string. Called by the String.prototype.match method.

**Type:** unique symbol

## replace

```TypeScript
readonly replace: unique symbol
```

A regular expression method that replaces matched substrings of a string. Called by the String.prototype.replace method.

**Type:** unique symbol

## search

```TypeScript
readonly search: unique symbol
```

A regular expression method that returns the index within a string that matches the regular expression. Called by the String.prototype.search method.

**Type:** unique symbol

## species

```TypeScript
readonly species: unique symbol
```

A function valued property that is the constructor function that is used to create derived objects.

**Type:** unique symbol

## split

```TypeScript
readonly split: unique symbol
```

A regular expression method that splits a string at the indices that match the regular expression. Called by the String.prototype.split method.

**Type:** unique symbol

## toPrimitive

```TypeScript
readonly toPrimitive: unique symbol
```

A method that converts an object to a corresponding primitive value. Called by the ToPrimitive abstract operation.

**Type:** unique symbol

## toStringTag

```TypeScript
readonly toStringTag: unique symbol
```

A String value that is used in the creation of the default string description of an object. Called by the built-in method Object.prototype.toString.

**Type:** unique symbol

## unscopables

```TypeScript
readonly unscopables: unique symbol
```

An Object whose own property names are property names that are excluded from the 'with'environment bindings of the associated objects.

**Type:** unique symbol
