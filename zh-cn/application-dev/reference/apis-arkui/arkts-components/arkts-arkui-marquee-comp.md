# Marquee

跑马灯组件，用于滚动展示一段单行文本，支持自定义滚动速度、方向、循环次数等。仅当文本内容宽度大于等于跑马灯组件宽度时滚动，否则不滚动。适用于需要在有限空间内展示较长文本的场景，如新闻标题滚动、通知公告、广告轮播等，可以有效节省界面空间并吸引用户注意。

> **说明：** > > 为了不影响滚动帧率，建议在滚动类组件中Marquee的个数不超过4个，或者使用 > > 对于Marquee组件动态帧率的场景，可以使用[MarqueeDynamicSyncScene](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md)接口实现。 > > 在文本宽度小于跑马灯组件宽度时，使用属性动画实现滚动。

## 子组件

无

## Marquee

```TypeScript
Marquee(options: MarqueeOptions)
```

创建跑马灯组件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [MarqueeOptions](arkts-arkui-marqueeoptions-i.md) | 是 | 配置跑马灯组件的参数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [MarqueeOptions](arkts-arkui-marqueeoptions-i.md) | Marquee初始化参数。 |

## 示例

```TypeScript
### 示例1（跑马灯内容动态更新）

该示例展示了跑马灯内容动态更新时的运行效果，主要涉及start、step、loop、fromStart、src等属性以及[marqueeUpdateStrategy](#marqueeupdatestrategy12)属性的设置。

从API version 23开始，[MarqueeOptions](#marqueeoptions18对象说明)新增spacing、delay属性。


```

```TypeScript
### 示例2（设置跑马灯停止回调）

该示例通过变更跑马灯状态来触发onStop回调，回调触发后使停止计数器numberStop的值加1。

从API版本26.0.0开始，新增[onStop](#onstop)接口。
```
