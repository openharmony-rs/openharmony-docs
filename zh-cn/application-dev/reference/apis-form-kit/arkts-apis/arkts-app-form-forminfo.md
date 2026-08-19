# @ohos.app.form.formInfo

formInfo模块提供了卡片信息和状态等相关类型和枚举。 > **说明：** > > 当前页面仅包含本模块的系统接口，其他公共接口参见[@ohos.app.form.formInfo (formInfo)](#ohosappformforminfo)。

**起始版本：** 23

<!--Device-unnamed-declare namespace formInfo--><!--Device-unnamed-declare namespace formInfo-End-->

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [FormInfo](arkts-form-forminfo-forminfo-i.md) | 卡片配置信息。 |
| [FormInfoFilter](arkts-form-forminfo-forminfofilter-i.md) | 卡片信息过滤器，仅将符合过滤器内要求的卡片信息返回。 |
| [FormStateInfo](arkts-form-forminfo-formstateinfo-i.md) | 卡片状态信息。 |
| [OverflowInfo](arkts-form-forminfo-overflowinfo-i.md) | 互动卡片动效信息。 |
| [Rect](arkts-form-forminfo-rect-i.md) | 通用矩形区域信息。可用于描述卡片坐标区域、互动卡片动效区域等信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ChangeSceneAnimationStateRequest](arkts-form-forminfo-changesceneanimationstaterequest-i-sys.md) | 互动卡片状态切换请求信息。互动卡片状态分为激活态和非激活态，非激活态下，互动卡片同普通卡片一致；激活态下，互动卡片支持拉起卡片提供方所开发的LiveFormExtensionAbility进程，实现互动卡片动效。 |
| [FormCustomConfig](arkts-form-forminfo-formcustomconfig-i-sys.md) | 卡片自定义配置信息。 |
| [FormInfo](arkts-form-forminfo-forminfo-i-sys.md) | 卡片配置信息。 |
| [FormInfoFilter](arkts-form-forminfo-forminfofilter-i-sys.md) | 卡片信息过滤器，仅将符合过滤器内要求的卡片信息返回。 |
| [FormProviderFilter](arkts-form-forminfo-formproviderfilter-i-sys.md) | Information about a running form. |
| [FunInteractionParams](arkts-form-forminfo-funinteractionparams-i-sys.md) | 趣味交互卡片配置参数。 |
| [OverflowRequest](arkts-form-forminfo-overflowrequest-i-sys.md) | 互动卡片动效请求信息。 |
| [PublishFormCrossBundleInfo](arkts-form-forminfo-publishformcrossbundleinfo-i-sys.md) | 跨应用加卡管控信息。 |
| [PublishFormResult](arkts-form-forminfo-publishformresult-i-sys.md) | 发布卡片加桌结果。 |
| [RunningFormInfo](arkts-form-forminfo-runningforminfo-i-sys.md) | 已经添加到桌面的卡片信息。 |
| [SceneAnimationParams](arkts-form-forminfo-sceneanimationparams-i-sys.md) | 场景动效卡片配置参数。 |
| [TemplateFormDetailInfo](arkts-form-forminfo-templateformdetailinfo-i-sys.md) | 模板卡对应的真实卡片信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ColorMode](arkts-form-forminfo-colormode-e.md) | 卡片主题样式统一跟随系统的颜色模式，卡片支持的颜色模式枚举。 |
| [FormDimension](arkts-form-forminfo-formdimension-e.md) | 定义卡片尺寸枚举。 |
| [FormLocation](arkts-form-forminfo-formlocation-e.md) | 卡片当前位置枚举。 |
| [FormParam](arkts-form-forminfo-formparam-e.md) | 卡片参数枚举。 |
| [FormShape](arkts-form-forminfo-formshape-e.md) | 定义卡片形状枚举。 |
| [FormState](arkts-form-forminfo-formstate-e.md) | 卡片状态枚举。 |
| [FormType](arkts-form-forminfo-formtype-e.md) | 支持的卡片类型枚举。JS卡片使用Web技术实现，适合简单的展示类卡片；ArkTS卡片使用ArkTS语言开发，支持更丰富的交互和动画效果。开发时应根据卡片复杂度和交互需求选择合适类型。 |
| [FormUpdateReason](arkts-form-forminfo-formupdatereason-e.md) | 卡片更新原因枚举。 |
| [LaunchReason](arkts-form-forminfo-launchreason-e.md) | 卡片创建原因枚举。 |
| [VisibilityType](arkts-form-forminfo-visibilitytype-e.md) | 卡片当前可见类型枚举。表示卡片在宿主界面上的可见状态，当卡片从桌面移入/移出屏幕或切换应用时状态会发生变化，开发者可据此优化卡片刷新策略。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FormLocation](arkts-form-forminfo-formlocation-e-sys.md) | 卡片当前位置枚举。 |
| [FormParam](arkts-form-forminfo-formparam-e-sys.md) | 卡片参数枚举。 |
| [FormUsageState](arkts-form-forminfo-formusagestate-e-sys.md) | 卡片当前使用状态枚举。 |
| [PublishFormErrorCode](arkts-form-forminfo-publishformerrorcode-e-sys.md) | 发布卡片加桌错误码枚举。 |
| [RenderingMode](arkts-form-forminfo-renderingmode-e-sys.md) | 卡片支持的渲染模式枚举。 |
| [SceneAnimationTriggerType](arkts-form-forminfo-sceneanimationtriggertype-e-sys.md) | 场景动效卡片触发类型枚举。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeleteFormsCallback](arkts-form-forminfo-deleteformscallback-t-sys.md) | 卡片删除回调。 |
| [GetFormRectInfoCallback](arkts-form-forminfo-getformrectinfocallback-t-sys.md) | 卡片位置、尺寸查询回调。使用Promise异步回调。 |
| [GetLiveFormStatusCallback](arkts-form-forminfo-getliveformstatuscallback-t-sys.md) | Get live form status info callback |
| [GetWantParamsCallback](arkts-form-forminfo-getwantparamscallback-t-sys.md) | 获取卡片参数回调。 |
| [PublishFormCrossBundleControlCallback](arkts-form-forminfo-publishformcrossbundlecontrolcallback-t-sys.md) | 跨应用加卡管控回调。 |
| [TemplateFormDetailInfoCallback](arkts-form-forminfo-templateformdetailinfocallback-t-sys.md) | 模板卡真实卡片信息回调。 |
| [UpdateFormsConfigCallback](arkts-form-forminfo-updateformsconfigcallback-t-sys.md) | 卡片配置更新回调。 |
<!--DelEnd-->

