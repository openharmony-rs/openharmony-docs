# @ohos.multimodalAwareness.onScreen

本模块提供对屏上内容的感知能力，支持获取页面内容、链接、截屏等信息，识别阅读场景、短视频场景等应用场景，提供文章标题、正文等实体信息，以及点击、滚动等交互信息。 > **说明：** > > 1. 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > 2. 本模块为系统接口。

**起始版本：** 23

<!--Device-unnamed-declare namespace onScreen--><!--Device-unnamed-declare namespace onScreen-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

## 导入模块

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [apperceive](arkts-multimodalawareness-onscreen-apperceive-f-sys.md) | 主动触发屏幕内容感知，获取屏幕内容进行快照分析。 |
| [capture](arkts-multimodalawareness-onscreen-capture-f-sys.md) | 主动触发屏幕内容感知，获取页面信息。 |
| [getPageContent](arkts-multimodalawareness-onscreen-getpagecontent-f-sys.md) | 在需要抓取内容的窗口在桌面上时，调用该接口以获取屏上内容。 |
| [interact](arkts-multimodalawareness-onscreen-interact-f-sys.md) | 主动触发屏幕行为交互，实现对界面行为的识别与行为反馈。例如：当capList能力列表为JumpContext时，点击后通过反馈信息精准跳转至指定段落并实现文字高亮。 <br>当capList能力列表为InjectEvent时，点击后执行相应的点击事件。 |
| [offReadingScreenPermissionListener](arkts-multimodalawareness-onscreen-offreadingscreenpermissionlistener-f-sys.md) | 关闭屏幕内容访问权限监测。 |
| [onReadingScreenPermissionListener](arkts-multimodalawareness-onscreen-onreadingscreenpermissionlistener-f-sys.md) | 开启屏幕内容访问权限监测，实时返回授权状态。 |
| [sendControlEvent](arkts-multimodalawareness-onscreen-sendcontrolevent-f-sys.md) | 在需要控制的窗口在桌面上时，在调用[onScreen.getPageContent](arkts-multimodalawareness-onscreen-getpagecontent-f-sys.md)后，根据其返回的段落信息，调用该接口发送屏上控制事件。 |
| [subscribe](arkts-multimodalawareness-onscreen-subscribe-f-sys.md) | 开启屏幕内容主动感知，并订阅屏幕感知结果。 |
| [trigger](arkts-multimodalawareness-onscreen-trigger-f-sys.md) | 主动触发屏幕内容感知，获取当前屏幕感知结果。 |
| [unsubscribe](arkts-multimodalawareness-onscreen-unsubscribe-f-sys.md) | 关闭屏幕内容主动感知，并取消订阅屏幕感知结果。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AwarenessItem](arkts-multimodalawareness-onscreen-awarenessitem-i-sys.md) | 提供页面信息。包括： * 页面基础信息，如页面内容、链接、截屏。 * 页面实体信息，如页面文章的标题、正文信息。 * 页面交互信息，如点击、滚动信息。 |
| [ContentOptions](arkts-multimodalawareness-onscreen-contentoptions-i-sys.md) | 屏上内容的获取选项。 |
| [ControlEvent](arkts-multimodalawareness-onscreen-controlevent-i-sys.md) | 控制事件。 |
| [EntityInfo](arkts-multimodalawareness-onscreen-entityinfo-i-sys.md) | 提供感知到的实体信息，包括内容、链接、图像和其他类型的实体。 |
| [OnscreenAwarenessCap](arkts-multimodalawareness-onscreen-onscreenawarenesscap-i-sys.md) | 屏上感知能力（包括但不限于阅读场景感知、OCR识别等功能）。 参数约束说明： 用户可通过能力项（capList）或分组 ID（groupId）使用屏上感知功能。 * 逻辑关系：capList 与 groupId 互为补充必填项，至少需提供其一，且不为空。 * 校验规则：调用接口时，系统会单独检测capList和groupId。 * 能力列表：按能力项或分组ID使用屏上感知功能，具体定义如下。 * capList支持能力列表 按具体业务场景预设的能力，可进行单一订阅或者触发，如下： \|capList支持能力列表\|功能说明\| \| ---- \| ------ \| \|Article\|获取阅读场景的感知信息。\| \|ShortVideo\|获取短视频场景的感知信息。\| \|Todo\|获取待办场景的感知信息。\| \|Activity\|获取基础服务的感知信息。\| \|UiImage\|获取页面内子图信息。\| \|JumpContext\|高亮跳转到指定上下文。\| \|QuickSnap\|获取单次截屏信息。使用规格：仅在capture接口使用，capList仅传递"QuickSnap"时生效，其他使用接口均返回401错误码。\| \|UiTree\|获取页面内JSON树信息。起始版本：26.0.0\| \|InjectEvent\|注入事件。起始版本：26.0.0\| \|CollectStrategy\|获取屏幕采集策略。起始版本：26.0.0\| * groupId支持能力列表<br> 按业务场景预设的一组能力集合。可统一订阅业务场景，如下： \|groupId支持能力列表\|对应子项能力\|功能说明\| \| ---- \| ------ \| ------\| \|SmartEdge\|Article\|获取阅读场景的感知信息。\| \|SmartEdge\|ShortVideo\|获取短视频场景的感知信息。\| \|SmartEdge\|Todo\|获取待办场景的感知信息。\| \|SmartEdge\|Activity\|获取基础服务的感知信息。\| \|CeliaMemory\|Article\|获取阅读场景的感知信息。\| |
| [OnscreenAwarenessInfo](arkts-multimodalawareness-onscreen-onscreenawarenessinfo-i-sys.md) | 屏上感知返回信息列表。 |
| [OnscreenAwarenessOptions](arkts-multimodalawareness-onscreen-onscreenawarenessoptions-i-sys.md) | 屏上感知参数列表，用于特定场景下获取屏上信息，如提供窗口ID用以采集应用界面内容和链接。 |
| [PageContent](arkts-multimodalawareness-onscreen-pagecontent-i-sys.md) | 屏上内容。 |
| [Paragraph](arkts-multimodalawareness-onscreen-paragraph-i-sys.md) | 段落信息。 |
| [ReadingScreenPermissionStatus](arkts-multimodalawareness-onscreen-readingscreenpermissionstatus-i-sys.md) | 读取屏幕信息的授权状态。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CollectStrategy](arkts-multimodalawareness-onscreen-collectstrategy-e-sys.md) | 页面信息收集策略。 |
| [EventType](arkts-multimodalawareness-onscreen-eventtype-e-sys.md) | 定义控制事件的类型。 |
| [Scenario](arkts-multimodalawareness-onscreen-scenario-e-sys.md) | 定义屏上内容的场景类型。 |
<!--DelEnd-->

