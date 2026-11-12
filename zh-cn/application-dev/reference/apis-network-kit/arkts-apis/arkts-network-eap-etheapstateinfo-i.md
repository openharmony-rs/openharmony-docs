# EthEapStateInfo

```TypeScript
interface EthEapStateInfo
```

表示通过stateChange回调传递的802.1X EAP身份验证状态信息。

**起始版本：** 26.0.1

<!--Device-eap-interface EthEapStateInfo--><!--Device-eap-interface EthEapStateInfo-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## message

```TypeScript
message?: string
```

补充消息，如失败原因等。成功时为空。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EthEapStateInfo-message?: string--><!--Device-EthEapStateInfo-message?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

## retryCount

```TypeScript
retryCount: number
```

当前重试计数（成功时重置为0）。取值限定为整数。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EthEapStateInfo-retryCount: int--><!--Device-EthEapStateInfo-retryCount: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

## state

```TypeScript
state: EthEapState
```

当前鉴权状态。

**类型：** [EthEapState](arkts-network-eap-etheapstate-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EthEapStateInfo-state: EthEapState--><!--Device-EthEapStateInfo-state: EthEapState-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap
