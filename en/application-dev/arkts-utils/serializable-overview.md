---
kits: ["ArkTS"]
description: "Overview of the types and characteristics of inter-thread communication objects: the transfer methods and applicable scenarios of ordinary objects, container class objects, ArrayBuffer, SharedArrayBuffer, Transferable objects, and Sendable objects, as well as constraints such as the 16MB limit for a single serialization, to guide the selection of communication objects."
keywords: [inter-thread communication objects, ordinary objects, container class objects, ArrayBuffer, SharedArrayBuffer, Transferable objects, Sendable objects, serialization limit, multithreading]
doctype: guide
status: active
---

# Overview of Inter-Thread Communication Objects
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:44:39.553Z pushedAt=2026-11-12T09:16:04.116Z nl=1 -->

In multithreaded concurrency scenarios, such as creating background threads via TaskPool or Worker, data interaction between different threads is necessary. Due to memory isolation between threads, inter-thread communication objects must implement value copying or memory sharing through serialization.

> **NOTE**
>
> - A maximum of 16 MB data can be serialized at a time.
> - Serialization does not support complex types decorated with decorators such as [@State](../ui/state-management/arkts-state.md), [@Prop](../ui/state-management/arkts-prop.md), and [@Link](../ui/state-management/arkts-link.md).

Currently, ArkTS supports the following types of objects for inter-thread communication:

- [Regular objects](normal-object.md): ArkTS supports direct passing of basic data types and custom objects (which must comply with serialization specifications).
- [Container objects](container-object.md): ArkTS supports direct passing of container objects (which must comply with serialization specifications).
- [ArrayBuffer objects](arraybuffer-object.md): used for efficient transmission of binary data, suitable for large segments of contiguous memory data (such as image or audio raw data).
- [SharedArrayBuffer objects](shared-arraybuffer-object.md): ArkTS supports shared memory across multiple threads, allowing direct access to the same memory area between threads, enhancing data transfer efficiency.
- [Transferable objects (NativeBinding objects)](transferabled-object.md): ArkTS supports transferring object ownership across threads (such as file descriptors and graphics resources), after which the original thread no longer has access rights.
- [Sendable objects](arkts-sendable.md): Shareable objects that conform to the ArkTS language specification. For supported data types, see [Sendable supported data types](arkts-sendable.md#sendable-data-types). They must satisfy the Sendable constraints. For details, see [Sendable usage rules and constraints](sendable-constraints.md).
