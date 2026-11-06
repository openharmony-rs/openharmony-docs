# Sensor_SubscriptionAttribute
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @andeszhang-->
<!--Tester: @zhaofangyuan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=78f85b66cc5fc42d50e25c207f47a6006c136e0a translatedAt=2026-09-02T07:30:58.229Z pushedAt=2026-09-05T11:20:52.148Z -->

```c
typedef struct Sensor_SubscriptionAttribute Sensor_SubscriptionAttribute
```

## Overview

Defines a struct for the sensor subscription attribute, including the sensor type, sampling rate, and data reporting interval. This attribute is applicable to sensor data subscription scenarios, helping developers configure the subscription mode based on service requirements and providing flexible capabilities for obtaining sensor data. This attribute can be used for step count and heart rate data subscription in health and fitness apps, real-time collection of temperature and humidity data in environment monitoring apps, and status change monitoring in device control apps.

**Since**: 11

**Related module**: [Sensor](capi-sensor.md)

**Header file**: [oh_sensor_type.h](capi-oh-sensor-type-h.md)

