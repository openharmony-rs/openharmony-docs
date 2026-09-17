# @ohos.app.form.LiveFormExtensionAbility(LiveFormExtensionAbility)

## 导入模块

```TypeScript
import { LiveFormExtensionAbility, LiveFormInfo } from '@kit.FormKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [LiveFormExtensionAbility](arkts-form-app-form-liveformextensionability-liveformextensionability-c.md) | 互动卡片扩展类，用于实现互动卡片的提供方功能。包含互动卡片提供方接收创建和销毁互动卡片的通知接口，开发者可在这些回调中实现卡片的初始化、数据绑定、资源清理等逻辑。[onLiveFormCreate](arkts-form-app-form-liveformextensionability-liveformextensionability-c.md#onliveformcreate)在用户切换互动卡片状态为激活态时触发，用于初始化和数据绑定；[onLiveFormDestroy](arkts-form-app-form-liveformextensionability-liveformextensionability-c.md#onliveformdestroy)在用户切换互动卡片状态为非激活态时触发，用于资源清理。两者形成完整的生命周期管理，应确保在create中分配的资源在destroy中正确释放。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [LiveFormInfo](arkts-form-app-form-liveformextensionability-liveforminfo-i.md) | 互动卡片信息。 |
