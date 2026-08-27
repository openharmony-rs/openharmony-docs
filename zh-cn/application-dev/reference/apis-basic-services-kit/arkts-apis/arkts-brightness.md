# @ohos.brightness

该模块提供屏幕亮度的设置接口。

> **说明：**
> 
> - 本模块接口为系统接口。

**起始版本：** 7

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { brightness } from '@kit.BasicServicesKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [setValue](arkts-basicservices-brightness-setvalue-f-sys.md) | 设置系统的屏幕亮度。适用于需要固定屏幕亮度的场景，例如阅读应用、视频播放应用、夜间模式等。若需要连续调节亮度，建议使用setValue(value: number, continuous: boolean)接口。 |
| [setValue](arkts-basicservices-brightness-setvalue-f-sys.md) | 设置系统的屏幕亮度。用于连续调节亮度的场景，在连续调节亮度过程中，设置continuous为true，结束时设置continuous为false，会有更好的性能。 |
<!--DelEnd-->
