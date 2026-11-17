---
kits: ["ArkTS / Ark Programming Language"]
description: "Overview of the positioning and features of the container class library: containers are implemented in a static language, do not support custom properties and methods, provide efficient data access performance, and are divided into linear containers and nonlinear containers, neither of which is thread-safe, helping developers select appropriate containers."
keywords: [container class library, linear container, nonlinear container, data structure, high-performance access, static language implementation, container selection]
doctype: guide
status: active
---

# Overview of the ArkTS Container Library
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:31:51.571Z pushedAt=2026-11-12T03:22:24.554Z nl=1 -->

The container class library is used to store elements of various data types and provides a series of methods for processing data. As a pure data structure container, it features efficient processing capabilities.

The container classes are implemented in a statically typed language, which restricts storage locations and properties and does not support custom properties and methods. This ensures that each data type avoids redundant logic when implementing its functions, thereby achieving efficient data access and improving application performance.

At present, two categories of containers are available: [linear containers](linear-container.md) and [nonlinear containers](nonlinear-container.md). Neither type of container is designed to be thread-safe.
