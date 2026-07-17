# SubscribeInfo（系统接口）

发现信息。

**起始版本：** 7

**废弃版本：** 11

<!--Device-deviceManager-interface SubscribeInfo--><!--Device-deviceManager-interface SubscribeInfo-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { deviceManager } from '@kit.DistributedServiceKit';
```

## capability

```TypeScript
capability: SubscribeCap
```

发现能力。

**类型：** SubscribeCap

**起始版本：** 7

**废弃版本：** 11

<!--Device-SubscribeInfo-capability: SubscribeCap--><!--Device-SubscribeInfo-capability: SubscribeCap-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## freq

```TypeScript
freq: ExchangeFreq
```

发现频率。

**类型：** ExchangeFreq

**起始版本：** 7

**废弃版本：** 11

<!--Device-SubscribeInfo-freq: ExchangeFreq--><!--Device-SubscribeInfo-freq: ExchangeFreq-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## isSameAccount

```TypeScript
isSameAccount: boolean
```

是否同账号，true表示同账号，false表示异账号。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 11

<!--Device-SubscribeInfo-isSameAccount: boolean--><!--Device-SubscribeInfo-isSameAccount: boolean-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## isWakeRemote

```TypeScript
isWakeRemote: boolean
```

是否唤醒设备，true表示唤醒，false表示不用唤醒。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 11

<!--Device-SubscribeInfo-isWakeRemote: boolean--><!--Device-SubscribeInfo-isWakeRemote: boolean-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## medium

```TypeScript
medium: ExchangeMedium
```

发现类型。

**类型：** ExchangeMedium

**起始版本：** 7

**废弃版本：** 11

<!--Device-SubscribeInfo-medium: ExchangeMedium--><!--Device-SubscribeInfo-medium: ExchangeMedium-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## mode

```TypeScript
mode: DiscoverMode
```

发现模式。

**类型：** DiscoverMode

**起始版本：** 7

**废弃版本：** 11

<!--Device-SubscribeInfo-mode: DiscoverMode--><!--Device-SubscribeInfo-mode: DiscoverMode-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

## subscribeId

```TypeScript
subscribeId: number
```

发现标识，用于标识不同的发现周期。 取值范围1~65535。

**类型：** number

**起始版本：** 7

**废弃版本：** 11

<!--Device-SubscribeInfo-subscribeId: number--><!--Device-SubscribeInfo-subscribeId: number-End-->

**系统能力：** SystemCapability.DistributedHardware.DeviceManager

**系统接口：** 此接口为系统接口。

