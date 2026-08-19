# ToggleConfiguration

开发者需要自定义class实现ContentModifier接口。继承自CommonConfiguration。

**继承/实现关系：** ToggleConfiguration extends CommonConfiguration<ToggleConfiguration>

**起始版本：** 12

<!--Device-unnamed-declare interface ToggleConfiguration--><!--Device-unnamed-declare interface ToggleConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## enabled

```TypeScript
enabled: boolean
```

是否可以切换状态。 true：可以切换状态；false：不可以切换状态。 默认值：true

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ToggleConfiguration-enabled: boolean--><!--Device-ToggleConfiguration-enabled: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isOn

```TypeScript
isOn: boolean
```

开关是否打开。 true：开关打开；false：开关关闭。 默认值：false

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ToggleConfiguration-isOn: boolean--><!--Device-ToggleConfiguration-isOn: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<boolean>
```

用于触发Toggle开关状态变化的回调函数，通常在自定义ContentModifier中通过编程方式改变开关状态。调用此回调并传入true可将开关状态设置为打开，传入false可将开关状态设置为关闭。

**类型：** Callback&lt;boolean&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ToggleConfiguration-triggerChange: Callback<boolean>--><!--Device-ToggleConfiguration-triggerChange: Callback<boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

