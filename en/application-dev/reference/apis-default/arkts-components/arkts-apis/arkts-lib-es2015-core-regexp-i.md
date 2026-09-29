# RegExp

```TypeScript
interface RegExp
```

## Modules to Import

```TypeScript
```

## flags

```TypeScript
readonly flags: string
```

Returns a string indicating the flags of the regular expression in question. This field is read-only. The characters in this string are sequenced and concatenated in the following order:

- "g" for global  
- "i" for ignoreCase  
- "m" for multiline  
- "u" for unicode  
- "y" for sticky

If no flags are set, the value is the empty string.

**Type:** string

<!--Device-RegExp-readonly flags: string--><!--Device-RegExp-readonly flags: string-End-->

## sticky

```TypeScript
readonly sticky: boolean
```

Returns a Boolean value indicating the state of the sticky flag (y) used with a regular expression. Default is false. Read-only.

**Type:** boolean

<!--Device-RegExp-readonly sticky: boolean--><!--Device-RegExp-readonly sticky: boolean-End-->

## unicode

```TypeScript
readonly unicode: boolean
```

Returns a Boolean value indicating the state of the Unicode flag (u) used with a regular expression. Default is false. Read-only.

**Type:** boolean

<!--Device-RegExp-readonly unicode: boolean--><!--Device-RegExp-readonly unicode: boolean-End-->
