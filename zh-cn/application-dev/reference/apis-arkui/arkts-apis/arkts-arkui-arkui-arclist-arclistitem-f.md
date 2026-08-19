# ArcListItem

## 导入模块

```TypeScript
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';
```

## ArcListItem

```TypeScript
@ComponentBuilder
export declare function ArcListItem(
    content_?: CustomBuilder,
): ArcListItemAttribute
```

创建弧形列表子组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-@ComponentBuilderexport declare function ArcListItem(    content_?: CustomBuilder,): ArcListItemAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function ArcListItem(    content_?: CustomBuilder,): ArcListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcListItemAttribute |  |


## ArcListItem

```TypeScript
@Builder
export declare function ArcListItem(
    style_: CustomBuilderT<ArcListItemAttribute>,
    content_?: CustomBuilder
): ArcListItemAttribute
```

定义ArcListItem组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function ArcListItem(    style_: CustomBuilderT<ArcListItemAttribute>,    content_?: CustomBuilder): ArcListItemAttribute--><!--Device-unnamed-@Builderexport declare function ArcListItem(    style_: CustomBuilderT<ArcListItemAttribute>,    content_?: CustomBuilder): ArcListItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;ArcListItemAttribute&gt; | 是 | 创建ArcListItem的样式 |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcListItemAttribute | ArcListItem的属性。 |

