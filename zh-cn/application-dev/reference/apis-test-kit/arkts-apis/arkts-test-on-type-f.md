# type

## type

```TypeScript
export function type(tp: string): On
```

Specifies the type of the target Component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ON-export function type(tp: string): On--><!--Device-ON-export function type(tp: string): On-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tp | string | 是 | The type value. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | this { |


## type

```TypeScript
export function type(tp: string, pattern: MatchPattern): On
```

Specifies the type of the target Component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ON-export function type(tp: string, pattern: MatchPattern): On--><!--Device-ON-export function type(tp: string, pattern: MatchPattern): On-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tp | string | 是 | The type value. |
| pattern | [MatchPattern](arkts-test-uitest-matchpattern-e.md) | 是 | the [MatchPattern](arkts-test-uitest-matchpattern-e.md#MatchPattern) of the text value,Set it default [EQUALS](arkts-test-uitest-matchpattern-e.md#EQUALS) if null or undefined. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | this { |

