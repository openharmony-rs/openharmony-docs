# @ohos.multimodalAwareness.onScreen(屏上感知)

本模块提供对屏上内容的感知能力，支持获取页面内容、链接、截屏等信息，识别阅读场景、短视频场景等应用场景，提供文章标题、正文等实体信息，以及点击、滚动等交互信息。

> **说明：** 
> 
> 1. 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 2. 本模块为系统接口。

**起始版本：** 20

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
| [interact](arkts-multimodalawareness-onscreen-interact-f-sys.md) | 主动触发屏幕行为交互，实现对界面行为的识别与行为反馈。例如：当capList能力列表为JumpContext时，点击后通过反馈信息精准跳转至指定段落并实现文字高亮。<br>当capList能力列表为InjectEvent时，点击后执行相应的点击事件。 |
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
| [AwarenessItem](arkts-multimodalawareness-onscreen-awarenessitem-i-sys.md) | 提供页面信息。包括： |
| [ContentOptions](arkts-multimodalawareness-onscreen-contentoptions-i-sys.md) | 屏上内容的获取选项。 |
| [ControlEvent](arkts-multimodalawareness-onscreen-controlevent-i-sys.md) | 控制事件。 |
| [EntityInfo](arkts-multimodalawareness-onscreen-entityinfo-i-sys.md) | 提供感知到的实体信息，包括内容、链接、图像和其他类型的实体。 |
| [OnscreenAwarenessCap](arkts-multimodalawareness-onscreen-onscreenawarenesscap-i-sys.md) | 屏上感知能力（包括但不限于阅读场景感知、OCR识别等功能）。 |
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
