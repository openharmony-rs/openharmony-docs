# DisplayComposerType.idl

## 概述

显示合成类型定义，定义显示图层合成操作相关接口所使用的数据类型。

模块包路径：ohos.hdi.display.composer.v1_3

引用：

- ohos.hdi.display.composer.v1_0.DisplayComposerType

- ohos.hdi.display.composer.v1_1.DisplayComposerType

- ohos.hdi.display.composer.v1_2.DisplayComposerType

**起始版本：**  6.0

**相关模块：**  [Display](_composer_display_v13.md)

## 汇总

### 枚举

| 名称 | 描述 |
| -------- | -------- |
| [TunnelLayerProperty](_composer_display_v13.md#tunnellayerproperty) {<br/>[TUNNEL_PROP_INVALID](_composer_display_v13.md) = 0, [TUNNEL_PROP_POSTION](_composer_display_v13.md) = (1 &lt;&lt; 0), [TUNNEL_PROP_BUFFER_ADDR](_composer_display_v13.md) = (1 &lt;&lt; 1), [TUNNEL_PROP_CLIENT_COMMIT](_composer_display_v13.md) = (1 &lt;&lt; 2),<br/>[TUNNEL_PROP_DEVICE_COMMIT](_composer_display_v13.md) = (1 &lt;&lt; 3), [TUNNEL_PROP_SECURE_DEVICE_COMMIT](_composer_display_v13.md) = (1 &lt;&lt; 4)<br/>} | 隧道层的属性ID枚举。 |
| [LayerType](_composer_display_v13.md#layertype) : ohos.hdi.display.composer.v1_0.LayerType { [LAYER_TYPE_TUNNEL](_composer_display_v13.md) } | 隧道层类型。 |
