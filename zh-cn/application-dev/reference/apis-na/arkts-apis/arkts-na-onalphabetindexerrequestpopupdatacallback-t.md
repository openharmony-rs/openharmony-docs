# OnAlphabetIndexerRequestPopupDataCallback

```TypeScript
export type OnAlphabetIndexerRequestPopupDataCallback = (index: int) => Array<string>
```

usingPopup设置值为true，索引项被选中时触发的事件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnAlphabetIndexerRequestPopupDataCallback = (index: int) => Array<string>--><!--Device-unnamed-export type OnAlphabetIndexerRequestPopupDataCallback = (index: int) => Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | selected index |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | string array corresponding to the index |

