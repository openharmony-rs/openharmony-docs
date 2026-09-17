# @ohos.app.form.formProvider(formProvider)

formProvider模块提供了获取卡片信息、更新卡片、设置卡片刷新时间等能力。该模块作为卡片提供方与卡片管理服务的桥梁，通过IPC机制与FormExtension进行通信，实现卡片的更新、信息获取等操作。适用于卡片提供方需要主动更新卡片内容、管理卡片生命周期、获取卡片运行状态等场景，帮助开发者实现卡片的动态更新和状态管理。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [cancelOverflow](arkts-form-formprovider-canceloverflow-f.md) | 卡片提供方发起取消互动卡片动效请求，只针对[场景动效类型互动卡片](../../../form/arkts-ui-widget-configuration.md#sceneanimationparams标签)生效，使用Promise异步回调。 |
| [closeFormEditAbility](arkts-form-formprovider-closeformeditability-f.md) | 关闭卡片编辑页。适用于卡片编辑完成或取消编辑的场景，例如用户完成参数配置后关闭编辑页、取消编辑操作等。 |
| [getFormRect](arkts-form-formprovider-getformrect-f.md) | 查询卡片位置、尺寸，使用Promise异步回调。适用于需要获取卡片在屏幕上的位置和尺寸信息的场景，例如卡片动效、位置校准、布局计算等。 |
| [getFormsInfo](arkts-form-formprovider-getformsinfo-f.md) | 获取设备上当前应用程序的卡片信息，并筛选符合条件的信息，使用callback异步回调。 |
| [getFormsInfo](arkts-form-formprovider-getformsinfo-f.md) | 获取设备上当前应用程序的卡片信息，使用callback异步回调。适用于卡片管理、调试、统计等场景，例如查看应用所有卡片配置信息、统计卡片数量等。 |
| [getFormsInfo](arkts-form-formprovider-getformsinfo-f.md) | 获取设备上当前应用符合条件的卡片信息，使用Promise异步回调。 |
| [getPublishedFormInfoById](arkts-form-formprovider-getpublishedforminfobyid-f.md) | 获取设备上当前应用程序已添加到桌面的指定卡片信息，使用Promise异步回调。 |
| [getPublishedFormInfos](arkts-form-formprovider-getpublishedforminfos-f.md) | 获取设备上当前应用所有已添加到桌面的卡片信息，使用Promise异步回调。 |
| [getPublishedRunningFormInfoById](arkts-form-formprovider-getpublishedrunningforminfobyid-f.md) | 获取当前应用已加桌的指定卡片信息，使用Promise异步回调。适用于卡片管理、调试等场景，例如查看指定卡片的位置信息和尺寸信息。 |
| [getPublishedRunningFormInfos](arkts-form-formprovider-getpublishedrunningforminfos-f.md) | 获取所有已加桌的卡片信息，使用Promise异步回调。适用于卡片管理、批量操作、统计等场景，例如查看应用所有已添加到桌面的卡片信息、批量更新卡片状态等。 |
| [openFormEditAbility](arkts-form-formprovider-openformeditability-f.md) | 打开卡片编辑页。适用于需要用户配置卡片参数的场景，例如设置卡片显示内容、选择数据源、配置更新频率等。 |
| [openFormManager](arkts-form-formprovider-openformmanager-f.md) | 打开当前应用的卡片管理页面。适用于卡片管理场景，例如预览当前应用所有可以加桌的卡片、添加卡片到负一屏或桌面等。 |
| [reloadAllForms](arkts-form-formprovider-reloadallforms-f.md) | 在应用主进程通过本接口可以通知FormExtension进程批量更新当前应用下已经加桌的所有卡片，仅支持在[UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md)中调用，使用Promise异步回调。 |
| [reloadForms](arkts-form-formprovider-reloadforms-f.md) | 对于当前应用中moduleName、abilityName、formName相同的卡片，每次加桌会分配不同的卡片ID。卡片提供方可通过本接口批量更新这些卡片。与reloadAllForms相比，本接口可精确指定更新特定配置的卡片，适用于仅需更新特定卡片场景；reloadAllForms更新当前应用所有已加桌卡片，适用于全局刷新场景。本接口在应用主进程中调用，通知FormExtension进程进行批量更新，仅支持在[UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md)中使用，使用Promise异步回调。 |
| [requestOverflow](arkts-form-formprovider-requestoverflow-f.md) | 卡片提供方发起互动卡片动效请求，只针对[场景动效类型互动卡片](../../../form/arkts-ui-widget-configuration.md#sceneanimationparams标签)生效，使用Promise异步回调。其中相关的方法为[cancelOverflow()](arkts-form-formprovider-canceloverflow-f.md)：取消互动卡片动效请求，用于取消已发起的动效。 |
| [setFormNextRefreshTime](arkts-form-formprovider-setformnextrefreshtime-f.md) | 设置指定卡片的下一次刷新时间，使用callback异步回调。适用于需要精确控制卡片刷新时机的场景，例如定时任务等。 |
| [setFormNextRefreshTime](arkts-form-formprovider-setformnextrefreshtime-f.md) | 设置指定卡片的下一次刷新时间，使用Promise异步回调。适用于需要精确控制卡片刷新时机的场景，例如定时任务等。 |
| [updateForm](arkts-form-formprovider-updateform-f.md) | 更新指定的卡片，使用callback异步回调。适用于卡片数据变化时主动更新卡片内容的场景，例如天气数据变化、股票价格更新、任务进度更新等。 |
| [updateForm](arkts-form-formprovider-updateform-f.md) | 更新指定的卡片，使用Promise异步回调。适用于卡片数据变化时主动更新卡片内容的场景，例如天气数据变化、股票价格更新、任务进度更新等。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [activateSceneAnimation](arkts-form-formprovider-activatesceneanimation-f-sys.md) | 互动卡片请求状态切换到激活态，只针对[场景动效类型互动卡片](../../../form/arkts-ui-widget-configuration.md#sceneanimationparams标签)生效，使用Promise异步回调。互动卡片状态分为激活态和非激活态，非激活态下，互动卡片同普通卡片一致；激活态下，互动卡片支持拉起卡片提供方所开发的LiveFormExtensionAbility进程，实现互动卡片动效。 |
| [deactivateSceneAnimation](arkts-form-formprovider-deactivatesceneanimation-f-sys.md) | 互动卡片请求切换到非激活态，只针对[场景动效类型互动卡片](../../../form/arkts-ui-widget-configuration.md#sceneanimationparams标签)生效，使用Promise异步回调。互动卡片状态分为激活态和非激活态，非激活态下，互动卡片同普通卡片一致；激活态下，互动卡片支持拉起卡片提供方所开发的LiveFormExtensionAbility进程，实现互动卡片动效。 |
| [isRequestPublishFormSupported](arkts-form-formprovider-isrequestpublishformsupported-f-sys.md) | 查询是否可以发布卡片到卡片使用方，使用callback异步回调。 |
| [isRequestPublishFormSupported](arkts-form-formprovider-isrequestpublishformsupported-f-sys.md) | 查询是否可以发布卡片到卡片使用方，使用Promise异步回调。 |
| [offPublishFormCrossBundleControl](arkts-form-formprovider-offpublishformcrossbundlecontrol-f-sys.md) | 取消订阅跨应用加桌管控。 |
| [onPublishFormCrossBundleControl](arkts-form-formprovider-onpublishformcrossbundlecontrol-f-sys.md) | 订阅跨应用加桌管控。 |
| [openFormManagerCrossBundle](arkts-form-formprovider-openformmanagercrossbundle-f-sys.md) | Open the view of forms belonging to the specified bundle. Client to communication with FormManagerService. |
| [requestPublishForm](arkts-form-formprovider-requestpublishform-f-sys.md) | 请求发布一张卡片到使用方。使用方通常为桌面，使用callback异步回调。 |
| [requestPublishForm](arkts-form-formprovider-requestpublishform-f-sys.md) | 请求发布一张卡片到使用方。使用方通常为桌面，使用callback异步回调。 |
| [requestPublishForm](arkts-form-formprovider-requestpublishform-f-sys.md) | 请求发布一张卡片到使用方。使用方通常为桌面，使用Promise异步回调。 |
| [updateTemplateFormDetailInfo](arkts-form-formprovider-updatetemplateformdetailinfo-f-sys.md) | 更新当前设备上指定的模板卡片静态配置信息。使用Promise异步回调。 |
<!--DelEnd-->
