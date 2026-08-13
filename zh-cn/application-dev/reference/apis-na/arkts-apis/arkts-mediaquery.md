# @ohos.mediaquery

提供根据不同媒体类型定义不同的样式。 > **说明：** > > - 以下API需先使用UIContext中的[getMediaQuery()](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getmediaquery)方法 > 获取到MediaQuery对象，再通过该对象调用对应方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace mediaquery--><!--Device-unnamed-declare namespace mediaquery-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [MediaQueryListener](arkts-na-mediaquery-mediaquerylistener-i.md) | 媒体查询的句柄，并包含了申请句柄时的首次查询结果。媒体查询根据设置的条件语句， 比如'(width <= 600vp)'，比较系统信息，若首次查询时相关信息未初始化，matches返回false。 继承自[MediaQueryResult](arkts-na-mediaquery-mediaqueryresult-i.md#MediaQueryResult)。 |
| [MediaQueryResult](arkts-na-mediaquery-mediaqueryresult-i.md) | 用于执行媒体查询操作。 |

