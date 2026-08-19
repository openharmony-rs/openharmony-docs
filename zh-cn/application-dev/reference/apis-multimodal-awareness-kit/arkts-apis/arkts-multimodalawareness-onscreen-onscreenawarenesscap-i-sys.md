# OnscreenAwarenessCap（系统接口）

屏上感知能力（包括但不限于阅读场景感知、OCR识别等功能）。 参数约束说明： 用户可通过能力项（capList）或分组 ID（groupId）使用屏上感知功能。 * 逻辑关系：capList 与 groupId 互为补充必填项，至少需提供其一，且不为空。 * 校验规则：调用接口时，系统会单独检测capList和groupId。 * 能力列表：按能力项或分组ID使用屏上感知功能，具体定义如下。 * capList支持能力列表 按具体业务场景预设的能力，可进行单一订阅或者触发，如下： |capList支持能力列表|功能说明| | ---- | ------ | |Article|获取阅读场景的感知信息。| |ShortVideo|获取短视频场景的感知信息。| |Todo|获取待办场景的感知信息。| |Activity|获取基础服务的感知信息。| |UiImage|获取页面内子图信息。| |JumpContext|高亮跳转到指定上下文。| |QuickSnap|获取单次截屏信息。使用规格：仅在capture接口使用，capList仅传递"QuickSnap"时生效，其他使用接口均返回401错误码。| |UiTree|获取页面内JSON树信息。起始版本：26.0.0| |InjectEvent|注入事件。起始版本：26.0.0| |CollectStrategy|获取屏幕采集策略。起始版本：26.0.0| * groupId支持能力列表<br> 按业务场景预设的一组能力集合。可统一订阅业务场景，如下： |groupId支持能力列表|对应子项能力|功能说明| | ---- | ------ | ------| |SmartEdge|Article|获取阅读场景的感知信息。| |SmartEdge|ShortVideo|获取短视频场景的感知信息。| |SmartEdge|Todo|获取待办场景的感知信息。| |SmartEdge|Activity|获取基础服务的感知信息。| |CeliaMemory|Article|获取阅读场景的感知信息。|

**起始版本：** 23

<!--Device-onScreen-export interface OnscreenAwarenessCap--><!--Device-onScreen-export interface OnscreenAwarenessCap-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## capList

```TypeScript
capList?: string[]
```

表示能力集合，包含页面内容、页面链接、文本选择等能力。具体能力项见下表。

**类型：** string[]

**起始版本：** 23

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

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OnscreenAwarenessCap-groupId?: string--><!--Device-OnscreenAwarenessCap-groupId?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

