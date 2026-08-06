# MaterialState

材质使能状态枚举，表示应用级沉浸式系统材质配置的状态。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-uiMaterial-export enum MaterialState--><!--Device-uiMaterial-export enum MaterialState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

默认模式。\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_、\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_、 [AlphabetIndexer]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_在组件本身未设置背景颜色、模糊参数和阴影参数时默认开启沉浸式系统材质；[Text]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_设置 [copyOption]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_后长按或双击触发的文本菜单默认开启沉浸式系统材质；其他组件由应用主动设置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MaterialState-DEFAULT = 0--><!--Device-MaterialState-DEFAULT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ENABLE

```TypeScript
ENABLE = 1
```

使能模式。\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_、\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_、 [AlphabetIndexer]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_、[ChipGroup]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_、 [Chip]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_、[Select]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_、[菜单控制]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_、[Toggle]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_、 [SegmentButton]\_\_\_JSDOC\_LINK\_DESC\_USD\_8\_\_\_、 [SegmentButtonV2]\_\_\_JSDOC\_LINK\_DESC\_USD\_9\_\_\_、[Slider]\_\_\_JSDOC\_LINK\_DESC\_USD\_10\_\_\_、 [bindSheet]\_\_\_JSDOC\_LINK\_DESC\_USD\_11\_\_\_、[SelectionMenu]\_\_\_JSDOC\_LINK\_DESC\_USD\_12\_\_\_组件默认开启沉浸式系统材质； [Text]\_\_\_JSDOC\_LINK\_DESC\_USD\_13\_\_\_设置[copyOption]\_\_\_JSDOC\_LINK\_DESC\_USD\_14\_\_\_后长按或双击触发的文本菜单默认开启沉浸式系统材质。此模式下，沉浸式系统材质样式生效的优先级高于组件 本身设置的背景色、模糊、阴影和边框样式。其他组件需开发者主动设置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MaterialState-ENABLE = 1--><!--Device-MaterialState-ENABLE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DISABLE

```TypeScript
DISABLE = 2
```

禁用模式。所有组件禁止开启沉浸式系统材质，即使主动为组件设置沉浸式系统材质参数也不会生效。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MaterialState-DISABLE = 2--><!--Device-MaterialState-DISABLE = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

