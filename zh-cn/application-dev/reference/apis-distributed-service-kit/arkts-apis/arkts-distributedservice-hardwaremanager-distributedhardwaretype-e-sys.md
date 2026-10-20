# DistributedHardwareType（系统接口）

```TypeScript
enum DistributedHardwareType
```

指定要操作的分布式硬件类型，决定暂停、恢复或停止操作的硬件范围。例如，设置为CAMERA时仅操作分布式相机，设置为ALL时操作所有分布式硬件。使用该参数前需确保对应的分布式硬件服务已启动。

**起始版本：** 11

<!--Device-hardwareManager-enum DistributedHardwareType--><!--Device-hardwareManager-enum DistributedHardwareType-End-->

**系统能力：** SystemCapability.DistributedHardware.DistributedHardwareFWK

**系统接口：** 此接口为系统接口。

## ALL

```TypeScript
ALL = 0
```

表示所有分布式硬件。

**起始版本：** 11

<!--Device-DistributedHardwareType-ALL = 0--><!--Device-DistributedHardwareType-ALL = 0-End-->

**系统能力：** SystemCapability.DistributedHardware.DistributedHardwareFWK

**系统接口：** 此接口为系统接口。

## CAMERA

```TypeScript
CAMERA = 1
```

表示分布式相机。

**起始版本：** 11

<!--Device-DistributedHardwareType-CAMERA = 1--><!--Device-DistributedHardwareType-CAMERA = 1-End-->

**系统能力：** SystemCapability.DistributedHardware.DistributedHardwareFWK

**系统接口：** 此接口为系统接口。

## MIC

```TypeScript
MIC = 1024
```

表示分布式麦克风。

**起始版本：** 11

<!--Device-DistributedHardwareType-MIC = 1024--><!--Device-DistributedHardwareType-MIC = 1024-End-->

**系统能力：** SystemCapability.DistributedHardware.DistributedHardwareFWK

**系统接口：** 此接口为系统接口。

## MODEM_MIC

```TypeScript
MODEM_MIC = 256
```

表示分布式移动通话的麦克风。

**起始版本：** 11

<!--Device-DistributedHardwareType-MODEM_MIC = 256--><!--Device-DistributedHardwareType-MODEM_MIC = 256-End-->

**系统能力：** SystemCapability.DistributedHardware.DistributedHardwareFWK

**系统接口：** 此接口为系统接口。

## MODEM_SPEAKER

```TypeScript
MODEM_SPEAKER = 512
```

表示分布式移动通话的扬声器。

**起始版本：** 11

<!--Device-DistributedHardwareType-MODEM_SPEAKER = 512--><!--Device-DistributedHardwareType-MODEM_SPEAKER = 512-End-->

**系统能力：** SystemCapability.DistributedHardware.DistributedHardwareFWK

**系统接口：** 此接口为系统接口。

## SCREEN

```TypeScript
SCREEN = 8
```

表示分布式屏幕。

**起始版本：** 11

<!--Device-DistributedHardwareType-SCREEN = 8--><!--Device-DistributedHardwareType-SCREEN = 8-End-->

**系统能力：** SystemCapability.DistributedHardware.DistributedHardwareFWK

**系统接口：** 此接口为系统接口。

## SPEAKER

```TypeScript
SPEAKER = 2048
```

表示分布式扬声器。

**起始版本：** 11

<!--Device-DistributedHardwareType-SPEAKER = 2048--><!--Device-DistributedHardwareType-SPEAKER = 2048-End-->

**系统能力：** SystemCapability.DistributedHardware.DistributedHardwareFWK

**系统接口：** 此接口为系统接口。
