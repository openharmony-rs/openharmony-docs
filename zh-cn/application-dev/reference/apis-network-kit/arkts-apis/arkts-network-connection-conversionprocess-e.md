# ConversionProcess

ASCII/Unicode转码转换流程参数的枚举。

**起始版本：** 23

<!--Device-connection-export enum ConversionProcess--><!--Device-connection-export enum ConversionProcess-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## NO_CONFIGURATION

```TypeScript
NO_CONFIGURATION = 0
```

仅允许转换已分配的Unicode代码点的域名（Unicode为每个字符分配一个唯一的数字，这个数字就叫做代码点）。

**起始版本：** 23

<!--Device-ConversionProcess-NO_CONFIGURATION = 0--><!--Device-ConversionProcess-NO_CONFIGURATION = 0-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## ALLOW_UNASSIGNED

```TypeScript
ALLOW_UNASSIGNED = 1
```

允许转换包含未分配Unicode代码点的域名(在Unicode字符集中，并非所有代码点都已分配字符，即未分配Unicode代码点)。

**起始版本：** 23

<!--Device-ConversionProcess-ALLOW_UNASSIGNED = 1--><!--Device-ConversionProcess-ALLOW_UNASSIGNED = 1-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## USE_STD3_ASCII_RULES

```TypeScript
USE_STD3_ASCII_RULES = 2
```

在转换过程中，强制使用STD-3 ASCII规则（即RFC 1123标准）检查生成的ASCII域名。

**起始版本：** 23

<!--Device-ConversionProcess-USE_STD3_ASCII_RULES = 2--><!--Device-ConversionProcess-USE_STD3_ASCII_RULES = 2-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

