# @ohos.FusionConnectivity.PartnerAgentExtensionContext (设备状态通知能力上下文)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

PartnerAgentExtensionContext模块是三方外设的发现和连接管理功能的上下文，提供外设发现、配对连接、状态通知等能力，适用于应用需要接入和管理第三方外设并获取其状态信息的场景，帮助开发者统一管理外设的连接生命周期。

> **说明**
>
> - 本模块接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 仅可在Stage模型下使用。

## 导入模块

```ts
import { PartnerAgentExtensionContext } from '@kit.ConnectivityKit';
```

## PartnerAgentExtensionContext

PartnerAgentExtensionContext模块是三方外设的发现和连接管理功能的上下文，继承自ExtensionContext类，提供了PartnerAgentExtensionAbility的相关上下文。该上下文为三方外设的发现与连接管理提供运行环境及能力入口，具体的发现策略、连接流程及接口使用方式请参见相关接口说明。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**： 此接口仅可在Stage模型下使用。
