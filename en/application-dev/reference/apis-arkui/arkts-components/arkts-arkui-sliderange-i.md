# SlideRange

Defines the callback type used in **SlideRange**.

> **NOTE:** 
> 
> - Currently, this API takes effect only when **min** ≤ **from** ≤ **to** ≤ **max** (the values of **min** and
> **max** do not depend on the values set, but on the actual values that take effect).
> 
> - You can set either **from** or **to**, or you can set both **from** and **to**.
> 
> - When the API is effective, if the set **from** value is between the adjacent multiples of **step**, then **from**takes the value of the left interval multiple of **step** or **min** as the corrected value.
> 
> - When the API is effective, if the set **to** value is between the adjacent multiples of **step**, then **to**takes the value of the right interval multiple of **step** or **MAX** as the corrected value.
> 
> - After **from** and **to** have taken their corrected values, when **value** is **undefined** or **null**, it takes the same value as **from**; when **value** is a number type, and if **value** ≤ **from**, then it takes
> **from**; if **value**
> **to**, then it takes **to**.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## from

```TypeScript
from?: number
```

Start of the slide range.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## to

```TypeScript
to?: number
```

End of the slide range.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
