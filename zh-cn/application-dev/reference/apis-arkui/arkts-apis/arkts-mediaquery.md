# @ohos.mediaquery

提供根据不同媒体类型定义不同的样式。 > **说明：** > > - 以下API需先使用UIContext中的\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_方法 > 获取到MediaQuery对象，再通过该对象调用对应方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-declare namespace mediaquery--><!--Device-unnamed-declare namespace mediaquery-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [MediaQueryListener](arkts-arkui-mediaquery-mediaquerylistener-i.md) | 媒体查询的句柄，并包含了申请句柄时的首次查询结果。媒体查询根据设置的条件语句， 比如'(width <= 600vp)'，比较系统信息，若首次查询时相关信息未初始化，matches返回false。 继承自[MediaQueryResult]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| [MediaQueryResult](arkts-arkui-mediaquery-mediaqueryresult-i.md) | 用于执行媒体查询操作。 |

