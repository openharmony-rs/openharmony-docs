# @system.brightness (屏幕亮度)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @w_Machine_cc-->

该模块提供屏幕亮度和模式的查询、调节接口。

> **说明：**
>
> - 从API Version 7 开始不再维护<!--Del-->。建议使用[@ohos.brightness](js-apis-brightness-sys.md)替代<!--DelEnd-->，替代接口能力仅对系统应用开放。
> - 本模块首批接口从API version 3开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块


```js
import brightness, { BrightnessModeResponse, BrightnessResponse } from '@system.brightness';
```


## brightness.getValue<sup>(deprecated)</sup>

getValue(options?: GetBrightnessOptions): void

获得设备当前的屏幕亮度值。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options | [GetBrightnessOptions](#getbrightnessoptionsdeprecated) | 否   | 获取屏幕亮度的参数对象。可选，默认为空。 |

**示例：**

  ```js
  brightness.getValue({
      success: (data: BrightnessResponse) => {
        console.log('success get brightness value:' + data.value);
      },
      fail: (data: string, code: number) => {
        console.error('get brightness fail, code: ' + code + ', data: ' + data);
      }
  });
  ```


## brightness.setValue<sup>(deprecated)</sup>

setValue(options?: SetBrightnessOptions): void

设置设备当前的屏幕亮度值。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options | [SetBrightnessOptions](#setbrightnessoptionsdeprecated) | 否   | 设置屏幕亮度的参数对象。可选，默认为空。 |

**示例：**

  ```js
  brightness.setValue({
      value: 100,
      success: () => {
        console.log('handling set brightness success.');
      },
      fail: (data: string, code: number) => {
        console.error('handling set brightness value fail, code:' + code + ', data: ' + data);
      }
  });
  ```


## brightness.getMode<sup>(deprecated)</sup>

getMode(options?: GetBrightnessModeOptions): void

获得当前屏幕亮度模式。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options | [GetBrightnessModeOptions](#getbrightnessmodeoptionsdeprecated) | 否 | 获取屏幕亮度模式的参数对象。可选，默认为空。 |

**示例：**

  ```js
  brightness.getMode({
      success: (data: BrightnessModeResponse) => {
        console.log('success get mode:' + data.mode);
      },
      fail: (data: string, code: number) => {
        console.error('handling get mode fail, code:' + code + ', data: ' + data);
      }
  });
  ```


## brightness.setMode<sup>(deprecated)</sup>

setMode(options?: SetBrightnessModeOptions): void

设置设备当前的屏幕亮度模式。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**
| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options | [SetBrightnessModeOptions](#setbrightnessmodeoptionsdeprecated) | 否   | 设置屏幕亮度模式的参数对象。可选，默认为空。 |

**示例：**

  ```js
  brightness.setMode({
      mode: 1,
      success: () => {
        console.log('handling set mode success.');
      },
      fail: (data: string, code: number) => {
        console.error('handling set mode fail, code:' + code + ', data: ' + data);
      }
  });
  ```


## brightness.setKeepScreenOn<sup>(deprecated)</sup>

setKeepScreenOn(options?: SetKeepScreenOnOptions): void

>从API version 7开始不再维护，建议使用[window.setWindowKeepScreenOn()](../apis-arkui/arkts-apis-window-Window.md#setwindowkeepscreenon9)替代。

设置屏幕是否保持常亮状态，开启常亮模式推荐在onShow()阶段调用。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options | [SetKeepScreenOnOptions](#setkeepscreenonoptionsdeprecated) | 否 | 设置屏幕常亮的参数对象。可选，默认为空。 |

**示例：**

  ```js
  brightness.setKeepScreenOn({
      keepScreenOn: true,
      success: () => {
        console.log('handling set keep screen on success.');
      },
      fail: (data: string, code: number) => {
        console.error('handling set keep screen on fail, code:' + code + ', data: ' + data);
      }
  });
  ```
## GetBrightnessOptions<sup>(deprecated)</sup>

获取屏幕亮度的参数对象。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

| 名称     | 类型                                                      | 必填 | 说明                                                         |
| -------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| success  | (data: [BrightnessResponse](#brightnessresponsedeprecated)) => void | 否   | 接口调用成功的回调函数。data为[BrightnessResponse](#brightnessresponsedeprecated)类型的返回值。 |
| fail     | (data: string, code: number) => void                      | 否   | 接口调用失败的回调函数。data为错误信息，code为错误码。       |
| complete | () => void                                                | 否   | 接口调用结束的回调函数。                                     |

## SetBrightnessOptions<sup>(deprecated)</sup>

设置屏幕亮度的参数对象。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

| 名称     | 类型                                 | 必填 | 说明                                                         |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| value    | number                               | 是   | 屏幕亮度，值为1-255之间的整数。<br/>-&nbsp;如果值小于等于0，系统按1处理。<br/>-&nbsp;如果值大于255，系统按255处理。<br/>-&nbsp;如果值为小数，系统将处理为整数。例如设置为8.1，系统按8处理。 |
| success  | () => void                           | 否   | 接口调用成功的回调函数。                                     |
| fail     | (data: string, code: number) => void | 否   | 接口调用失败的回调函数。data为错误信息，code为错误码。       |
| complete | () => void                           | 否   | 接口调用结束的回调函数。                                     |

## BrightnessResponse<sup>(deprecated)</sup>

包含屏幕亮度的对象。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

| 名称 | 类型 | 可读 | 可写 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| value | number | 是 | 否 | 屏幕亮度，范围：1到255。 |

## GetBrightnessModeOptions<sup>(deprecated)</sup>

获取屏幕亮度模式的参数对象。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

| 名称     | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| success  | (data: [BrightnessModeResponse](#brightnessmoderesponsedeprecated)) => void | 否   | 接口调用成功的回调函数。data为[BrightnessModeResponse](#brightnessmoderesponsedeprecated)类型的返回值。 |
| fail     | (data: string, code: number) => void                         | 否   | 接口调用失败的回调函数。data为错误信息，code为错误码。       |
| complete | () => void                                                   | 否   | 接口调用结束的回调函数。                                     |

## SetBrightnessModeOptions<sup>(deprecated)</sup>

设置屏幕亮度模式的参数对象。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

| 名称     | 类型                                 | 必填 | 说明                                                   |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------ |
| mode     | number                               | 是   | 0表示手动调节屏幕亮度模式，1表示自动调节屏幕亮度模式。 |
| success  | () => void                           | 否   | 接口调用成功的回调函数。                               |
| fail     | (data: string, code: number) => void | 否   | 接口调用失败的回调函数。data为错误信息，code为错误码。 |
| complete | () => void                           | 否   | 接口调用结束的回调函数。                               |

## BrightnessModeResponse<sup>(deprecated)</sup>

包含屏幕亮度模式的对象。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

| 名称 | 类型 | 可读 | 可写 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| mode | number | 是 | 否 | 0表示手动调节屏幕亮度模式，1表示自动调节屏幕亮度模式。 |

## SetKeepScreenOnOptions<sup>(deprecated)</sup>

设置屏幕常亮的参数对象。

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager.Lite

| 名称         | 类型                                 | 必填 | 说明                                                   |
| ------------ | ------------------------------------ | ---- | ------------------------------------------------------ |
| keepScreenOn | boolean                              | 是   | true表示保持屏幕常亮，false表示取消屏幕常亮。          |
| success      | () => void                           | 否   | 接口调用成功的回调函数。                               |
| fail         | (data: string, code: number) => void | 否   | 接口调用失败的回调函数。data为错误信息，code为错误码。 |
| complete     | () => void                           | 否   | 接口调用结束的回调函数。                               |

