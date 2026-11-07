# Overview of the ArkTS Container Library
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-11-04T09:15:38.361Z pushedAt=2026-11-04T09:36:12.778Z nl=1 -->

The container class library is used to store elements of various data types and provides a series of methods for processing data. As a pure data structure container, it features efficient processing capabilities.

The container classes are implemented in a statically typed language, which restricts storage locations and properties and does not support custom properties and methods. This ensures that each data type avoids redundant logic when implementing its functions, thereby achieving efficient data access and improving application performance.

At present, two categories of containers are available: [linear containers](linear-container.md) and [nonlinear containers](nonlinear-container.md). Neither type of container is designed to be thread-safe.
