# OperateCheckV2

列表右侧元素为Switch、CheckBox、Radio的类型。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export declare class OperateCheckV2--><!--Device-unnamed-export declare class OperateCheckV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: OperateCheckV2Options)
```

OperateCheckV2的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OperateCheckV2-constructor(options?: OperateCheckV2Options)--><!--Device-OperateCheckV2-constructor(options?: OperateCheckV2Options)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | OperateCheckV2的可选项 |

## accessibilityDescription

```TypeScript
public accessibilityDescription?: ResourceStr
```

Switch/CheckBox/Radio的无障碍描述。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OperateCheckV2-public accessibilityDescription?: ResourceStr--><!--Device-OperateCheckV2-public accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
public accessibilityLevel?: string
```

Switch/CheckBox/Radio的无障碍重要性。

**类型：** string

**默认值：** auto

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OperateCheckV2-public accessibilityLevel?: string--><!--Device-OperateCheckV2-public accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
public accessibilityText?: ResourceStr
```

Switch/CheckBox/Radio的无障碍文本属性。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OperateCheckV2-public accessibilityText?: ResourceStr--><!--Device-OperateCheckV2-public accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isCheck

```TypeScript
public isCheck?: boolean
```

是否默认选中。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OperateCheckV2-public isCheck?: boolean--><!--Device-OperateCheckV2-public isCheck?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
public onChange?: OnChangeCallback
```

操作checkbox/switch/radio时的回调函数。

**类型：** OnChangeCallback

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OperateCheckV2-public onChange?: OnChangeCallback--><!--Device-OperateCheckV2-public onChange?: OnChangeCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

