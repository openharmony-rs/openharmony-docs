# EapData

EAP信息。 ​**系统能力**​：SystemCapability.Communication.NetManager.Eap

**起始版本：** 20

<!--Device-eap-interface EapData--><!--Device-eap-interface EapData-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## bufferLen

```TypeScript
bufferLen: int
```

数据长度。

**类型：** int

**起始版本：** 20

<!--Device-EapData-bufferLen: int--><!--Device-EapData-bufferLen: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

## eapBuffer

```TypeScript
eapBuffer: Uint8Array
```

从EAP header开始的EAP原始数据，未加密。

**类型：** Uint8Array

**起始版本：** 20

<!--Device-EapData-eapBuffer: Uint8Array--><!--Device-EapData-eapBuffer: Uint8Array-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

## msgId

```TypeScript
msgId: int
```

伪随机数，用于关联处理前后的EAP数据。

**类型：** int

**起始版本：** 20

<!--Device-EapData-msgId: int--><!--Device-EapData-msgId: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

