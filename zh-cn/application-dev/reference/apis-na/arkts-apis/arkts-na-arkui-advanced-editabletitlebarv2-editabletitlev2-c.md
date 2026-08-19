# EditableTitleV2

标题配置类。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare class EditableTitleV2--><!--Device-unnamed-export declare class EditableTitleV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(options?: EditableTitleV2Options)
```

EditableTitleV2的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleV2-constructor(options?: EditableTitleV2Options)--><!--Device-EditableTitleV2-constructor(options?: EditableTitleV2Options)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [EditableTitleV2Options](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlev2options-i.md) | 否 | 标题配置选项。 |

## mainTitle

```TypeScript
@Trace
  public mainTitle: ResourceStr
```

主标题内容。 默认值：''，表示标题内容为空。

**类型：** ResourceStr

**默认值：** ''

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleV2-@Trace  public mainTitle: ResourceStr--><!--Device-EditableTitleV2-@Trace  public mainTitle: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## subTitle

```TypeScript
@Trace
  public subTitle?: ResourceStr
```

副标题内容。需要在标题下方显示补充说明信息时传入此参数。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditableTitleV2-@Trace  public subTitle?: ResourceStr--><!--Device-EditableTitleV2-@Trace  public subTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

