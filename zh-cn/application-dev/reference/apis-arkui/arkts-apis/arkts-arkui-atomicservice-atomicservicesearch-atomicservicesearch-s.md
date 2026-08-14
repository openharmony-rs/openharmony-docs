# AtomicServiceSearch

AtomicServiceSearch为开发者提供满足定制化需求的功能，内容包括默认显示的搜索区、可自定义的选择区和功能区（最多两个）。 > **说明：** > > 该组件从API version 18开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-export declare struct AtomicServiceSearch--><!--Device-unnamed-export declare struct AtomicServiceSearch-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: SearchController
```

Search组件控制器，用于设置输入光标的位置、退出编辑态等操作。默认值为undefined。

**类型：** SearchController

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceSearch-controller?: SearchController--><!--Device-AtomicServiceSearch-controller?: SearchController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## operation

```TypeScript
operation?: OperationParams
```

功能区（右侧）的功能设置项。默认值为undefined。

**类型：** [OperationParams](arkts-arkui-atomicservice-atomicservicesearch-operationparams-i.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceSearch-operation?: OperationParams--><!--Device-AtomicServiceSearch-operation?: OperationParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
@Prop
  placeholder?: ResourceStr
```

搜索框内默认显示的提示文本。默认值为Search。

**类型：** ResourceStr

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceSearch-@Prop  placeholder?: ResourceStr--><!--Device-AtomicServiceSearch-@Prop  placeholder?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## search

```TypeScript
@Prop
  search?: SearchParams
```

search搜索区可支持的事件及样式。默认值为undefined。

**类型：** [SearchParams](arkts-arkui-atomicservice-atomicservicesearch-searchparams-i.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceSearch-@Prop  search?: SearchParams--><!--Device-AtomicServiceSearch-@Prop  search?: SearchParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## select

```TypeScript
@Prop
  select?: SelectParams
```

select选择区的内容、事件及样式。默认值为undefined。

**类型：** [SelectParams](arkts-arkui-atomicservice-atomicservicesearch-selectparams-i.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceSearch-@Prop  select?: SelectParams--><!--Device-AtomicServiceSearch-@Prop  select?: SelectParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
@Prop
  value?: ResourceStr
```

设置当前显示的搜索文本内容。默认值为空字符串。

**类型：** ResourceStr

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceSearch-@Prop  value?: ResourceStr--><!--Device-AtomicServiceSearch-@Prop  value?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

