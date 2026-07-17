# CapitalizeMode

枚举，定义了文本首字母大写的不同模式。

| 名称 | 值 | 说明 |  
| -------- | -- | -------- |  
| NONE | 0 | 不进行任何首字母大写处理。

**使用场景：**适用于无需自动大写的输入框，如密码输入、验证码输入等。|  
| SENTENCES | 1 | 每个句子的首字母大写。

**使用场景：**适用于普通文本输入框，如聊天、备忘录等，自动在句号等标点后将首字母大写。|  
| WORDS | 2 | 每个单词首字母大写。

**使用场景：**适用于标题、人名等需要每个单词首字母大写的场景。|  
| CHARACTERS | 3 | 每个字母都大写。

**使用场景：**适用于全大写输入场景，如缩写词输入（如URL中的域名部分）。|

**起始版本：** 20

<!--Device-inputMethod-export enum CapitalizeMode--><!--Device-inputMethod-export enum CapitalizeMode-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## NONE

```TypeScript
NONE = 0
```

不进行任何首字母大写处理。

**起始版本：** 20

<!--Device-CapitalizeMode-NONE = 0--><!--Device-CapitalizeMode-NONE = 0-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## SENTENCES

```TypeScript
SENTENCES
```

每个句子的首字母大写。

**起始版本：** 20

<!--Device-CapitalizeMode-SENTENCES--><!--Device-CapitalizeMode-SENTENCES-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## WORDS

```TypeScript
WORDS
```

每个单词首字母大写。

**起始版本：** 20

<!--Device-CapitalizeMode-WORDS--><!--Device-CapitalizeMode-WORDS-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## CHARACTERS

```TypeScript
CHARACTERS
```

每个字母都大写。

**起始版本：** 20

<!--Device-CapitalizeMode-CHARACTERS--><!--Device-CapitalizeMode-CHARACTERS-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

