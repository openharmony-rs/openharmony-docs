# AtomicServiceSearch

AtomicServiceSearch为开发者提供满足定制化需求的功能，内容包括默认显示的搜索区、可自定义的选择区和功能区（最多两个）。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Component

<!--Device-unnamed-export declare struct AtomicServiceSearch--><!--Device-unnamed-export declare struct AtomicServiceSearch-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: SearchController
```

Set the Search component controller.

**类型：** SearchController

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceSearch-controller?: SearchController--><!--Device-AtomicServiceSearch-controller?: SearchController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## operation

```TypeScript
operation?: OperationParams
```

Function settings in the selection area (right).

**类型：** OperationParams

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceSearch-operation?: OperationParams--><!--Device-AtomicServiceSearch-operation?: OperationParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ResourceStr
```

Indicates default prompt text displayed in the search box. The default value is Search, which supports globalization.

**类型：** ResourceStr

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceSearch-placeholder?: ResourceStr--><!--Device-AtomicServiceSearch-placeholder?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## search

```TypeScript
search?: SearchParams
```

Events and styles supported by the search area.

**类型：** SearchParams

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceSearch-search?: SearchParams--><!--Device-AtomicServiceSearch-search?: SearchParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## select

```TypeScript
select?: SelectParams
```

Contents, events, and styles of the select area.

**类型：** SelectParams

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceSearch-select?: SelectParams--><!--Device-AtomicServiceSearch-select?: SelectParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: ResourceStr
```

Sets the search text content that is currently displayed.

**类型：** ResourceStr

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**装饰器类型：** @Prop

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceSearch-value?: ResourceStr--><!--Device-AtomicServiceSearch-value?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

