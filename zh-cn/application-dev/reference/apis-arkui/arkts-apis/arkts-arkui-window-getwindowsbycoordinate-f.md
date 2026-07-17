# getWindowsByCoordinate

## 导入模块

```TypeScript
import { window } from '@kit.ArkUI';
```

## getWindowsByCoordinate

```TypeScript
function getWindowsByCoordinate(displayId: number, windowNumber?: number, x?: number, y?: number):
      Promise<Array<Window>>
```

查询本应用指定坐标下的可见窗口数组，按当前窗口层级排列，层级最高的窗口对应数组下标为0，使用Promise异步回调。

**起始版本：** 14

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-window-function getWindowsByCoordinate(displayId: long, windowNumber?: int, x?: int, y?: int):
      Promise<Array<Window>>--><!--Device-window-function getWindowsByCoordinate(displayId: long, windowNumber?: int, x?: int, y?: int):
      Promise<Array<Window>>-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | number | 是 | 查询窗口所在的displayId，该参数应为整数，传入非整数会忽略掉小数部分，可以在窗口属性[WindowProperties](arkts-arkui-window-windowproperties-i.md)中获取。 |
| windowNumber | number | 否 | 查询的窗口数量，该参数应为大于0的整数，传入非整数会忽略掉小数部分，未设置或小于等于0返回所有满足条件的窗口。 |
| x | number | 否 | 查询的x坐标，以屏幕左上角为原点，该参数应为非负整数，传入非整数会忽略掉小数部分，未设置或小于0返回所有可见窗口。 |
| y | number | 否 | 查询的y坐标，以屏幕左上角为原点，该参数应为非负整数，传入非整数会忽略掉小数部分，未设置或小于0返回所有可见窗口。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<Window>> | Promise对象。返回获取到的窗口对象数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally.Possible cause: Internal task error. |

**示例：**

```TypeScript
import { window } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    let windowClass: window.Window | undefined = undefined;
    try {
      let displayId = 0;
      window.getWindowsByCoordinate(displayId, 2, 500, 500).then((data) => {
        console.info(`Succeeded in getting windows. Data: ${data}`);
        for (let windowObject of data) {
          // do something with window
          windowClass = windowObject;
        }
      }).catch((err: BusinessError) => {
        console.error(`Failed to get window from point. Cause code: ${err.code}, message: ${err.message}`);
      });
    } catch (exception) {
      console.error(`Failed to get window from point. Cause code: ${exception.code}, message: ${exception.message}`);
    }
  }
}

```

