# OS Account Privilege List

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @pan9f-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=e69ec64ac858719fcfee7d95c940787db87ff304 translatedAt=2026-09-23T02:04:31.088Z pushedAt=2026-09-23T10:54:51.525Z -->

The following table lists the privileges that can be granted by the OS account authorization module.

> **NOTE**
>
> Whether a privilege is available depends on whether it has been deployed in the current OS version. If the OS version does not contain the privilege configuration, [AUTHORIZATION_NOT_SUPPORTED](js-apis-osAccount-authorization.md#authorizationresultcode) will be returned when [authorization.getAuthorizationManager().requestAuthorization](js-apis-osAccount-authorization.md#requestauthorization) is called.

| Privilege                                      | Privilege Value                                   | Description                           | Validity Period                           | Associated Permissions                           |
| ----------------------------------------- | ---------------------------------------- | ------------------------------ |------------------------------ |------------------------------ |
| ohos.privilege.operate_raw_net_packets | PRIVILEGE_OPERATE_RAW_NET_PACKETS        | Privilege to operate raw network packets. | Lifecycle of the authorized process. | ohos.permission.kernel.NET_RAW |
