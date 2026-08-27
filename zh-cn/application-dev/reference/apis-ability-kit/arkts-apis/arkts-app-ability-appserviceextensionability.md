# @ohos.app.ability.AppServiceExtensionAbility

AppServiceExtensionAbility模块提供后台服务相关扩展能力，包括后台服务的创建、销毁、连接、断开等生命周期回调。适用于需要长时间执行后台任务或维持后台连接的场景，
 例如后台流量监控行为，能够帮助应用提升后台服务的持续运行能力。
 > **说明：**
 >
 > 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
 >
 > 本模块接口仅可在Stage模型下使用。
 ## 约束限制
 - 当前仅支持PC/2in1设备。
 - 应用集成AppServiceExtensionAbility的组件需要申请ACL权限（ohos.permission.SUPPORT_APP_SERVICE_EXTENSION）。该ACL权限当前只对企业普通应用开放申请，申请方
 式参考权限申请指导。
 - 为保障系统安全性和稳定性，防止AppServiceExtensionAbility滥用系统资源，系统对其能力进行管控，不支持@ohos.window (窗口)。
 ## 生命周期
 AppServiceExtensionAbility提供了[onCreate()](arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md#oncreate)、
 [onRequest()](arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md#onrequest)、[onConnect()](arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md#onconnect)和
 [onDestroy()](arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md#ondestroy)生命周期回调，开发者可根据需要重写对应的回调方法。下图展示了AppServiceExtensionAbility的生命
 周期。
 
 - **onCreate**
 在AppServiceExtensionAbility实例创建时，系统会触发该回调。
 - **onDestroy**
 在AppServiceExtensionAbility实例销毁时，系统会触发该回调。
 - **onRequest**
 调用方使用startAppServiceExtensionAbility()拉起AppServiceExtensionAbility实例时，系统会触发该回调。
 - **onConnect**
 调用方使用connectAppServiceExtensionAbility连接AppServiceExtensionAbility实例时，系统会触发该回调。
 - **onDisconnect**
 当所有连接方断开与AppServiceExtensionAbility实例的连接时，系统会触发该回调。


## 导入模块

```TypeScript
import { AppServiceExtensionAbility } from '@kit.AbilityKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AppServiceExtensionAbility](arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md) | AppServiceExtensionAbility模块提供后台服务相关扩展能力，包括后台服务的创建、销毁、连接、断开等生命周期回调。 |
