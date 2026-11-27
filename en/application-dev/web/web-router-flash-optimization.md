---
kits: ["ArkWeb Kit"]
description: "Describes how to set the Web component background color to match the web page background color, eliminating the bottom flicker during Navigation routing redirection to a Web page."
keywords: [page flicker, Web component, Web component background color, Navigation, routing redirection, backgroundColor, system navigation bar]
doctype: guide
status: active
---

# Mitigating Page Flickering When Navigating to a New Web Component
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @wangxinbao01-->
<!--Designer: @defeng20201-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d8274331dc7d9141ea5823ca830b176bf16e74e4 translatedAt=2026-11-27T08:28:41.976Z pushedAt=2026-11-27T09:20:44.616Z nl=2 -->

When an app uses a router such as [Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md) to navigate to a **Web** component page, flickering may occur at the bottom of the page during web page loading, which affects user experience.

## Causes

When a router such as the **Navigation** component is used to navigate to a **Web** component page, the application determines whether to hide the system navigation bar based on the callback notification of the web page. If it decides to hide the system navigation bar, the layout of the **Web** component is adjusted accordingly. The layout adjustment process can be simplified into the following four phases:

![web-router-flash-optimization.png](figures/web-router-flash-optimization.png)

Description of the four states in the figure (from left to right):

1. The application is routed to the web page. The top of the page is the system navigation bar, and the bottom is the **Web** component. In this case, the web page can be loaded properly.

2. During web page loading, the system sends a callback notification to the application side to hide the system navigation bar, so as to switch to the web-side navigation bar. In this case, the system navigation bar is hidden, the layout of the **Web** component is adjusted accordingly, and the background color (for example, gray) of the **Web** component is initially displayed at the bottom of the page.

3. The web page continues to be loaded and displayed based on the new size. The background color (for example, white) of the HTML page is displayed first.

4. Finally, the web page content is completely loaded, and the complete HTML web page content is displayed.

In the preceding process, if the background color of the **Web** component is different from that of the web page, flickering may occur during the navigation. The flickering  probability depends on the complexity of the web page and network conditions.

## Optimization

The application can set the background color of the Web component to match the web page background color, thereby avoiding visual flickering and improving user experience. For example, set the background color of the Web component to white.

In similar cases, if the default background color of the Web component is white while the web page background color is gray, white flickering may occur when navigating to a new web page. Similarly, setting the background color of the Web component to gray can resolve this issue.

Example of setting the background color of the **Web** component to gray (the default background color is white):

  <!-- @[FixingPageFlickeringButton](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ProcessWeb/entry/src/main/ets/pages/FixingPageFlickering.ets) -->
  
  ``` TypeScript
  Web({ src: $rawfile('xxx.html'), controller: this.webController})
    .backgroundColor(Color.Gray)
  ```