# FocusRule（系统接口）

```TypeScript
export type FocusRule = 'bypassSelf' | 'bypassSelfDescendants' |
'checkSelf' | 'checkSelfBypassDescendants'
```

表示查找可聚焦节点时，如何判断起始节点及其子节点的聚焦能力。

**起始版本：** 23

<!--Device-unnamed-export type FocusRule = 'bypassSelf' | 'bypassSelfDescendants' |
'checkSelf' | 'checkSelfBypassDescendants'--><!--Device-unnamed-export type FocusRule = 'bypassSelf' | 'bypassSelfDescendants' |
'checkSelf' | 'checkSelfBypassDescendants'-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| 'bypassSelf' | 表示跳过对起始节点的检查，只检查其子节点。值固定为'bypassSelf'字符串。 |
| 'bypassSelfDescendants' | 表示跳过对起始节点及其所有子节点的检查。值固定为'bypassSelfDescendants'字符串。 |
| 'checkSelf' | 表示先检查起始节点是否可以聚焦，如果可以则直接使用；如果不能聚焦，则继续检查其子节点。值固定为'checkSelf'字符串。 |
| 'checkSelfBypassDescendants' | 表示先检查起始节点是否可以聚焦，如果可以则使用；如果不能聚焦，则跳过所有子节点的检查。值固定为' checkSelfBypassDescendants'字符串。 |

