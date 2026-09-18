# @ohos.sensor

The **Sensor** module provides APIs for obtaining the sensor list and subscribing to sensor data. It also provides some common sensor algorithms.

**Since:** 8

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createQuaternion](arkts-sensorservice-sensor-createquaternion-f.md) | Converts a rotation vector into a quaternion. This API uses an asynchronous callback to return the result. |
| [createQuaternion](arkts-sensorservice-sensor-createquaternion-f.md) | Converts a rotation vector into a quaternion. This API uses a promise to return the result. |
| [createRotationMatrix](arkts-sensorservice-sensor-createrotationmatrix-f.md) | Converts a rotation vector into a rotation matrix. This API uses an asynchronous callback to return the result. |
| [createRotationMatrix](arkts-sensorservice-sensor-createrotationmatrix-f.md) | Converts a rotation vector into a rotation matrix. This API uses a promise to return the result. |
| [createRotationMatrix](arkts-sensorservice-sensor-createrotationmatrix-f.md) | Obtains the rotation matrix based on a gravity vector and geomagnetic vector. This API uses an asynchronous callback to return the result. |
| [createRotationMatrix](arkts-sensorservice-sensor-createrotationmatrix-f.md) | Obtains the rotation matrix based on a gravity vector and geomagnetic vector. This API uses a promise to return the result. |
| [getAltitude](arkts-sensorservice-sensor-getaltitude-f.md) | Obtains the altitude at which the device is located based on the sea-level atmospheric pressure and the current atmospheric pressure. This API uses an asynchronous callback to return the result. |
| [getAltitude](arkts-sensorservice-sensor-getaltitude-f.md) | Obtains the altitude at which the device is located based on the sea-level atmospheric pressure and the current atmospheric pressure. This API uses a promise to return the result. |
| [getAngleModify](arkts-sensorservice-sensor-getanglemodify-f.md) | Obtains the angle change between two rotation matrices. This API uses an asynchronous callback to return the result. |
| [getAngleModify](arkts-sensorservice-sensor-getanglemodify-f.md) | Obtains the angle change between two rotation matrices. This API uses a promise to return the result. |
| [getAngleVariation](arkts-sensorservice-sensor-getanglevariation-f.md) | Obtains the angle change between two rotation matrices. This API uses an asynchronous callback to return the result. |
| [getAngleVariation](arkts-sensorservice-sensor-getanglevariation-f.md) | Obtains the angle change between two rotation matrices. This API uses a promise to return the result. |
| [getDeviceAltitude](arkts-sensorservice-sensor-getdevicealtitude-f.md) | Obtains the altitude based on the atmospheric pressure. This API uses an asynchronous callback to return the result. |
| [getDeviceAltitude](arkts-sensorservice-sensor-getdevicealtitude-f.md) | Obtains the altitude based on the atmospheric pressure. This API uses a promise to return the result. |
| [getDirection](arkts-sensorservice-sensor-getdirection-f.md) | Obtains the device direction based on the rotation matrix. This API uses an asynchronous callback to return the result. |
| [getDirection](arkts-sensorservice-sensor-getdirection-f.md) | Obtains the device direction based on the rotation matrix. This API uses a promise to return the result. |
| [getGeomagneticDip](arkts-sensorservice-sensor-getgeomagneticdip-f.md) | Obtains the magnetic dip based on the inclination matrix. This API uses an asynchronous callback to return the result. |
| [getGeomagneticDip](arkts-sensorservice-sensor-getgeomagneticdip-f.md) | Obtains the magnetic dip based on the inclination matrix. This API uses a promise to return the result. |
| [getGeomagneticField](arkts-sensorservice-sensor-getgeomagneticfield-f.md) | Obtains the geomagnetic field of a geographic location. This API uses an asynchronous callback to return the result. |
| [getGeomagneticField](arkts-sensorservice-sensor-getgeomagneticfield-f.md) | Obtains the geomagnetic field of a geographic location. This API uses a promise to return the result. |
| [getGeomagneticInfo](arkts-sensorservice-sensor-getgeomagneticinfo-f.md) | Obtains the geomagnetic field of a geographic location at a certain time. This API uses an asynchronous callback to return the result. |
| [getGeomagneticInfo](arkts-sensorservice-sensor-getgeomagneticinfo-f.md) | Obtains the geomagnetic field of a geographic location at a certain time. This API uses a promise to return the result. |
| [getInclination](arkts-sensorservice-sensor-getinclination-f.md) | Obtains the magnetic dip based on the inclination matrix. This API uses an asynchronous callback to return the result. |
| [getInclination](arkts-sensorservice-sensor-getinclination-f.md) | Obtains the magnetic dip based on the inclination matrix. This API uses a promise to return the result. |
| [getOrientation](arkts-sensorservice-sensor-getorientation-f.md) | Obtains the device direction based on the rotation matrix. This API uses an asynchronous callback to return the result. |
| [getOrientation](arkts-sensorservice-sensor-getorientation-f.md) | Obtains the device direction based on the rotation matrix. This API uses a promise to return the result. |
| [getQuaternion](arkts-sensorservice-sensor-getquaternion-f.md) | Obtains the quaternion from a rotation vector. This API uses an asynchronous callback to return the result. |
| [getQuaternion](arkts-sensorservice-sensor-getquaternion-f.md) | Obtains the quaternion from a rotation vector. This API uses a promise to return the result. |
| [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md) | Obtains the rotation matrix from a rotation vector. This API uses an asynchronous callback to return the result. |
| [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md) | Obtains the rotation matrix from a rotation vector. This API uses a promise to return the result. |
| [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md) | Obtains the rotation matrix based on a gravity vector and geomagnetic vector. This API uses an asynchronous callback to return the result. |
| [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md) | Obtains the rotation matrix based on a gravity vector and geomagnetic vector. This API uses a promise to return the result. |
| [getSensorList](arkts-sensorservice-sensor-getsensorlist-f.md) | Obtains information about all sensors on the device. This API uses an asynchronous callback to return the result. |
| [getSensorList](arkts-sensorservice-sensor-getsensorlist-f.md) | Obtains information about all sensors on the device. This API uses a promise to return the result. |
| [getSensorListByDeviceSync](arkts-sensorservice-sensor-getsensorlistbydevicesync-f.md) | Obtains the information about all sensors on the device. |
| [getSensorListSync](arkts-sensorservice-sensor-getsensorlistsync-f.md) | Obtains information about all sensors on the device. This API returns the result synchronously. |
| [getSingleSensor](arkts-sensorservice-sensor-getsinglesensor-f.md) | Obtains information about the sensor of a specific type. This API uses an asynchronous callback to return the result. |
| [getSingleSensor](arkts-sensorservice-sensor-getsinglesensor-f.md) | Obtains information about the sensor of a specific type. This API uses a promise to return the result. |
| [getSingleSensorByDeviceSync](arkts-sensorservice-sensor-getsinglesensorbydevicesync-f.md) | Obtains information about the sensor of a specific type. |
| [getSingleSensorSync](arkts-sensorservice-sensor-getsinglesensorsync-f.md) | Obtains information about the sensor of a specific type. This API returns the result synchronously. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the acceleration sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the acceleration sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the uncalibrated acceleration sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the uncalibrated acceleration sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the ambient light sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the ambient light sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the ambient temperature sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the ambient temperature sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the barometer sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the barometer sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the gravity sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the gravity sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the gyroscope sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the gyroscope sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the uncalibrated gyroscope sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the uncalibrated gyroscope sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the Hall effect sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the Hall effect sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the heart rate sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the heart rate sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the humidity sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the humidity sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the linear acceleration sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the linear acceleration sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the magnetic field sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the magnetic field sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the uncalibrated magnetic field sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the uncalibrated magnetic field sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the orientation sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the orientation sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the pedometer sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the pedometer sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the pedometer detection sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the pedometer detection sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the proximity sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the proximity sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the rotation vector sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the rotation vector sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from valid motion sensor data. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from valid motion sensor data. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the wear detection sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from the fused pressure sensor data. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from data of the wear detection sensor. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from valid motion sensor data. |
| [off](arkts-sensorservice-sensor-off-f.md) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#offsensorstatuschange) | Disables listening for sensor status changes. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the acceleration sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the uncalibrated acceleration sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the ambient light sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the ambient temperature sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the barometer sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the gravity sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the gyroscope sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the uncalibrated gyroscope sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the Hall effect sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the heart rate sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the humidity sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the linear acceleration sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the magnetic field sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the uncalibrated magnetic field sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the orientation sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the pedometer sensor. The step counter sensor's data reporting is subject to some delay, and the delay is determined by specific product implementations. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the pedometer detection sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the proximity sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the rotation vector sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to the significant motion sensor data. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data of the wear detection sensor. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to the fused pressure sensor data. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the acceleration sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the uncalibrated acceleration sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the ambient light sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the ambient temperature sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the barometer sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the gravity sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the gyroscope sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the uncalibrated gyroscope sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the Hall effect sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the heart rate sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the humidity sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the linear acceleration sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the magnetic field sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the uncalibrated magnetic field sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the orientation sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the pedometer sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the pedometer detection sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the proximity sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the rotation vector sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the significant motion sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md) | Subscribes to data changes of the wear detection sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#onsensorstatuschange) | Enables listening for sensor status changes. This API asynchronously returns the result through a callback. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the acceleration sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the uncalibrated acceleration sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the ambient light sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the temperature sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the barometer sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the gravity sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the gyroscope sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the uncalibrated gyroscope sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the Hall effect sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the heart rate sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the humidity sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the linear acceleration sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the magnetic field sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the uncalibrated magnetic field sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the orientation sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the pedometer sensor once. The step counter sensor's data reporting is subject to some delay, and the delay is determined by specific product implementations. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the pedometer sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the proximity sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the rotation vector sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains the significant motion sensor data once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Obtains data of the wear detection sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the acceleration sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the uncalibrated acceleration sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the ambient light sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the ambient temperature sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the barometer sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the gravity sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the gyroscope sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the uncalibrated gyroscope sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the Hall effect sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the heart rate sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the humidity sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the linear acceleration sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the magnetic field sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the uncalibrated magnetic field sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the orientation sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the pedometer sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the pedometer detection sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the proximity sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the rotation vector sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the significant motion sensor. |
| [once](arkts-sensorservice-sensor-once-f.md) | Subscribes to only one data change of the wear detection sensor. |
| [transformCoordinateSystem](arkts-sensorservice-sensor-transformcoordinatesystem-f.md) | Rotates a rotation vector so that it can represent the coordinate system in different ways. This API uses an asynchronous callback to return the result. |
| [transformCoordinateSystem](arkts-sensorservice-sensor-transformcoordinatesystem-f.md) | Rotates a rotation vector so that it can represent the coordinate system in different ways. This API uses a promise to return the result. |
| [transformRotationMatrix](arkts-sensorservice-sensor-transformrotationmatrix-f.md) | Transforms a rotation vector based on the coordinate system. This API uses an asynchronous callback to return the result. |
| [transformRotationMatrix](arkts-sensorservice-sensor-transformrotationmatrix-f.md) | Transforms a rotation vector based on the coordinate system. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [off](arkts-sensorservice-sensor-off-f-sys.md) | Unsubscribes from data of the color sensor. |
| [off](arkts-sensorservice-sensor-off-f-sys.md) | Unsubscribes from data of the color sensor. |
| [off](arkts-sensorservice-sensor-off-f-sys.md) | Unsubscribes from data of the SAR sensor. |
| [off](arkts-sensorservice-sensor-off-f-sys.md) | Unsubscribes from data of the SAR sensor. |
| [on](arkts-sensorservice-sensor-on-f-sys.md) | Subscribes to data of the color sensor. |
| [on](arkts-sensorservice-sensor-on-f-sys.md) | Subscribes to data of the Sodium Adsorption Ratio (SAR) sensor. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AccelerometerResponse](arkts-sensorservice-sensor-accelerometerresponse-i.md) | Describes the acceleration sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [AccelerometerUncalibratedResponse](arkts-sensorservice-sensor-accelerometeruncalibratedresponse-i.md) | Describes the uncalibrated acceleration sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [AmbientTemperatureResponse](arkts-sensorservice-sensor-ambienttemperatureresponse-i.md) | Describes the ambient temperature sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [BarometerResponse](arkts-sensorservice-sensor-barometerresponse-i.md) | Describes the barometer sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [CoordinatesOptions](arkts-sensorservice-sensor-coordinatesoptions-i.md) | Describes the coordinate options. |
| [FusionPressureResponse](arkts-sensorservice-sensor-fusionpressureresponse-i.md) | Describes the fusion pressure sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [GeomagneticResponse](arkts-sensorservice-sensor-geomagneticresponse-i.md) | Describes a geomagnetic response object. |
| [GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md) | Describes the gravity sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [GyroscopeResponse](arkts-sensorservice-sensor-gyroscoperesponse-i.md) | Describes the gyroscope sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [GyroscopeUncalibratedResponse](arkts-sensorservice-sensor-gyroscopeuncalibratedresponse-i.md) | Describes the uncalibrated gyroscope sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [HallResponse](arkts-sensorservice-sensor-hallresponse-i.md) | Describes the Hall effect sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [HeartRateResponse](arkts-sensorservice-sensor-heartrateresponse-i.md) | Describes the heart rate sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [HumidityResponse](arkts-sensorservice-sensor-humidityresponse-i.md) | Describes the humidity sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [LightResponse](arkts-sensorservice-sensor-lightresponse-i.md) | Describes the ambient light sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [LinearAccelerometerResponse](arkts-sensorservice-sensor-linearaccelerometerresponse-i.md) | Describes the linear acceleration sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [LocationOptions](arkts-sensorservice-sensor-locationoptions-i.md) | Describes the geographical location. |
| [MagneticFieldResponse](arkts-sensorservice-sensor-magneticfieldresponse-i.md) | Describes the magnetic field sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [MagneticFieldUncalibratedResponse](arkts-sensorservice-sensor-magneticfielduncalibratedresponse-i.md) | Describes the uncalibrated magnetic field sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [Options](arkts-sensorservice-sensor-options-i.md) | Describes the sensor data reporting frequency. |
| [OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md) | Describes the orientation sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [PedometerDetectionResponse](arkts-sensorservice-sensor-pedometerdetectionresponse-i.md) | Describes the pedometer detection sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md) | Describes the pedometer sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [ProximityResponse](arkts-sensorservice-sensor-proximityresponse-i.md) | Describes the proximity sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [Response](arkts-sensorservice-sensor-response-i.md) | Describes the timestamp of the sensor data. |
| [RotationMatrixResponse](arkts-sensorservice-sensor-rotationmatrixresponse-i.md) | Describes the response for setting the rotation matrix. |
| [RotationVectorResponse](arkts-sensorservice-sensor-rotationvectorresponse-i.md) | Describes the rotation vector sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [Sensor](arkts-sensorservice-sensor-sensor-i.md) | Describes the sensor information. |
| [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | Defines sensor parameters, including **deviceId** and **sensorIndex**. |
| [SensorStatusEvent](arkts-sensorservice-sensor-sensorstatusevent-i.md) | Defines a device status change event. |
| [SignificantMotionResponse](arkts-sensorservice-sensor-significantmotionresponse-i.md) | Describes the significant motion sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md) | Describes the wear detection sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ColorResponse](arkts-sensorservice-sensor-colorresponse-i-sys.md) | Describes the color sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
| [SarResponse](arkts-sensorservice-sensor-sarresponse-i-sys.md) | Describes the SAR sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [SensorAccuracy](arkts-sensorservice-sensor-sensoraccuracy-e.md) | Enumerates the accuracy levels of sensor data. |
| [SensorId](arkts-sensorservice-sensor-sensorid-e.md) | Enumerates the sensor types. |
| [SensorType](arkts-sensorservice-sensor-sensortype-e.md) | Enumerates the sensor types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [SensorId](arkts-sensorservice-sensor-sensorid-e-sys.md) | Enumerates the sensor types. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [SensorFrequency](arkts-sensorservice-sensor-sensorfrequency-t.md) | Defines the reporting frequency mode of the sensor. |
