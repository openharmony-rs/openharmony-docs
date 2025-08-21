# @system.vibrator (振动)
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @butterls-->
<!--Tester: @murphy84-->
<!--Adviser: @hu-zhiqiong-->

vibrator模块提供控制马达振动的能力，主要包含灯的列表查询、打开灯、关闭灯等接口，振动器的列表查询、振动器的振动器效果查询、触发/关闭振动器等接口。

控制类小器件指的是设备上的LED灯和振动器。其中，LED灯主要用作指示（如充电状态）、闪烁功能（如三色灯）等；振动器主要用于闹钟、开关机振动、来电振动等场景。


> **说明：**
> - 本模块首批接口从API version 3开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 从API Version 8开始，该接口不再维护，推荐使用新接口[`@ohos.vibrator`](js-apis-vibrator.md)。
> - 该功能使用需要对应硬件支持，仅支持真机调试。


## 导入模块


```ts
import { Vibrator } from '@kit.SensorServiceKit';
```

## Vibrator.vibrate

 vibrate(options?: VibrateOptions): void

触发设备振动。

**需要权限**：ohos.permission.VIBRATE

**系统能力**：SystemCapability.Sensors.MiscDevice.Lite

**参数**：

| 参数名  | 类型                              | 必填 | 说明       |
| ------- | --------------------------------- | ---- | ---------- |
| options | [VibrateOptions](#vibrateoptions) | 否   | 振动模式。 |

**示例**：

```ts
import { Vibrator, VibrateOptions } from '@kit.SensorServiceKit';

let vibrateOptions: VibrateOptions = {
  mode: 'short',
  success: () => {
    console.info('Succeed in vibrating');
  },
  fail: (data: string, code: number) => {
    console.info(`Failed to vibrate. Data: ${data}, code: ${code}`);
  },
  complete: () => {
    console.info('completed in vibrating');
  }
};
Vibrator.vibrate(vibrateOptions);
```

## VibrateOptions

振动模式。

**需要权限**：ohos.permission.VIBRATE

**系统能力**：SystemCapability.Sensors.MiscDevice.Lite

| 名称     | 类型     | 必填 | 说明                                                         |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| mode     | string   | 否   | 振动的模式，其中long表示长振动，short表示短振动，默认值为long。 |
| success  | Function | 否   | 感应到振动数据变化后的回调函数。                             |
| fail     | Function | 否   | 接口调用失败的回调函数。                                     |
| complete | Function | 否   | 接口调用结束的回调函数。                                     |