# Sensor_SubscriptionId
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @andeszhang-->
<!--Tester: @zhaofangyuan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=2cc3d788470dfc527ff67f0d956b9e3149129ee5 translatedAt=2026-09-02T07:31:28.288Z pushedAt=2026-09-05T11:23:42.618Z -->

```c
typedef struct Sensor_SubscriptionId Sensor_SubscriptionId
```

## Overview

Defines a struct for the sensor subscription ID, which uniquely identifies a sensor subscription. This struct is used to identify a sensor subscription, including the sensor type and subscription conditions. You can use the sensor subscription ID to manage the lifecycle of a sensor subscription, including activating, deactivating, and querying the subscription status.

When subscribing to sensor data, the sensor subscription ID is used as a parameter in the subscription request to identify the subscription relationship. When querying the subscribed sensor information, the sensor subscription ID is used to obtain the corresponding subscription status and data. When canceling a sensor subscription, the sensor subscription ID is used to specify the subscription to be canceled.

**Since**: 11

**Related module**: [Sensor](capi-sensor.md)

**Header file**: [oh_sensor_type.h](capi-oh-sensor-type-h.md)

