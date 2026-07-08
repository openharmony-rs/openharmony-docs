# RawFileDescriptor

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @liule_123-->
<!--Designer: @buda_wy-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

本模块提供rawfile文件所在HAP包的文件描述符信息，包括文件描述符、rawfile文件的起始偏移和文件长度。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import { resourceManager } from '@kit.LocalizationKit'
```

## RawFileDescriptor

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

| 名称     | 类型    | 只读   | 可选  | 说明           |
| ------ | ------  | ---- | ---- | ------------------ |
| fd     | ArkTS-Dyn: number<br>ArkTS-Sta: int  | 否    | 否 | 文件描述符。 |
| offset | ArkTS-Dyn: number<br>ArkTS-Sta: long  | 否    | 否 | 起始偏移量，表示rawfile文件在HAP包中的起始位置。单位为Byte。  |
| length | ArkTS-Dyn: number<br>ArkTS-Sta: long  | 否    | 否 | 文件长度，表示rawfile文件的大小。单位为Byte。       |