# InterfaceConflictInfo

```TypeScript
interface InterfaceConflictInfo
```

描述当已独占声明的USB接口被其他进程以非独占方式声明时的冲突信息，通过调用[usbManager.claimInterfaceExclusive](arkts-basicservices-usbmanager-claiminterfaceexclusive-f.md)独占声明接口后使用。

> **说明：** 
> 
> 此回调在其他进程调用非互斥的
> [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md)
> 接口声明同一USB接口时触发。独占持有方可通过此回调获知潜在的访问冲突。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.USB.USBManager

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

## busNum

```TypeScript
busNum: number
```

USB设备的总线地址。取值限定为整数。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.USB.USBManager

## devAddr

```TypeScript
devAddr: number
```

USB设备的设备地址。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.USB.USBManager

## interfaceId

```TypeScript
interfaceId: number
```

被其他进程声明的USB接口的ID。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.USB.USBManager
