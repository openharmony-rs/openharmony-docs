# 包管理子系统Changelog

## cl.bundlemanager.1 新增默认浏览器权限

**访问级别**

公共能力

**变更原因**

为避免非专业或低安全性应用引发的安全风险与体验割裂，鸿蒙系统通过引入权限管控机制对默认浏览器生态进行规范。该机制从安全、隐私及用户体验三个维度设定了严格的准入标准，旨在全面保障并提升用户的网络浏览体验。

**变更影响**

变更前：
1. 只要声明支持打开HTTP协议即可展示在默认浏览器备选列表并且可以被设置为默认浏览器。

变更后：
1. 需要申请默认浏览器权限（ohos.permission.DEFAULT_WEB_BROWSER）才可以展示在默认浏览器备选列表。
2. 具备默认浏览器权限的应用才可以被设置为默认浏览器。

**起始 API Level**

26.1.0

**变更发生版本**

从OpenHarmony SDK 7.0.0.45开始。

**变更的接口/组件**

不涉及

**适配指导**

如果有称为默认浏览器的诉求，需要按照受限权限申请指导进行默认浏览器权限（ohos.permission.DEFAULT_WEB_BROWSER）申请。

受限权限申请指导：https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/declare-permissions-in-acl

可申请默认浏览器权限的特殊场景和功能：

默认浏览器权限面向浏览器类应用，用于将应用设置为系统默认浏览器，接管系统及第三方应用发出的网页链接打开请求，统一管理网页内容的跳转与展示。

仅满足浏览器品类标准，并通过安全、隐私、用户体验三项审核的应用方可申请此权限。

申请后AGC的审核时长：预计3个工作日内反馈审核结果。

权限授权后，在配置文件中[声明权限](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/declare-permissions)
