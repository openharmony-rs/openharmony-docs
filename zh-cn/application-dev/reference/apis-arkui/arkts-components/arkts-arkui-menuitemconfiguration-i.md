# MenuItemConfiguration

开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。

**继承/实现关系：** MenuItemConfiguration extends [CommonConfiguration<MenuItemConfiguration>](CommonConfiguration<MenuItemConfiguration>)

**起始版本：** 12

<!--Device-unnamed-declare interface MenuItemConfiguration extends CommonConfiguration<MenuItemConfiguration>--><!--Device-unnamed-declare interface MenuItemConfiguration extends CommonConfiguration<MenuItemConfiguration>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="triggerselect"></a>
## triggerSelect

```TypeScript
triggerSelect(index: number, value: string): void
```

下拉菜单选中某一项的回调函数。

<br/>**说明：**

<br/>index会赋值给事件[onSelect](SelectAttribute#onSelect(callback: (index: number, value: string) => void))回调中的索引参数； value会返回给Select组件显示，同时会赋值给事件[onSelect](SelectAttribute#onSelect(callback: (index: number, value: string) => void))回调中的文本参数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MenuItemConfiguration-triggerSelect(index: number, value: string): void--><!--Device-MenuItemConfiguration-triggerSelect(index: number, value: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 选中菜单项的索引。 |
| value | string | 是 | 选中菜单项的文本。 |

## icon

```TypeScript
icon?: ResourceStr
```

下拉菜单项的图片内容。

**说明：**

string格式可用于加载网络图片和本地图片。

**类型：** ResourceStr

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MenuItemConfiguration-icon?: ResourceStr--><!--Device-MenuItemConfiguration-icon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

下拉菜单项的索引，索引值从0开始。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MenuItemConfiguration-index: number--><!--Device-MenuItemConfiguration-index: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected: boolean
```

下拉菜单项是否被选中。值为true表示选中，值为false表示未选中。

默认值：false

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MenuItemConfiguration-selected: boolean--><!--Device-MenuItemConfiguration-selected: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolIcon

```TypeScript
symbolIcon?: SymbolGlyphModifier
```

下拉选项Symbol图片。

symbolIcon优先级高于icon。

**类型：** SymbolGlyphModifier

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MenuItemConfiguration-symbolIcon?: SymbolGlyphModifier--><!--Device-MenuItemConfiguration-symbolIcon?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

下拉菜单项的文本内容。

**说明：**

当文本字符的长度超过菜单项文本区域的宽度时，文本将会被截断。

**类型：** ResourceStr

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MenuItemConfiguration-value: ResourceStr--><!--Device-MenuItemConfiguration-value: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

