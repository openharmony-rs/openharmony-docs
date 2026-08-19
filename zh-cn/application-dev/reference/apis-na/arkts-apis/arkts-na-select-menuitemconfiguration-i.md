# MenuItemConfiguration

菜单项配置接口，用于ContentModifier中。

**继承/实现关系：** MenuItemConfiguration extends CommonConfiguration<MenuItemConfiguration>

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface MenuItemConfiguration--><!--Device-unnamed-export declare interface MenuItemConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## triggerSelect

```TypeScript
triggerSelect(index: int, value: string): void
```

下拉菜单选中某一项的回调函数。 <br/>index：选中菜单项的索引。 <br/>value：选中菜单项的文本。 <br/>**说明：** <br/>index会赋值给事件[onSelect](arkts-na-onselectcallback-t.md)回调中的索引参数； value会返回给Select组件显示，同时会赋值给事件[onSelect](arkts-na-onselectcallback-t.md)回调中的文本参数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuItemConfiguration-triggerSelect(index: int, value: string): void--><!--Device-MenuItemConfiguration-triggerSelect(index: int, value: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 菜单项的索引。 |
| value | string | 是 | 菜单项的文本内容。 |

## icon

```TypeScript
icon?: ResourceStr
```

菜单项的图标。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuItemConfiguration-icon?: ResourceStr--><!--Device-MenuItemConfiguration-icon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: int
```

菜单项的索引。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuItemConfiguration-index: int--><!--Device-MenuItemConfiguration-index: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected: boolean
```

菜单项是否被选中。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuItemConfiguration-selected: boolean--><!--Device-MenuItemConfiguration-selected: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolIcon

```TypeScript
symbolIcon?: SymbolGlyphModifier
```

下拉选项Symbol图片。 symbolIcon优先级高于icon。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** SymbolGlyphModifier

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuItemConfiguration-symbolIcon?: SymbolGlyphModifier--><!--Device-MenuItemConfiguration-symbolIcon?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

菜单项的文本内容。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuItemConfiguration-value: ResourceStr--><!--Device-MenuItemConfiguration-value: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

