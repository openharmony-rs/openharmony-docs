# FinalizationRegistry

## Modules to Import

```TypeScript
```

## register

```TypeScript
register(target: object, heldValue: T, unregisterToken?: object): void
```

Registers an object with the registry.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | object | Yes |  |
| heldValue | T | Yes |  |
| unregisterToken | object | No |  |

## unregister

```TypeScript
unregister(unregisterToken: object): void
```

Unregisters an object from the registry.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| unregisterToken | object | Yes |  |

## [Symbol.toStringTag]

```TypeScript
readonly [Symbol.toStringTag]: "FinalizationRegistry"
```

**Type:** "FinalizationRegistry"
