# SerialAttribute

串口的配置参数。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-serialManager-interface SerialAttribute--><!--Device-serialManager-interface SerialAttribute-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

## baudRate

```TypeScript
baudRate: BaudRates
```

串口波特率。

**类型：** BaudRates

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-SerialAttribute-baudRate: BaudRates--><!--Device-SerialAttribute-baudRate: BaudRates-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

## dataBits

```TypeScript
dataBits?: DataBits
```

串口数据位，默认值为8位。

**类型：** DataBits

**默认值：** DATABIT_8

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-SerialAttribute-dataBits?: DataBits--><!--Device-SerialAttribute-dataBits?: DataBits-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

## parity

```TypeScript
parity?: Parity
```

串口奇偶校验，默认值为None，无奇偶校验。

**类型：** Parity

**默认值：** NONE

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-SerialAttribute-parity?: Parity--><!--Device-SerialAttribute-parity?: Parity-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

## stopBits

```TypeScript
stopBits?: StopBits
```

串口停止位，默认值为1位。

**类型：** StopBits

**默认值：** STOPBIT_1

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-SerialAttribute-stopBits?: StopBits--><!--Device-SerialAttribute-stopBits?: StopBits-End-->

**系统能力：** SystemCapability.USB.USBManager.Serial

