# AudioHapticFileDescriptor

描述音振文件描述符。 > **注意：** > > 开发者需要确保fd是可用的文件描述符，且offset和length的值都是正确的。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-audioHaptic-interface AudioHapticFileDescriptor--><!--Device-audioHaptic-interface AudioHapticFileDescriptor-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

## fd

```TypeScript
fd: int
```

音振资源文件的文件描述符，通常大于等于0。

**类型：** int

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-AudioHapticFileDescriptor-fd: int--><!--Device-AudioHapticFileDescriptor-fd: int-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

## length

```TypeScript
length?: long
```

读取数据的字节长度。默认情况下，长度为文件中从偏移量位置开始的剩余字节数。

**类型：** long

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-AudioHapticFileDescriptor-length?: long--><!--Device-AudioHapticFileDescriptor-length?: long-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

## offset

```TypeScript
offset?: long
```

文件中数据读取的偏移量，单位为字节。默认情况下，偏移量为0。

**类型：** long

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-AudioHapticFileDescriptor-offset?: long--><!--Device-AudioHapticFileDescriptor-offset?: long-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

