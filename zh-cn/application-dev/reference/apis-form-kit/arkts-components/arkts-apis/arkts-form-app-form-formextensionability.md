# @ohos.app.form.FormExtensionAbility(卡片扩展能力-FormExtensionAbility)

FormExtensionAbility为卡片扩展模块，提供卡片创建、销毁、刷新等生命周期回调。适用于需要在应用中实现卡片功能的场景，帮助开发者快速构建卡片数据更新机制，提升用户与应用的交互体验。

> **说明：**
 >
 > FormExtensionAbility创建后10秒内无操作将会被清理。

## 约束限制

为保障系统安全性和稳定性，防止 FormExtensionAbility 滥用系统资源，系统对其能力进行管控， 不支持以下模块的引用：

- [@ohos.ability.particleAbility (ParticleAbility模块)](../../apis-ability-kit/arkts-apis/arkts-ability-ability-particleability.md)  
 - [@ohos.multimedia.audio (音频管理)](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md)  
 - [@ohos.multimedia.camera (相机管理)](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md)  
 - [@ohos.multimedia.media (媒体服务)](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media.md)  
 -[@ohos.resourceschedule.backgroundTaskManager (后台任务管理)](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-resourceschedule-backgroundtaskmanager.md)

## 导入模块

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [FormExtensionAbility](arkts-form-app-form-formextensionability-formextensionability-c.md) | 卡片扩展类。包含卡片提供方接收创建卡片、修改可见性等的通知接口。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FormExtensionAbility](arkts-form-app-form-formextensionability-formextensionability-c-sys.md) | 卡片扩展类。包含卡片提供方接收创建卡片、修改可见性等的通知接口。 |
<!--DelEnd-->
