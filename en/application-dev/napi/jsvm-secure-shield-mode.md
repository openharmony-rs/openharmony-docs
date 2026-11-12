---
kits: ["ArkTS Kit"]
description: "Describes the functional restrictions of JSVM Secure Shield mode and how to enable it. Designed for users with high security requirements, this mode globally disables JIT and WebAssembly. The guide also explains how to assess app compatibility and performance in this mode."
keywords: ["Secure Shield mode","JSVM","JIT","WebAssembly","security restrictions","functional restrictions","compatibility assessment"]
doctype: guide
status: active
---

# JSVM-API Secure Shield Mode
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=1bcf41641a10f17d0f56bfc82362dc9488eaf7eb translatedAt=2026-11-09T08:52:17.301Z nl=1 -->

The Secure Shield mode is a system-level security protection solution designed for users with high security requirements. This mode strictly restricts functionalities to significantly enhance system security and effectively defend against threats through the remote attack surface. In Secure Shield mode, the functionalities of JSVM are restricted. You need to evaluate the application availability in Secure Shield mode.

## Enabling Secure Shield Mode

To enable Secure Shield mode, perform the following steps:
1. Go to system settings on your phone.
2. Tap **Privacy and security**.
3. Tap **Secure Shield mode** and enable it.

## Functionality Restrictions in Shield Guard Mode

To reduce the risk of JSVM attacks, Secure Shield mode will implement the following key security restrictions:
- All Just-In-Time (JIT) compilation functionalities are disabled, including those for apps that have obtained ACL permissions.
- WebAssembly support is suspended (WebAssembly in the current version depends on JIT).

## Application Compatibility Evaluation

When running an application in Secure Shield mode, you are advised to perform the following compatibility checks:
1. JavaScript performance evaluation:
    - Test the running efficiency of the app in the restricted environment.
    - Optimize possible performance bottlenecks.

2. WebAssembly compatibility check:
    - Static code analysis: Check the WebAssembly API calls in the project and the Wasm dependency of the third-party library.
    - Runtime verification: Perform full-functionality tests in Secure Shield mode.