---
kits: ["Ability Kit"]
description: "Describes how to construct an explicit Want by specifying bundleName and abilityName to start the target UIAbility component within the application to complete a specific task."
keywords: [explicit Want, UIAbility, in-app start, abilityName, bundleName, component start]
doctype: guide
status: active
---
# Using Explicit Want to Start an Application Component

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @li-weifeng2024-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=a1d9e9480675783d1b3e40efa6d0d69b49968592 translatedAt=2026-11-23T07:44:36.672Z pushedAt=2026-11-24T08:03:31.427Z nl=1 -->

When a user touches a button in an application, the application often needs to start a UIAbility component to complete a specific task. If the **abilityName** and **bundleName** parameters are specified when starting a UIAbility, then the explicit Want is used.

The user touches a button in the application to start the UIAbility component to complete a specific task. To start the UIAbility component in explicit Want mode, the **abilityName** and **bundleName** parameters must be specified. For details, see [Starting UIAbility in the Same Application](uiability-intra-device-interaction.md).
