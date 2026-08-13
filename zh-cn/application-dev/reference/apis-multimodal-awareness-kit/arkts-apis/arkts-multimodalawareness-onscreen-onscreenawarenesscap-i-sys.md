# OnscreenAwarenessCap（系统接口）

屏上感知能力（包括但不限于阅读场景感知、OCR识别等功能）。 参数约束说明： 用户可通过能力项（capList）或分组 ID（groupId）使用屏上感知功能。 * 逻辑关系：capList 与 groupId 互为补充必填项, 至少需提供其一，且不为空。 * 校验规则：调用接口时，系统会单独检测capList和groupId。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-onScreen-export interface OnscreenAwarenessCap--><!--Device-onScreen-export interface OnscreenAwarenessCap-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## capList

```TypeScript
capList?: string[]
```

表示能力集合，包含页面内容、页面链接、文本选择等能力。具体能力项见下表。

**类型：** string[]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessCap-capList?: string[]--><!--Device-OnscreenAwarenessCap-capList?: string[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## groupId

```TypeScript
groupId?: string
```

业务分组ID。具体分组ID见下表。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessCap-groupId?: string--><!--Device-OnscreenAwarenessCap-groupId?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

