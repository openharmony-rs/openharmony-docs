# Sensor_Subscriber
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @andeszhang-->
<!--Tester: @zhaofangyuan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=2cc3d788470dfc527ff67f0d956b9e3149129ee5 translatedAt=2026-09-02T07:29:56.899Z pushedAt=2026-09-05T11:18:37.268Z -->

```c
typedef struct Sensor_Subscriber Sensor_Subscriber
```

## Overview

Defines a struct for the sensor subscriber, including the subscription callback function and user data. You can use this struct to specify the parameters of a sensor subscriber. After the subscription is successful, the sensor data updates will be received.

**Since**: 11

**Related module**: [Sensor](capi-sensor.md)

**Header file**: [oh_sensor_type.h](capi-oh-sensor-type-h.md)

