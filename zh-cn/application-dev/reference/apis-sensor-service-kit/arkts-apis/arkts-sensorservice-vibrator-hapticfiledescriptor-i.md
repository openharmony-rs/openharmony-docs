# HapticFileDescriptor

自定义振动配置文件的描述符，必须确认资源文件可用，其参数可通过\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_从 沙箱路径获取或者通过 [getRawFd]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_ 从HAP资源获取。使用场景：振动序列被存储在一个文件中，需要根据偏移量和长度进行振动，振动序列存储格式，请参考 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_。 使用时需注意以下问题： - 振动结束后建议及时关闭文件描述符，避免资源泄露。使用getRawFd获取的文件描述符需通过closeRawFd关闭，使用fileIo.open获取的需通过fileIo.close关闭。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-vibrator-interface HapticFileDescriptor--><!--Device-vibrator-interface HapticFileDescriptor-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## fd

```TypeScript
fd: int
```

资源文件描述符。可通过\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_从沙箱路径获取或通过 [getRawFd]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 从HAP资源获取。

**类型：** int

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-HapticFileDescriptor-fd: int--><!--Device-HapticFileDescriptor-fd: int-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## length

```TypeScript
length?: long
```

资源长度。单位：字节。默认值：从偏移位置至文件结尾的长度。取值范围：不可超出文件有效范围。使用场景：适用于振动配置文件中包含多种振动效果、需要指定特定长度振动的场景。不填写时默认读取从偏移位置至文件结尾的全部内容。

**类型：** long

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-HapticFileDescriptor-length?: long--><!--Device-HapticFileDescriptor-length?: long-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## offset

```TypeScript
offset?: long
```

距文件起始位置的偏移量。单位：字节。默认值：文件起始位置（0）。取值范围：不可超出文件有效范围。使用场景：适用于振动配置文件中包含多种振动效果、需要指定从特定偏移位置开始振动的场景。不填写时默认从文件起始位置开始。

**类型：** long

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-HapticFileDescriptor-offset?: long--><!--Device-HapticFileDescriptor-offset?: long-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

