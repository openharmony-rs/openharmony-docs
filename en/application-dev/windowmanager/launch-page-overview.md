# Application Starting Window Overview
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @xiaochaobu-->
<!--Designer: @tenMiles-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=494f31a35d1b25179fe202754d9ee44d527d8ab6 translatedAt=2026-11-05T10:48:43.564Z pushedAt=2026-11-06T01:01:12.327Z nl=1 -->

The starting window is the first page displayed when an application is launched from a cold start. It remains visible until the application process starts or the application content is fully loaded. This window plays a crucial role in presenting the brand identity of the application. You can customize resources to display a unique logo, thereby strengthening user recognition of the product.

## Use Scenarios

You are advised to consider the display effect in the following scenarios when designing the starting window.

- Application cold start

  When the application is launched without any background processes running, the starting window is shown first. There is a 200 ms fade-out animation transitioning from the starting window to the application content.

- Widgets on the multitasking screen

  If an application transitions to the background during startup, its starting window is displayed on the multitasking screen.

- Application exit

  If an application is destroyed and no snapshot is generated on the system, the starting window is displayed during the application exit.