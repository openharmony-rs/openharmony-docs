# BusinessCapability

描述设备支持的业务功能。

**起始版本：** 23

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## 导入模块

```TypeScript
import { partnerAgent } from '@kit.ConnectivityKit';
```

## supportMediaControl

```TypeScript
supportMediaControl?: boolean
```

该设备是否支持媒体控制功能，例如控制媒体播放、音量调节、上一首和下一首等功能。true表示支持，false表示不支持。未指定默认为false。

注意：

supportMediaControl和supportTelephonyControl均选择false时，设备发现时不会拉起[PartnerAgentExtensionAbility](arkts-connectivity-fusionconnectivity-partneragentextensionability-partneragentextensionability-c.md)进程。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

## supportTelephonyControl

```TypeScript
supportTelephonyControl?: boolean
```

该设备是否支持通话控制功能，如接听和挂断电话。 true表示支持，false表示不支持。未指定默认为false。

注意：

supportMediaControl和supportTelephonyControl均选择false时，设备发现时不会拉起[PartnerAgentExtensionAbility](arkts-connectivity-fusionconnectivity-partneragentextensionability-partneragentextensionability-c.md)进程。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core
