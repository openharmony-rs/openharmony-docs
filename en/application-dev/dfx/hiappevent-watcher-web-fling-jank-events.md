# ArkWeb Fling Jank Event Overview

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @pxlstrong-->
<!--Designer: @pxlstrong-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Introduction
[ArkWeb](../web/web-component-overview.md) provides **Web** components for displaying web page content in applications, enabling you to control web pages. Page scrolling consists of two phases: dragging and flinging. Dragging refers to the scrolling when you touch the screen. Flinging refers to the page scrolling at a certain speed after your finger leaves the screen. Since API version 23, the ArkWeb fling jank events can be subscribed to. If a user scrolls the web page on an application and frame loss occurs and lasts for more than 50 ms, the ArkWeb fling jank event is triggered and related frame loss data is generated.

This topic describes the ArkWeb fling jank event detection principles, fields, and specifications. For details about how to use the HiAppEvent APIs to subscribe to ArkWeb fling jank events, see the following documents:

- [Subscribing to ArkWeb Fling Jank Events (ArkTS)](hiappevent-watcher-web-fling-jank-events-arkts.md)

> **NOTE**
>
> ArkWeb fling jank events provide only the **web_id** of the **Web** component where frame freeze occurs, the maximum frame loss duration, and other related data. You can use **web_id** to obtain the URL of the web page where frame loss occurs by referring to the sample code in "Subscribing to ArkWeb Fling Jank Events (ArkTS)". Then, use [DevTools](../web/web-debugging-with-devtools.md) to reproduce the problem and locate the root cause.
>
> Since API version 23, ArkWeb fling jank events can be subscribed to using HiAppEvent in [application clones](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/app-clone), atomic services, and [input method applications](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/inputmethod-application-guide).

## Detection Principles

After the rendering and drawing are complete, ArkWeb generates a buffer and sends it to the graphics buffer. The graphics side obtains the buffer and displays it. During the flinging phase, the time difference between the two buffer exchanges between ArkWeb and the graphics side is checked to determine whether a timeout occurs and whether frame loss occurs on the ArkWeb side.

## params

The following table describes the **params** property of the ArkWeb fling jank events.

| Name| Type| Description|
| -------- | -------- | -------- |
| start_time | number | Start time of the fling effect, which is a timestamp.|
| duration | number | Duration of the fling effect, in ms.|
| web_id | number | Web ID of the component where frame loss occurs.|
| max_app_frame_time | number | Maximum duration of consecutive frame loss during the fling effect, in ms.|
