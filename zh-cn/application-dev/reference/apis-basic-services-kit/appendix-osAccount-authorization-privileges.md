# 系统账号特权列表

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @pan9f-->
<!--Adviser: @zengyawen-->

下表内容为系统账号授权模块可授权的特权。

> **说明：**
>
> 特权的可用性取决于当前系统版本是否已部署该特权的配置。若系统版本未包含该特权配置，调用[authorization.getAuthorizationManager().requestAuthorization](js-apis-osAccount-authorization.md#requestauthorization)时将返回[AUTHORIZATION_NOT_SUPPORTED](js-apis-osAccount-authorization.md#authorizationresultcode)。

| 特权                                      | 特权值                                   | 说明                           |有效期                           |关联的权限                           |
| ----------------------------------------- | ---------------------------------------- | ------------------------------ |------------------------------ |------------------------------ |
| ohos.privilege.operate_raw_net_packets | PRIVILEGE_OPERATE_RAW_NET_PACKETS        | 操作原始网络包的特权。 |与被授权进程的生命周期相绑定| ohos.permission.kernel.NET_RAW|
