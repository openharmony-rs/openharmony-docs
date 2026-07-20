# DeviceResponse

定义设备信息获取的参数选项。

**起始版本：** 3

**废弃版本：** 6

<!--Device-unnamed-export interface DeviceResponse--><!--Device-unnamed-export interface DeviceResponse-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## 导入模块

```TypeScript
import { DeviceResponse, GetDeviceOptions } from '@kit.BasicServicesKit';
```

## apiVersion

```TypeScript
apiVersion: number
```

系统API版本号。

**类型：** number

**起始版本：** 4

**废弃版本：** 6

<!--Device-DeviceResponse-apiVersion: number--><!--Device-DeviceResponse-apiVersion: number-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## brand

```TypeScript
brand: string
```

品牌。

**类型：** string

**起始版本：** 3

**废弃版本：** 6

<!--Device-DeviceResponse-brand: string--><!--Device-DeviceResponse-brand: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## deviceType

```TypeScript
deviceType: string
```

设备类型。常见取值：phone（手机）、tablet（平板）、tv（电视）、wearable（可穿戴设备）等。

**类型：** string

**起始版本：** 4

**废弃版本：** 6

<!--Device-DeviceResponse-deviceType: string--><!--Device-DeviceResponse-deviceType: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## language

```TypeScript
language: string
```

系统语言。

**类型：** string

**起始版本：** 4

**废弃版本：** 6

<!--Device-DeviceResponse-language: string--><!--Device-DeviceResponse-language: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## manufacturer

```TypeScript
manufacturer: string
```

生产商。

**类型：** string

**起始版本：** 3

**废弃版本：** 6

<!--Device-DeviceResponse-manufacturer: string--><!--Device-DeviceResponse-manufacturer: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## model

```TypeScript
model: string
```

型号。

**类型：** string

**起始版本：** 3

**废弃版本：** 6

<!--Device-DeviceResponse-model: string--><!--Device-DeviceResponse-model: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## product

```TypeScript
product: string
```

产品代号。

**类型：** string

**起始版本：** 3

**废弃版本：** 6

<!--Device-DeviceResponse-product: string--><!--Device-DeviceResponse-product: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## region

```TypeScript
region: string
```

系统地区。

**类型：** string

**起始版本：** 4

**废弃版本：** 6

<!--Device-DeviceResponse-region: string--><!--Device-DeviceResponse-region: string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## screenDensity

```TypeScript
screenDensity: number
```

屏幕像素密度。表示屏幕每英寸的像素点数量，单位为dpi(dots per inch)。不同设备的屏幕像素密度存在差异。

**类型：** number

**起始版本：** 4

**废弃版本：** 6

<!--Device-DeviceResponse-screenDensity: number--><!--Device-DeviceResponse-screenDensity: number-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## screenShape

```TypeScript
screenShape: 'rect' | 'circle'
```

屏幕形状。可取值：

- rect：方形屏；

- circle：圆形屏。

**类型：** 'rect' \| 'circle'

**起始版本：** 4

**废弃版本：** 6

<!--Device-DeviceResponse-screenShape: 'rect' | 'circle'--><!--Device-DeviceResponse-screenShape: 'rect' | 'circle'-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## windowHeight

```TypeScript
windowHeight: number
```

可使用的窗口宽度，单位px。不同设备的可使用窗口尺寸存在差异。

**类型：** number

**起始版本：** 3

**废弃版本：** 6

<!--Device-DeviceResponse-windowHeight: number--><!--Device-DeviceResponse-windowHeight: number-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## windowWidth

```TypeScript
windowWidth: number
```

可使用的窗口宽度，单位px。不同设备的可使用窗口尺寸存在差异。

**类型：** number

**起始版本：** 3

**废弃版本：** 6

<!--Device-DeviceResponse-windowWidth: number--><!--Device-DeviceResponse-windowWidth: number-End-->

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

