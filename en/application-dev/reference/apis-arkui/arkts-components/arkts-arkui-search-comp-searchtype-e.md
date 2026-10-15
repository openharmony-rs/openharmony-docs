# SearchType

```TypeScript
declare enum SearchType
```

Enumerates the search input box types.

**Since:** 11

<!--Device-unnamed-declare enum SearchType--><!--Device-unnamed-declare enum SearchType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## EMAIL

```TypeScript
EMAIL = 5
```

Email address input mode.

Supports digits, letters, underscores, decimal points, !, #, $, %, &, ', *, +, -, /, =, ?, ^,`, {, |, }, ~, and the @ character (only one @ character is allowed).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchType-EMAIL = 5--><!--Device-SearchType-EMAIL = 5-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NORMAL

```TypeScript
NORMAL = 0
```

Basic input mode with no special restrictions.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchType-NORMAL = 0--><!--Device-SearchType-NORMAL = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NUMBER

```TypeScript
NUMBER = 2
```

Pure number input mode.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchType-NUMBER = 2--><!--Device-SearchType-NUMBER = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NUMBER_DECIMAL

```TypeScript
NUMBER_DECIMAL = 12
```

Number input mode with a decimal point.

Supports digits and a decimal point (only one decimal point is allowed).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchType-NUMBER_DECIMAL = 12--><!--Device-SearchType-NUMBER_DECIMAL = 12-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ONE_TIME_CODE

```TypeScript
ONE_TIME_CODE = 14
```

Verification code input mode with no special restrictions. In this mode, the system input method is pulled up by default after the component gains focus.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-SearchType-ONE_TIME_CODE = 14--><!--Device-SearchType-ONE_TIME_CODE = 14-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PHONE_NUMBER

```TypeScript
PHONE_NUMBER = 3
```

Phone number input mode.

Supports digits, spaces, +, -, *, #, (, and ), with no length limit.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchType-PHONE_NUMBER = 3--><!--Device-SearchType-PHONE_NUMBER = 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## URL

```TypeScript
URL = 13
```

URL input mode with no special restrictions.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchType-URL = 13--><!--Device-SearchType-URL = 13-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
