# originalText

## originalText

```TypeScript
export function originalText(text: string, pattern?: MatchPattern): On
```

Specifies the original text for the target Component. If the accessibility property 'accessibilityLevel' of a component is set to 'no' or 'no-hide-descendants', you will not be able to use [text](arkts-test-uitest-on-c.md#text) to match the component with the specified original text, but you can use this method to achieve it; if the component does not set the above accessibility property, this method has no difference with [text](arkts-test-uitest-on-c.md#text)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ON-export function originalText(text: string, pattern?: MatchPattern): On--><!--Device-ON-export function originalText(text: string, pattern?: MatchPattern): On-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | the original text value. |
| pattern | [MatchPattern](arkts-test-uitest-matchpattern-e.md) | 否 | the [MatchPattern](arkts-test-uitest-matchpattern-e.md#MatchPattern) of the text value, Set it default [EQUALS](arkts-test-uitest-matchpattern-e.md#EQUALS) if null or undefined. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | this { |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000007](../errorcode-uitest.md#17000007-参数不合法) | Parameter verification failed. |

