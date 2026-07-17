# WordBreak

Enum of word break

**起始版本：** 11

<!--Device-unnamed-declare enum WordBreak--><!--Device-unnamed-declare enum WordBreak-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NORMAL

```TypeScript
NORMAL = 0
```

By default, CJK text can be wrapped between any 2 characters, and non-CJK text can only be wrapped in spaces.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WordBreak-NORMAL = 0--><!--Device-WordBreak-NORMAL = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BREAK_ALL

```TypeScript
BREAK_ALL = 1
```

Non-CJK text be wrapped at any character

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WordBreak-BREAK_ALL = 1--><!--Device-WordBreak-BREAK_ALL = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## BREAK_WORD

```TypeScript
BREAK_WORD = 2
```

Non-CJK text can be wrapped at any character and if a complete word can be preserved in space breaks, the word must be kept on the line.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WordBreak-BREAK_WORD = 2--><!--Device-WordBreak-BREAK_WORD = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## HYPHENATION

```TypeScript
HYPHENATION = 3
```

For supported languages, line breaks can be performed by syllables.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-WordBreak-HYPHENATION = 3--><!--Device-WordBreak-HYPHENATION = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

