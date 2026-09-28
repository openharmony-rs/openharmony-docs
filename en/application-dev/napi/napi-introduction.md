# Node-API Overview
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @shilei123; @liudachuan3-->
<!--Designer: @shilei123-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=3383cf6b2a36933eae9d88e06bbfad5f09f5363a translatedAt=2026-09-16T03:07:56.759Z pushedAt=2026-09-16T08:19:12.189Z -->

## When to Use

OpenHarmony Node-API is a mechanism extended from the [Node-API](https://nodejs.org/docs/latest-v18.x/api/n-api.html) specification of Node.js 18.x LTS. It provides the interaction capability between ArkTS/JS and C/C++ modules, and offers a set of stable, cross-platform APIs that can be used on different operating systems.

Unless otherwise specified, Node-API in this document refers to OpenHarmony Node-API.

> **NOTE**
>
> For details about the differences between OpenHarmony Node-API and the Node-API specification of Node.js 18.x LTS, see [Node-API](../reference/native-lib/napi.md).

Generally, ArkTS/JS is used for OpenHarmony application development. However, in compute-intensive scenarios, such as games and physical simulations, the existing C/C++ libraries are required to meet the requirements for performance and efficiency. Node-API encapsulates I/O, CPU-intensive, and OS underlying capabilities and exposes these capabilities in the form of C APIs. It uses the C/C++ module registration mechanism to mount properties and methods to ArkTS/JS objects to implement interaction between ArkTS/JS and C/C++. Node-API provides the following benefits:

- The system can open rich module functionalities of the framework layer to ArkTS/JS through the module registration mechanism of Node-API, and open the C/C++ capabilities to the ArkTS/JS layer of applications.

- You can encapsulate core capabilities in C/C++ and use them with ArkTS/JS APIs to improve the execution efficiency of your application.

## Node-API Architecture

**Figure 1** Node-API architecture

![napi_mechanism](figures/napi_mechanism.png)

- Native module: a module developed using Node-API and imported to ArkTS.

- Node-API: implements the logic for interaction between ArkTS and C/C++ code.

- ModuleManager: manages native modules, including loading and locating native modules.

- ScopeManager: manages the lifecycle of **napi_value**.

- ReferenceManager: manages the lifecycle of **napi_ref**.

- Native engine: ArkTS engine abstraction layer, which unifies the API behavior of the ArkTS engine at the Node-API layer.

- ArkCompiler ArkTS Runtime: ArkTS runtime.

## Key Interaction Process of Node-API

**Figure 2** Key interaction process of Node-API

![process_napi](figures/process_napi.png)

The interaction between ArkTS and C++ consists of the following two steps:

1. Initialization: When a native module is imported to ArkTS, the ArkTS engine calls the ModuleManager to load the .so file and dependencies of the module. When the module is loaded for the first time, the module registration is triggered. Then, the method properties defined by the module are embedded to an **exports** object and the object is returned.

2. Invocation: When an ArkTS method is called using the **exports** object, the ArkTS engine locates and calls the embedded C/C++ method.
