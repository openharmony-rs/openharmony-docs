# DeviceProfileInfo（系统接口）

设备信息。

**起始版本：** 15

<!--Device-distributedDeviceManager-interface DeviceProfileInfo--><!--Device-distributedDeviceManager-interface DeviceProfileInfo-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
```

## bleMac

```TypeScript
bleMac: string
```

蓝牙BLE的MAC地址。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-bleMac: string--><!--Device-DeviceProfileInfo-bleMac: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## brMac

```TypeScript
brMac: string
```

蓝牙BR的MAC地址。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-brMac: string--><!--Device-DeviceProfileInfo-brMac: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## deviceId

```TypeScript
deviceId: string
```

设备ID。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-deviceId: string--><!--Device-DeviceProfileInfo-deviceId: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## deviceName

```TypeScript
deviceName: string
```

设备名称。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-deviceName: string--><!--Device-DeviceProfileInfo-deviceName: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## deviceSn

```TypeScript
deviceSn: string
```

设备序列号。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-deviceSn: string--><!--Device-DeviceProfileInfo-deviceSn: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## deviceType

```TypeScript
deviceType: string
```

设备类型。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-deviceType: string--><!--Device-DeviceProfileInfo-deviceType: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## firmwareVersion

```TypeScript
firmwareVersion: string
```

固件版本。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-firmwareVersion: string--><!--Device-DeviceProfileInfo-firmwareVersion: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## hardwareVersion

```TypeScript
hardwareVersion: string
```

硬件版本。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-hardwareVersion: string--><!--Device-DeviceProfileInfo-hardwareVersion: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## internalModel

```TypeScript
internalModel?: string
```

设备所属产品的内部型号。默认为空。

**类型：** string

**起始版本：** 18

<!--Device-DeviceProfileInfo-internalModel?: string--><!--Device-DeviceProfileInfo-internalModel?: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## isLocalDevice

```TypeScript
isLocalDevice: boolean
```

是否为本地设备。

- false：表示非本地设备，即被查询的其他设备。  
- true：表示本地设备，即当前正在使用该接口的设备。

**类型：** boolean

**起始版本：** 15

<!--Device-DeviceProfileInfo-isLocalDevice: boolean--><!--Device-DeviceProfileInfo-isLocalDevice: boolean-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## mac

```TypeScript
mac: string
```

MAC地址。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-mac: string--><!--Device-DeviceProfileInfo-mac: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## manufacturer

```TypeScript
manufacturer: string
```

制造商。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-manufacturer: string--><!--Device-DeviceProfileInfo-manufacturer: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## model

```TypeScript
model: string
```

设备型号。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-model: string--><!--Device-DeviceProfileInfo-model: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## modifyTime

```TypeScript
modifyTime: string
```

修改时间。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-modifyTime: string--><!--Device-DeviceProfileInfo-modifyTime: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## productId

```TypeScript
productId: string
```

设备所属产品ID。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-productId: string--><!--Device-DeviceProfileInfo-productId: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## productName

```TypeScript
productName?: string
```

设备所属的产品名称。默认为空。

**类型：** string

**起始版本：** 18

<!--Device-DeviceProfileInfo-productName?: string--><!--Device-DeviceProfileInfo-productName?: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## protocolType

```TypeScript
protocolType: number
```

协议类型。

**类型：** number

**起始版本：** 15

<!--Device-DeviceProfileInfo-protocolType: int--><!--Device-DeviceProfileInfo-protocolType: int-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## registerTime

```TypeScript
registerTime: string
```

注册时间。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-registerTime: string--><!--Device-DeviceProfileInfo-registerTime: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## sdkVersion

```TypeScript
sdkVersion: string
```

SDK版本。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-sdkVersion: string--><!--Device-DeviceProfileInfo-sdkVersion: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## services

```TypeScript
services?: Array<ServiceProfileInfo>
```

服务配置信息列表。默认为空。

**类型：** Array<ServiceProfileInfo>

**起始版本：** 15

<!--Device-DeviceProfileInfo-services?: Array<ServiceProfileInfo>--><!--Device-DeviceProfileInfo-services?: Array<ServiceProfileInfo>-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## setupType

```TypeScript
setupType: number
```

设备类型。

**类型：** number

**起始版本：** 15

<!--Device-DeviceProfileInfo-setupType: int--><!--Device-DeviceProfileInfo-setupType: int-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## shareTime

```TypeScript
shareTime: string
```

分享时间。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-shareTime: string--><!--Device-DeviceProfileInfo-shareTime: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## sleMac

```TypeScript
sleMac: string
```

Starflash的MAC地址。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-sleMac: string--><!--Device-DeviceProfileInfo-sleMac: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## softwareVersion

```TypeScript
softwareVersion: string
```

软件版本。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-softwareVersion: string--><!--Device-DeviceProfileInfo-softwareVersion: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## subProductId

```TypeScript
subProductId?: string
```

设备所属产品子ID。默认为空。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-subProductId?: string--><!--Device-DeviceProfileInfo-subProductId?: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## wiseDeviceId

```TypeScript
wiseDeviceId: string
```

已注册设备标识。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-wiseDeviceId: string--><!--Device-DeviceProfileInfo-wiseDeviceId: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## wiseUserId

```TypeScript
wiseUserId: string
```

已注册用户标识。

**类型：** string

**起始版本：** 15

<!--Device-DeviceProfileInfo-wiseUserId: string--><!--Device-DeviceProfileInfo-wiseUserId: string-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

