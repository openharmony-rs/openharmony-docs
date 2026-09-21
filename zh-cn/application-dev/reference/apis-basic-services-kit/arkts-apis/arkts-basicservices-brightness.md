# @ohos.brightness(屏幕亮度)

该模块提供屏幕亮度的设置接口，支持设置指定亮度值及连续调节亮度，适用于需要在应用中动态控制屏幕亮度的场景，可实现屏幕亮度的精细化管理。

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
| [setValue](arkts-basicservices-brightness-setvalue-f-sys.md#setvalue) | 设置系统的屏幕亮度。适用于需要固定屏幕亮度的场景，例如阅读应用、视频播放应用、夜间模式等。若需要连续调节亮度，建议使用setValue(value: number, continuous: boolean)接口。 |
| [setValue](arkts-basicservices-brightness-setvalue-f-sys.md#setvalue-1) | 设置系统的屏幕亮度。用于连续调节亮度的场景，在连续调节亮度过程中，设置continuous为true可减少不必要的系统亮度刷新，结束时设置continuous为false恢复正常刷新模式，从而提升连续调节时的流畅度。 |
<!--DelEnd-->
