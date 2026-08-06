# PanelInfo

输入法面板属性信息。用于描述输入法面板的类型和显示状态，在创建输入法面板时作为配置参数传入。 - **含义/功能**：定义输入法面板的类型（软键盘或状态栏）和显示状态（固定态、悬浮态或候选词态），作为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_的配置参数，决定创建的面板形态。 - **使用场景**：当输入法应用需要通过\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_创建输入法面板时使用，用于指定面板的类型和状态。例如：创建默认的固定态软键盘面板、创建可自由拖动的悬浮态软键盘面板、创建独立显示候选词的候选词态面板。 - **使用后效果**：设置的\_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_和\_\_\_INLINE\_CODE\_DESC\_USD\_3\_\_\_将决定创建的面板类型和显示形态。设置完成后，系统将按指定类型和状态创建面板，面板的显隐行为由\_\_\_INLINE\_CODE\_DESC\_USD\_4\_\_\_决定——固定态和悬浮态由系统控制显隐，候选词态由开发者自行控制。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface PanelInfo--><!--Device-unnamed-export interface PanelInfo-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## flag

```TypeScript
flag?: PanelFlag
```

输入法面板状态类型。 - 默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_(0)，表示固定态面板类型。 - 当前仅用于描述软键盘类型的面板的状态。 - 不同状态类型下面板的显隐行为不同：\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_和\_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_由系统控制显隐，\_\_\_INLINE\_CODE\_DESC\_USD\_3\_\_\_由开发者自行控制显隐。

**类型：** PanelFlag

**默认值：** FLG_FIXED

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-PanelInfo-flag?: PanelFlag--><!--Device-PanelInfo-flag?: PanelFlag-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## type

```TypeScript
type: PanelType
```

输入法面板类型。决定面板是软键盘还是状态栏。不填写时默认为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_(0)。

**类型：** PanelType

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-PanelInfo-type: PanelType--><!--Device-PanelInfo-type: PanelType-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

