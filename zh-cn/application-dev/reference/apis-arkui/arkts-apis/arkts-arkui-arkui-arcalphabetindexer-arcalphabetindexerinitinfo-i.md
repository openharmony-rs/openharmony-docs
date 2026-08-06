# ArcAlphabetIndexerInitInfo

定义弧形字母索引条的初始化参数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface ArcAlphabetIndexerInitInfo--><!--Device-unnamed-export declare interface ArcAlphabetIndexerInitInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## arrayValue

```TypeScript
arrayValue: string[]
```

字母索引字符串数组，不可设置为空。

**类型：** string[]

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcAlphabetIndexerInitInfo-arrayValue: string[]--><!--Device-ArcAlphabetIndexerInitInfo-arrayValue: string[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## selected

```TypeScript
selected: int | Bindable<int>
```

初始选中项索引值，若超出索引值范围，则取默认值0。 该参数支持\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_双向绑定变量。

**类型：** int \| Bindable&lt;int&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcAlphabetIndexerInitInfo-selected: int | Bindable<int>--><!--Device-ArcAlphabetIndexerInitInfo-selected: int | Bindable<int>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

