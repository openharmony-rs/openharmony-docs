# TextMenuShowMode

菜单的显示模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum TextMenuShowMode--><!--Device-unnamed-export declare enum TextMenuShowMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

显示在当前窗口中。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextMenuShowMode-DEFAULT = 0--><!--Device-TextMenuShowMode-DEFAULT = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PREFER_WINDOW

```TypeScript
PREFER_WINDOW = 1
```

优先显示在独立窗口中，若不支持独立窗口，则显示在当前窗口中。 **说明：** 除应用主窗口、应用子窗口、系统模态窗口及系统桌面类型的窗口外，其他类型的窗口不支持将文本选择菜单显示在独立窗口中。 在预览器中不支持将文本选择菜单显示在独立窗口中。 在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中不支持将文本选择菜单显示在独立窗口中。 当文本类组件已经显示在子窗类型的\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_4\_\_\_中时，不支持将其对应的文本选择菜单显示在独立窗口中。 当TextInput、TextArea可支持拉起AutoFill时，不支持将其对应的文本选择菜单显示在独立窗口中。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextMenuShowMode-PREFER_WINDOW = 1--><!--Device-TextMenuShowMode-PREFER_WINDOW = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

