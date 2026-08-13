# withinComponent

## withinComponent

```TypeScript
export function withinComponent(com: Component): On
```

要求目标组件位于由给定[Component](arkts-test-uitest-component-c.md#Component)指定的另一个组件的内部 对象，用于相对于组件定位。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-ON-export function withinComponent(com: Component): On--><!--Device-ON-export function withinComponent(com: Component): On-End-->

**系统能力：** SystemCapability.Test.UiTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| com | [Component](arkts-test-uitest-component-c.md) | 是 | 描述目标组件所在的组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [On](arkts-test-uitest-on-c.md) | this { |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17000007](../errorcode-uitest.md#17000007-参数不合法) | Parameter verification failed. |

