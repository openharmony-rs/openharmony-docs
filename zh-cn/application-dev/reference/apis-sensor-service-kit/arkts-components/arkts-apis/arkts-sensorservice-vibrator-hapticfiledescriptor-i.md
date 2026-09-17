# HapticFileDescriptor

自定义振动配置文件的描述符，必须确认资源文件可用，其参数可通过[fileIo.open](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileioopen)从沙箱路径获取或者通过[getRawFd](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getrawfd)从HAP资源获取。使用场景：振动序列被存储在一个文件中，需要根据偏移量和长度进行振动，振动序列存储格式，请参考[振动效果说明](../../../device/sensor/vibrator-guidelines.md#振动效果说明)。使用时需注意以下问题：

- 振动结束后建议及时关闭文件描述符，避免资源泄露。使用getRawFd获取的文件描述符需通过closeRawFd关闭，使用fileIo.open获取的需通过fileIo.close关闭。

**起始版本：** 10

**系统能力：** SystemCapability.Sensors.MiscDevice

## 导入模块

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## fd

```TypeScript
fd: number
```

资源文件描述符。可通过[fileIo.open](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileioopen)从沙箱路径获取或通过[getRawFd](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getrawfd)从HAP资源获取。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Sensors.MiscDevice

## length

```TypeScript
length?: number
```

资源长度。单位：B（字节）。默认值：从偏移位置至文件结尾的长度。取值范围：不可超出文件有效范围。使用场景：适用于振动配置文件中包含多种振动效果、需要指定特定长度振动的场景。不填写时默认读取从偏移位置至文件结尾的全部内容。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Sensors.MiscDevice

## offset

```TypeScript
offset?: number
```

距文件起始位置的偏移量。单位：B（字节）。默认值：文件起始位置（0）。取值范围：不可超出文件有效范围。使用场景：适用于振动配置文件中包含多种振动效果、需要指定从特定偏移位置开始振动的场景。不填写时默认从文件起始位置开始。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Sensors.MiscDevice
