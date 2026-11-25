---
kits: ["Ability Kit"]
description: "Lists the common action and entities values in implicit Want and their meanings, and explains that the related capabilities are no longer recommended due to generalized use. It is recommended to launch applications by specified type instead."
keywords: [action, entities, implicit Want, ACTION_HOME, ACTION_VIEW_DATA, ENTITY_BROWSABLE, application launch]
doctype: guide
status: not_recommended
---
# Common action and entities Values (Not Recommended)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @li-weifeng2024-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=a1d9e9480675783d1b3e40efa6d0d69b49968592 translatedAt=2026-11-23T07:47:47.647Z pushedAt=2026-11-24T08:23:15.338Z nl=1 -->

> **NOTE**
>
> Due to the generalized use of the fields **action** and **entities**, the system lacks control over the behavior of applications declaring **action** and **entities**. This loophole allows malicious applications to make false declarations, hijacking traffic and rendering post-redirection features inoperative. As such, the system intends to deprecate unnecessary **action** and **entities**. You are advised to [start an application of the specified type](./start-intent-panel.md).

**action**: indicates the common operation (such as view, share, application details) that the caller wants to perform. In implicit [Want](../reference/apis-ability-kit/js-apis-app-ability-want.md), developers can define this field, in conjunction with uri or parameters, to indicate the operation to perform on the data, such as opening or viewing the uri data. For example, when uri is a URL and action is `ACTION_VIEW_DATA`, then it indicates matching the application component that can access the URL. Declaring the action field in Want indicates that the called application is expected to support the declared operation. Declaring actions in the [skills field](../quick-start/module-configuration-file.md#skills) in the configuration file of the called application indicates that the application supports the declared operation. The common action values are as follows. For specific action values, see [action constant description](../reference/apis-ability-kit/js-apis-ability-wantConstant.md#action).

**Common action values**


- **ACTION_HOME**: action of starting the application entry component. It must be used together with **ENTITY_HOME**. The application icon on the home screen is an explicit entry component. Users can touch the icon to start the entry component. Multiple entry components can be configured for an application.

- **ACTION_CHOOSE**: action of selecting local resource data, such as Contacts and Gallery. Generally, the system has corresponding Picker applications for different types of data.

- **ACTION_VIEW_DATA**: action of viewing data. A website URI indicates the action for opening the website. For details, see [Using startAbility to Start a File Application](./file-processing-apps-startup.md).

- **ACTION_VIEW_MULTIPLE_DATA**: action of launching the UI for sending multiple data records.

The **entities** field specifies the additional category information (such as browser and video player) of the target component. It is a supplement to action in implicit [Want](../reference/apis-ability-kit/js-apis-app-ability-want.md). You can define this field to filter application categories, for example, browser. Declaring the **entities** field in Want indicates that the invoked application should belong to the declared category. The **entities** field under [skills](../quick-start/module-configuration-file.md#skills) in the configuration file indicates the categories supported by the application. Common **entities** values are as follows. For details, see [entity](../reference/apis-ability-kit/js-apis-ability-wantConstant.md#entity).

**Common entities values**


- **ENTITY_DEFAULT**: default category, which is meaningless.

- **ENTITY_HOME**: application components with an icon displayed on the home screen.

- **ENTITY_BROWSABLE**: browser type.