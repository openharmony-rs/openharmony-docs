# Vibrator Overview

<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @andeszhang-->
<!--Tester: @zhaofangyuan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=2cc3d788470dfc527ff67f0d956b9e3149129ee5 translatedAt=2026-08-20T06:25:45.600Z pushedAt=2026-08-20T13:27:36.558Z -->

The **vibrator** module extends the vibrator service via maximizing utilization of vibrator hardware capabilities. By innovatively integrating vibration and interaction, the module takes user interaction efficiency and usability to the next level.

## Working Principles

The vibrator is a Misc device that consists of four modules: Vibrator API, Vibrator Framework, Vibrator Service, and HDF layer.

  **Figure 1** Vibrator in Misc devices

![0752d302-aeb9-481a-bb8f-e5524eb61eeb](figures/0752d302-aeb9-481a-bb8f-e5524eb61eeb.png)

- Vibrator API: provides basic vibrator APIs, which can be used to query the vibrator list and the vibration effect, and start or stop the vibrator.

- Vibrator framework: manages the framework layer of the vibrator and communicates with the Misc Device Service.

- Misc device service: manages services of controllers.

- HDF layer: adapts to different devices.

## Constraints

When using a vibrator, you must declare the **ohos.permission.VIBRATE** permission before you can control the vibration effect.