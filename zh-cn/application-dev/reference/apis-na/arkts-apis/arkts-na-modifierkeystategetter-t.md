# ModifierKeyStateGetter

```TypeScript
export type ModifierKeyStateGetter = (keys: Array<string>) => boolean
```

The modifier key state query function block.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type ModifierKeyStateGetter = (keys: Array<string>) => boolean--><!--Device-unnamed-export type ModifierKeyStateGetter = (keys: Array<string>) => boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keys | Array&lt;string&gt; | 是 | Indicate the modifier keys to query. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | the query result |

