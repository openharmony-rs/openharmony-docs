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

<!--Device-Locale-maximize(): Locale--><!--Device-Locale-maximize(): Locale-End-->

## minimize

```TypeScript
minimize(): Locale
```

Attempts to remove information about the locale that would be added by calling `Locale.maximize()`.

<!--Device-Locale-minimize(): Locale--><!--Device-Locale-minimize(): Locale-End-->

## toString

```TypeScript
toString(): BCP47LanguageTag
```

Returns the locale's full locale identifier string.

<!--Device-Locale-toString(): BCP47LanguageTag--><!--Device-Locale-toString(): BCP47LanguageTag-End-->

## baseName

```TypeScript
baseName: string
```

A string containing the language, and the script and region if available.

**Type:** string

<!--Device-Locale-baseName: string--><!--Device-Locale-baseName: string-End-->

## language

```TypeScript
language: string
```

The primary language subtag associated with the locale.

**Type:** string

<!--Device-Locale-language: string--><!--Device-Locale-language: string-End-->
