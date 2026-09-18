# EapData

EAP信息。

​**系统能力**​：SystemCapability.Communication.NetManager.Eap

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## bufferLen

```TypeScript
bufferLen: number
```

数据长度。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## eapBuffer

```TypeScript
eapBuffer: Uint8Array
```

从EAP header开始的EAP原始数据，未加密。

**类型：** Uint8Array

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## msgId

```TypeScript
msgId: number
```

伪随机数，用于关联处理前后的EAP数据。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap
