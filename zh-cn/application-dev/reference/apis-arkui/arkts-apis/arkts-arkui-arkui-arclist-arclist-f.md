# ArcList

## 导入模块

```TypeScript
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';
```

## ArcList

```TypeScript
@ComponentBuilder
export declare function ArcList(
    options?: ArkListOptions, 
    content_?: CustomBuilder,
): ArcListAttribute
```

创建弧形列表实例，传入弧形列表配置项参数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-@ComponentBuilderexport declare function ArcList(    options?: ArkListOptions,     content_?: CustomBuilder,): ArcListAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function ArcList(    options?: ArkListOptions,     content_?: CustomBuilder,): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ArkListOptions](arkts-arkui-arkui-arclist-arklistoptions-i.md) | 否 |  |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) |  |


## ArcList

```TypeScript
@Builder
export declare function ArcList(
    style_: CustomBuilderT<ArcListAttribute>,
    content_?: CustomBuilder
): ArcListAttribute
```

定义ArcList组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function ArcList(    style_: CustomBuilderT<ArcListAttribute>,    content_?: CustomBuilder): ArcListAttribute--><!--Device-unnamed-@Builderexport declare function ArcList(    style_: CustomBuilderT<ArcListAttribute>,    content_?: CustomBuilder): ArcListAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;[ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md)&gt; | 是 | The style to create an ArcList. |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcListAttribute](arkts-arkui-arkui-arclist-arclistattribute-c.md) | ArcList的属性。 |

