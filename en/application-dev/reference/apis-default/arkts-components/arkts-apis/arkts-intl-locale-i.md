# Locale

```TypeScript
interface Locale extends LocaleOptions
```

## Modules to Import

```TypeScript
```

## maximize

```TypeScript
maximize(): Locale
```

Gets the most likely values for the language, script, and region of the locale based on existing values.

## minimize

```TypeScript
minimize(): Locale
```

Attempts to remove information about the locale that would be added by calling `Locale.maximize()`.

## toString

```TypeScript
toString(): BCP47LanguageTag
```

Returns the locale's full locale identifier string.

## baseName

```TypeScript
baseName: string
```

A string containing the language, and the script and region if available.

**Type:** string

## language

```TypeScript
language: string
```

The primary language subtag associated with the locale.

**Type:** string
