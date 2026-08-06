# EditableLeftIconV2

左侧图标配置类，使用@ObservedV2装饰器，支持状态观察。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export declare class EditableLeftIconV2--><!--Device-unnamed-export declare class EditableLeftIconV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: EditableLeftIconV2Options)
```

EditableLeftIconV2的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableLeftIconV2-constructor(options?: EditableLeftIconV2Options)--><!--Device-EditableLeftIconV2-constructor(options?: EditableLeftIconV2Options)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 左侧图标配置选项。 |

## defaultFocus

```TypeScript
public defaultFocus: boolean
```

是否默认获取焦点。 true：获焦。 false：不获焦。 默认值：false。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableLeftIconV2-public defaultFocus: boolean--><!--Device-EditableLeftIconV2-public defaultFocus: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iconType

```TypeScript
public iconType: EditableLeftIconTypeV2
```

图标类型。 默认值：EditableLeftIconTypeV2.Back。

**类型：** EditableLeftIconTypeV2

**默认值：** EditableLeftIconTypeV2.Back

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableLeftIconV2-public iconType: EditableLeftIconTypeV2--><!--Device-EditableLeftIconV2-public iconType: EditableLeftIconTypeV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onAction

```TypeScript
public onAction?: OnActionCallback
```

点击左侧图标的回调函数。未设置时，Back类型默认执行路由返回，Cancel类型无操作。

**类型：** OnActionCallback

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableLeftIconV2-public onAction?: OnActionCallback--><!--Device-EditableLeftIconV2-public onAction?: OnActionCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

