# OperateCheckV2

列表右侧元素为Switch、CheckBox、Radio的类型。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class OperateCheckV2--><!--Device-unnamed-export declare class OperateCheckV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: OperateCheckV2Options)
```

OperateCheckV2的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OperateCheckV2-constructor(options?: OperateCheckV2Options)--><!--Device-OperateCheckV2-constructor(options?: OperateCheckV2Options)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [OperateCheckV2Options](arkts-na-arkui-advanced-composelistitemv2-operatecheckv2options-i.md) | 否 | OperateCheckV2的可选项 |

## accessibilityDescription

```TypeScript
@Trace
  public accessibilityDescription?: ResourceStr
```

Switch/CheckBox/Radio的无障碍描述。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OperateCheckV2-@Trace  public accessibilityDescription?: ResourceStr--><!--Device-OperateCheckV2-@Trace  public accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
@Trace
  public accessibilityLevel?: string
```

Switch/CheckBox/Radio的无障碍重要性。

**类型：** string

**默认值：** auto

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OperateCheckV2-@Trace  public accessibilityLevel?: string--><!--Device-OperateCheckV2-@Trace  public accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
@Trace
  public accessibilityText?: ResourceStr
```

Switch/CheckBox/Radio的无障碍文本属性。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OperateCheckV2-@Trace  public accessibilityText?: ResourceStr--><!--Device-OperateCheckV2-@Trace  public accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isCheck

```TypeScript
@Trace
  public isCheck?: boolean
```

是否默认选中。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OperateCheckV2-@Trace  public isCheck?: boolean--><!--Device-OperateCheckV2-@Trace  public isCheck?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
@Trace
  public onChange?: OnChangeCallback
```

操作checkbox/switch/radio时的回调函数。

**类型：** [OnChangeCallback](arkts-na-onchangecallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OperateCheckV2-@Trace  public onChange?: OnChangeCallback--><!--Device-OperateCheckV2-@Trace  public onChange?: OnChangeCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

