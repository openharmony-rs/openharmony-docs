# @ohos.app.ability.kioskManager

KioskManager模块提供Kiosk模式管理能力，包括系统进入/退出Kiosk模式操作。Kiosk模式是一种特殊的设备锁定模式，可以确保设备界面只服务于特定的交互场景。在这种模式下，用户只能使用特定的应用。例如，在银行ATM机上，用户只能通过ATM软件进行操作，而不能退出该软件或切换到其他应用。

**起始版本：** 20

<!--Device-unnamed-declare namespace kioskManager--><!--Device-unnamed-declare namespace kioskManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { kioskManager } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [enterKioskMode](arkts-ability-kioskmanager-enterkioskmode-f.md#enterkioskmode-1) | 进入Kiosk模式。使用Promise异步回调。该接口仅在Phone、PC/2in1和Tablet设备中可正常调用，在其他设备中返回801错误码。 |
| [exitKioskMode](arkts-ability-kioskmanager-exitkioskmode-f.md#exitkioskmode-1) | 退出Kiosk模式。使用Promise异步回调。该接口仅对已进入Kiosk模式的应用生效。该接口仅在Phone、PC/2in1和Tablet设备中可正常调用，在其他设备中返回801错误码。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getKioskStatus](arkts-ability-kioskmanager-getkioskstatus-f-sys.md#getkioskstatus-1) | 获取系统Kiosk模式的状态信息（包括当前系统是否处于Kiosk模式、进入Kiosk模式应用的名称和UID）。使用Promise异步回调。该接口仅在Phone、PC/2in1和Tablet设备中可正常调用，在其他设备中返回801错误码。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [KioskStatus](arkts-ability-kioskmanager-kioskstatus-t.md) | Kiosk状态信息，包括系统是否处于Kiosk模式以及该模式下的应用信息。 |

