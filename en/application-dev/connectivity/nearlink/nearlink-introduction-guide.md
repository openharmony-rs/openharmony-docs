# NearLink Overview
<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @CCCZKing-->
<!--Designer: @lilong32; @CCCZKing-->
<!--Tester: @zhangjiaji111-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=1dcd96bd4dccbe71b3303f191c3246c6b702a5b9 translatedAt=2026-09-29T10:58:13.392Z pushedAt=2026-09-30T06:24:37.076Z -->

NearLink provides a low-power, high-rate short-range communication service, supporting connections and data exchange between NearLink devices.

In NearLink communication, devices are classified into two roles: central devices and peripheral devices. A central device actively initiates scanning to discover and connect to peripheral devices that are broadcasting. A peripheral device announces itself by sending broadcasts; after being discovered and connected by a central device, it can perform corresponding data transmission. Device roles are not fixed, and the same device can assume different roles depending on the service scenario.

Possible use cases include:

- After a central device and a peripheral device (mouse) are paired and connected over NearLink, the mouse is used as an input device to control the central device.
- After a central device and a peripheral device (stylus) are paired and connected over NearLink, the stylus is used as an input device to control the central device.

## Constraints

The NearLink service applies to phones, PCs/2-in-1 devices, TVs, tablets, and wearables.

<!--RP1-->

<!--RP1End-->
