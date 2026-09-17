# RelativeTimeFormatUnitSingular

```TypeScript
type RelativeTimeFormatUnitSingular =
        | "year"
        | "quarter"
        | "month"
        | "week"
        | "day"
        | "hour"
        | "minute"
        | "second"
```

Value of the `unit` property in objects returned by `Intl.RelativeTimeFormat.prototype.formatToParts()`. `formatToParts` and `format` methods accept either singular or plural unit names as input, but `formatToParts` only outputs singular (e.g. "day") not plural (e.g."days").

[MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/RelativeTimeFormat/formatToParts#Using_formatToParts).

| Type | Description |
| --- | --- |
| "year" |  |
| "quarter" |  |
| "month" |  |
| "week" |  |
| "day" |  |
| "hour" |  |
| "minute" |  |
| "second" |  |
