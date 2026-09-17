# WordBreak

The word break rule.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NORMAL

```TypeScript
NORMAL = 0
```

Word breaks can occur between any two characters for Chinese, Japanese, and Korean (CJK) text, but can occur only at a space character for non-CJK text (such as English).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BREAK_ALL

```TypeScript
BREAK_ALL = 1
```

Line breaks can occur between any two characters for non-CJK text. For CJK text, the effect is the same as that of **NORMAL**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BREAK_WORD

```TypeScript
BREAK_WORD = 2
```

This option has the same effect as **BREAK_ALL** for non-CJK text, except that it preferentially wraps lines at appropriate characters (for example, spaces). If no breakpoints are found, it breaks between any two characters. For CJK text, the effect is the same as that of **NORMAL**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## HYPHENATION

```TypeScript
HYPHENATION = 3
```

This option has the same effect as **BREAK_ALL** for non-CJK text, except that it preferentially wraps lines at appropriate characters (for example, spaces). If no breakpoints are found, it breaks between any two characters. For CJK text, the effect is the same as that of **NORMAL**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
