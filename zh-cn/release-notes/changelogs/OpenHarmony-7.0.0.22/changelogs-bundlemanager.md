# 包管理子系统Changelog

## cl.bundlemanager.1 Ability Kit相关公共事件行为变更，增加管控

**访问级别**

公开接口

**变更原因**

Ability Kit部分公共事件中包含应用信息，存在信息泄露的安全风险，需要增加管控。

**变更影响**

此变更涉及应用适配。

对于公共事件[COMMON_EVENT_PACKAGE_ADDED](../../../application-dev/reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_package_added)、[COMMON_EVENT_PACKAGE_REMOVED](../../../application-dev/reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_package_removed)、[COMMON_EVENT_PACKAGE_CHANGED](../../../application-dev/reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_package_changed)、[COMMON_EVENT_PACKAGE_CACHE_CLEARED](../../../application-dev/reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_package_cache_cleared)的订阅方增加了管控。

- 变更前：系统应用和三方应用都可以监听到In-House应用相关事件。

- 变更后：系统应用可以监听In-House应用的相关事件，API版本26.0.0以下三方应用仍然可以监听In-House应用的相关事件，API版本26.0.0及以上三方应用如需监听In-House应用的相关事件则需要对应的In-House应用在app.json5的[allowListenBundleChangedEvent](../../../application-dev/quick-start/app-configuration-file.md)中配置本应用的[appIdentifier](../../../application-dev/quick-start/common-problem-of-application.md#什么是appidentifier)。

**起始 API Level**

9

**变更发生版本**

从OpenHarmony SDK 7.0.0.22版本开始。

**变更的接口/组件**

变更的公共事件列表：
| 事件名称 | 描述 |
| -------- | -------- |
| [COMMON_EVENT_PACKAGE_ADDED](../../../application-dev/reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_package_added) | 应用安装完成的事件。 |
| [COMMON_EVENT_PACKAGE_REMOVED](../../../application-dev/reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_package_removed) | 应用卸载完成的事件。 |
| [COMMON_EVENT_PACKAGE_CHANGED](../../../application-dev/reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_package_changed) | 应用更新完成的事件。 |
| [COMMON_EVENT_PACKAGE_CACHE_CLEARED](../../../application-dev/reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_package_cache_cleared) | 应用缓存数据清理完成的事件。 |


**适配指导**

API版本26.0.0及以上三方应用如需监听In-House应用的相关事件需要对应的In-House应用在app.json5的[allowListenBundleChangedEvent](../../../application-dev/quick-start/app-configuration-file.md)中配置本应用的[appIdentifier](../../../application-dev/quick-start/common-problem-of-application.md#什么是appidentifier)。
