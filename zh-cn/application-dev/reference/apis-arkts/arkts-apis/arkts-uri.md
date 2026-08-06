# @ohos.uri

本模块提供URI字符串解析功能，支持URI各组成部分（协议、主机、端口、路径、查询参数和片段等）的提取与设置，以及URI编码/解码、比较判断、路径规范化和查询参数操作等能力。 适用于网络请求URL处理、深链接解析或数据共享URI处理等场景。 URI遵循RFC3986规范标准，不支持非标准场景解析。 > **说明：** > > - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare namespace uri--><!--Device-unnamed-declare namespace uri-End-->

**系统能力：** SystemCapability.Utils.Lang

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [URI](arkts-arkts-uri-uri-c.md) | 构造一个URI对象，并提供URI比较、路径规范化、查询参数操作、路径段追加和URI类型判断等方法。 |

