---
kits: ["ArkTS Kit"]
description: "Explains how to request the restricted ACL permission ohos.permission.kernel.ALLOW_EXECUTABLE_FORT_MEMORY required for JSVM JIT, including the AGC application process, profile certificate updates, and adaptation precautions."
keywords: ["JIT permission","ACL","ALLOW_EXECUTABLE_FORT_MEMORY","profile certificate","AGC","app marketplace","permission request","JSVM"]
doctype: guide
status: active
---

# Requesting the JIT Profile for JSVM-API
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=1bcf41641a10f17d0f56bfc82362dc9488eaf7eb translatedAt=2026-11-09T08:52:17.288Z nl=1 -->

Just In Time (JIT) compilation introduces the security risk of arbitrary code injection. To protect app security and maintain the pure HarmonyOS ecosystem, the system disables the JSVM JIT feature by default. If you need to use this feature, you must submit an application for the restricted ACL permission `ohos.permission.kernel.ALLOW_EXECUTABLE_FORT_MEMORY` to the app marketplace (AppGallery Connect), and describe the specific scenarios in which the JSVM engine's JIT feature will be used in the supplementary materials. After the permission is approved, you can update the profile certificate from the AppGallery Connect website, and then repackage and release the app. For the permission application and adaptation process, see *[Requesting Restricted Permissions](../security/AccessToken/declare-permissions-in-acl.md)*.


## Precautions
1. If the permission certificate is not applied for but the permission is declared in the configuration file, the application installation will fail.
2. If the error "The ohos.permission.kernel.ALLOW_EXECUTABLE_FORT_MEMORY permission under requestPermissions must be a value that is predefined within the SDK or a custom one that you have included under definePermissions." is displayed during the compilation process, update the OpenHarmony SDK to the latest version (5.0.2.125 or later).
3. When Secure Shield mode is enabled, the operating system disables the JIT functionality globally. This restriction applies to all applications, including privileged applications that have obtained the ACL permission. For details, see [JSVM-API Secure Shield Mode](jsvm-secure-shield-mode.md).
