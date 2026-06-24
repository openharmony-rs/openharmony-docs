# @ohos.commonEvent

本模块提供了公共事件的能力，包括公共事件的权限列表，发布公共事件，订阅或取消订阅公共事件，获取或修改公共事件结果代码、结果数据等。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [commonEventManager:commonEventManager](../../apis-basic-service-kit/arkts-apis/arkts-commoneventmanager.md#commonEventManager)

**系统能力：** SystemCapability.Notification.CommonEvent

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createSubscriber](arkts-api10lessdeprecatedmodules-commonevent-createsubscriber-f.md#createSubscriber-1) | 以回调形式创建订阅者。<br/> |
| [createSubscriber](arkts-api10lessdeprecatedmodules-commonevent-createsubscriber-f.md#createSubscriber-2) | 以Promise形式创建订阅者。<br/> |
| [publish](arkts-api10lessdeprecatedmodules-commonevent-publish-f.md#publish-1) | 发布公共事件（回调形式）。<br/> |
| [publish](arkts-api10lessdeprecatedmodules-commonevent-publish-f.md#publish-2) | 以回调的形式发布公共事件。<br/> |
| <!--DelRow-->[publishAsUser](arkts-api10lessdeprecatedmodules-commonevent-publishasuser-f-sys.md#publishAsUser-1) | 以回调的形式向指定用户发布公共事件。<br/> |
| <!--DelRow-->[publishAsUser](arkts-api10lessdeprecatedmodules-commonevent-publishasuser-f-sys.md#publishAsUser-2) | 以回调形式向指定用户发布公共事件并指定发布信息。<br/> |
| [subscribe](arkts-api10lessdeprecatedmodules-commonevent-subscribe-f.md#subscribe-1) | 以回调形式订阅公共事件。<br/> |
| [unsubscribe](arkts-api10lessdeprecatedmodules-commonevent-unsubscribe-f.md#unsubscribe-1) | 以回调形式取消订阅公共事件。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Support](arkts-api10lessdeprecatedmodules-commonevent-support-e.md) | 系统公共事件是指由系统服务或系统应用发布的事件，订阅这些系统公共事件需要特定的权限。<br/> |

