# OnAlphabetIndexerRequestPopupDataCallback

```TypeScript
declare type OnAlphabetIndexerRequestPopupDataCallback  = (index: number) => Array<string>
```

[usingPopup]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_设置值为true，索引项被选中时触发的事件。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnAlphabetIndexerRequestPopupDataCallback  = (index: number) => Array<string>--><!--Device-unnamed-declare type OnAlphabetIndexerRequestPopupDataCallback  = (index: number) => Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | selected index  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | string array corresponding to the index |

