# AlphabetIndexerOptions

用于设置索引条参数。 > **说明：** > > 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface AlphabetIndexerOptions--><!--Device-unnamed-export interface AlphabetIndexerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrayValue

```TypeScript
arrayValue: Array<string>
```

字符串数组，每个字符串代表一个索引项。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AlphabetIndexerOptions-arrayValue: Array<string>--><!--Device-AlphabetIndexerOptions-arrayValue: Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected: int | Bindable<int>
```

初始选中项索引值，若超出索引值范围，则取默认值0。与selected属性同时设置时，selected属性的优先级较高。 取值范围：[0, arrayValue.length-1] 该属性支持[\$\$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

**类型：** int \| [Bindable](arkts-na-common-bindable-i.md)&lt;int&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AlphabetIndexerOptions-selected: int | Bindable<int>--><!--Device-AlphabetIndexerOptions-selected: int | Bindable<int>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

