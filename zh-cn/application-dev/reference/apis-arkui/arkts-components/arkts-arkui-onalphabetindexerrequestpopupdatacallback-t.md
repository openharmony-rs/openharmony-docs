# OnAlphabetIndexerRequestPopupDataCallback

```TypeScript
declare type OnAlphabetIndexerRequestPopupDataCallback  = (index: number) => Array<string>
```

[usingPopup](AlphabetIndexerAttribute#usingPopup)设置值为true，索引项被选中时触发的事件。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | selected index |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | string array corresponding to the index |

