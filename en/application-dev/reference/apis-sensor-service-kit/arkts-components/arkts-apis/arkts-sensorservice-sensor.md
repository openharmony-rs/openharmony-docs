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
| [createQuaternion](arkts-sensorservice-sensor-createquaternion-f.md#createquaternion) | Converts a rotation vector into a quaternion. This API uses an asynchronous callback to return the result. |
| [createQuaternion](arkts-sensorservice-sensor-createquaternion-f.md#createquaternion-1) | Converts a rotation vector into a quaternion. This API uses a promise to return the result. |
| [createRotationMatrix](arkts-sensorservice-sensor-createrotationmatrix-f.md#createrotationmatrix) | Converts a rotation vector into a rotation matrix. This API uses an asynchronous callback to return the result. |
| [createRotationMatrix](arkts-sensorservice-sensor-createrotationmatrix-f.md#createrotationmatrix-1) | Converts a rotation vector into a rotation matrix. This API uses a promise to return the result. |
| [createRotationMatrix](arkts-sensorservice-sensor-createrotationmatrix-f.md#createrotationmatrix-2) | Obtains the rotation matrix based on a gravity vector and geomagnetic vector. This API uses an asynchronous callback to return the result. |
| [createRotationMatrix](arkts-sensorservice-sensor-createrotationmatrix-f.md#createrotationmatrix-3) | Obtains the rotation matrix based on a gravity vector and geomagnetic vector. This API uses a promise to return the result. |
| [getAltitude](arkts-sensorservice-sensor-getaltitude-f.md#getaltitude) | Obtains the altitude at which the device is located based on the sea-level atmospheric pressure and the current atmospheric pressure. This API uses an asynchronous callback to return the result. |
| [getAltitude](arkts-sensorservice-sensor-getaltitude-f.md#getaltitude-1) | Obtains the altitude at which the device is located based on the sea-level atmospheric pressure and the current atmospheric pressure. This API uses a promise to return the result. |
| [getAngleModify](arkts-sensorservice-sensor-getanglemodify-f.md#getanglemodify) | Obtains the angle change between two rotation matrices. This API uses an asynchronous callback to return the result. |
| [getAngleModify](arkts-sensorservice-sensor-getanglemodify-f.md#getanglemodify-1) | Obtains the angle change between two rotation matrices. This API uses a promise to return the result. |
| [getAngleVariation](arkts-sensorservice-sensor-getanglevariation-f.md#getanglevariation) | Obtains the angle change between two rotation matrices. This API uses an asynchronous callback to return the result. |
| [getAngleVariation](arkts-sensorservice-sensor-getanglevariation-f.md#getanglevariation-1) | Obtains the angle change between two rotation matrices. This API uses a promise to return the result. |
| [getDeviceAltitude](arkts-sensorservice-sensor-getdevicealtitude-f.md#getdevicealtitude) | Obtains the altitude based on the atmospheric pressure. This API uses an asynchronous callback to return the result. |
| [getDeviceAltitude](arkts-sensorservice-sensor-getdevicealtitude-f.md#getdevicealtitude-1) | Obtains the altitude based on the atmospheric pressure. This API uses a promise to return the result. |
| [getDirection](arkts-sensorservice-sensor-getdirection-f.md#getdirection) | Obtains the device direction based on the rotation matrix. This API uses an asynchronous callback to return the result. |
| [getDirection](arkts-sensorservice-sensor-getdirection-f.md#getdirection-1) | Obtains the device direction based on the rotation matrix. This API uses a promise to return the result. |
| [getGeomagneticDip](arkts-sensorservice-sensor-getgeomagneticdip-f.md#getgeomagneticdip) | Obtains the magnetic dip based on the inclination matrix. This API uses an asynchronous callback to return the result. |
| [getGeomagneticDip](arkts-sensorservice-sensor-getgeomagneticdip-f.md#getgeomagneticdip-1) | Obtains the magnetic dip based on the inclination matrix. This API uses a promise to return the result. |
| [getGeomagneticField](arkts-sensorservice-sensor-getgeomagneticfield-f.md#getgeomagneticfield) | Obtains the geomagnetic field of a geographic location. This API uses an asynchronous callback to return the result. |
| [getGeomagneticField](arkts-sensorservice-sensor-getgeomagneticfield-f.md#getgeomagneticfield-1) | Obtains the geomagnetic field of a geographic location. This API uses a promise to return the result. |
| [getGeomagneticInfo](arkts-sensorservice-sensor-getgeomagneticinfo-f.md#getgeomagneticinfo) | Obtains the geomagnetic field of a geographic location at a certain time. This API uses an asynchronous callback to return the result. |
| [getGeomagneticInfo](arkts-sensorservice-sensor-getgeomagneticinfo-f.md#getgeomagneticinfo-1) | Obtains the geomagnetic field of a geographic location at a certain time. This API uses a promise to return the result. |
| [getInclination](arkts-sensorservice-sensor-getinclination-f.md#getinclination) | Obtains the magnetic dip based on the inclination matrix. This API uses an asynchronous callback to return the result. |
| [getInclination](arkts-sensorservice-sensor-getinclination-f.md#getinclination-1) | Obtains the magnetic dip based on the inclination matrix. This API uses a promise to return the result. |
| [getOrientation](arkts-sensorservice-sensor-getorientation-f.md#getorientation) | Obtains the device direction based on the rotation matrix. This API uses an asynchronous callback to return the result. |
| [getOrientation](arkts-sensorservice-sensor-getorientation-f.md#getorientation-1) | Obtains the device direction based on the rotation matrix. This API uses a promise to return the result. |
| [getQuaternion](arkts-sensorservice-sensor-getquaternion-f.md#getquaternion) | Obtains the quaternion from a rotation vector. This API uses an asynchronous callback to return the result. |
| [getQuaternion](arkts-sensorservice-sensor-getquaternion-f.md#getquaternion-1) | Obtains the quaternion from a rotation vector. This API uses a promise to return the result. |
| [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md#getrotationmatrix) | Obtains the rotation matrix from a rotation vector. This API uses an asynchronous callback to return the result. |
| [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md#getrotationmatrix-1) | Obtains the rotation matrix from a rotation vector. This API uses a promise to return the result. |
| [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md#getrotationmatrix-2) | Obtains the rotation matrix based on a gravity vector and geomagnetic vector. This API uses an asynchronous callback to return the result. |
| [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md#getrotationmatrix-3) | Obtains the rotation matrix based on a gravity vector and geomagnetic vector. This API uses a promise to return the result. |
| [getSensorList](arkts-sensorservice-sensor-getsensorlist-f.md#getsensorlist) | Obtains information about all sensors on the device. This API uses an asynchronous callback to return the result. |
| [getSensorList](arkts-sensorservice-sensor-getsensorlist-f.md#getsensorlist-1) | Obtains information about all sensors on the device. This API uses a promise to return the result. |
| [getSensorListByDeviceSync](arkts-sensorservice-sensor-getsensorlistbydevicesync-f.md) | Obtains the information about all sensors on the device. |
| [getSensorListSync](arkts-sensorservice-sensor-getsensorlistsync-f.md) | Obtains information about all sensors on the device. This API returns the result synchronously. |
| [getSingleSensor](arkts-sensorservice-sensor-getsinglesensor-f.md#getsinglesensor) | Obtains information about the sensor of a specific type. This API uses an asynchronous callback to return the result. |
| [getSingleSensor](arkts-sensorservice-sensor-getsinglesensor-f.md#getsinglesensor-1) | Obtains information about the sensor of a specific type. This API uses a promise to return the result. |
| [getSingleSensorByDeviceSync](arkts-sensorservice-sensor-getsinglesensorbydevicesync-f.md) | Obtains information about the sensor of a specific type. |
| [getSingleSensorSync](arkts-sensorservice-sensor-getsinglesensorsync-f.md) | Obtains information about the sensor of a specific type. This API returns the result synchronously. |
| [off](arkts-sensorservice-sensor-off-f.md#off-4) | Unsubscribes from data of the acceleration sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-5) | Unsubscribes from data of the acceleration sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-6) | Unsubscribes from data of the uncalibrated acceleration sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-7) | Unsubscribes from data of the uncalibrated acceleration sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-8) | Unsubscribes from data of the ambient light sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-9) | Unsubscribes from data of the ambient light sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-10) | Unsubscribes from data of the ambient temperature sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-11) | Unsubscribes from data of the ambient temperature sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-12) | Unsubscribes from data of the barometer sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-13) | Unsubscribes from data of the barometer sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-14) | Unsubscribes from data of the gravity sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-15) | Unsubscribes from data of the gravity sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-16) | Unsubscribes from data of the gyroscope sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-17) | Unsubscribes from data of the gyroscope sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-18) | Unsubscribes from data of the uncalibrated gyroscope sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-19) | Unsubscribes from data of the uncalibrated gyroscope sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-20) | Unsubscribes from data of the Hall effect sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-21) | Unsubscribes from data of the Hall effect sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-22) | Unsubscribes from data of the heart rate sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-23) | Unsubscribes from data of the heart rate sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-24) | Unsubscribes from data of the humidity sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-25) | Unsubscribes from data of the humidity sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-26) | Unsubscribes from data of the linear acceleration sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-27) | Unsubscribes from data of the linear acceleration sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-28) | Unsubscribes from data of the magnetic field sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-29) | Unsubscribes from data of the magnetic field sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-30) | Unsubscribes from data of the uncalibrated magnetic field sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-31) | Unsubscribes from data of the uncalibrated magnetic field sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-32) | Unsubscribes from data of the orientation sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-33) | Unsubscribes from data of the orientation sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-34) | Unsubscribes from data of the pedometer sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-35) | Unsubscribes from data of the pedometer sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-36) | Unsubscribes from data of the pedometer detection sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-37) | Unsubscribes from data of the pedometer detection sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-38) | Unsubscribes from data of the proximity sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-39) | Unsubscribes from data of the proximity sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-40) | Unsubscribes from data of the rotation vector sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-41) | Unsubscribes from data of the rotation vector sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-42) | Unsubscribes from valid motion sensor data. |
| [off](arkts-sensorservice-sensor-off-f.md#off-43) | Unsubscribes from valid motion sensor data. |
| [off](arkts-sensorservice-sensor-off-f.md#off-44) | Unsubscribes from data of the wear detection sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-45) | Unsubscribes from the fused pressure sensor data. |
| [off](arkts-sensorservice-sensor-off-f.md#off-46) | Unsubscribes from data of the wear detection sensor. |
| [off](arkts-sensorservice-sensor-off-f.md#off-47) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-48) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-49) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-50) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-51) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-52) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-53) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-54) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-55) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-56) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-57) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-58) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-59) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-60) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-61) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-62) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-63) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-64) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-65) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#off-66) | Unsubscribes from valid motion sensor data. |
| [off](arkts-sensorservice-sensor-off-f.md#off-67) | Unsubscribes from sensor data changes. |
| [off](arkts-sensorservice-sensor-off-f.md#offsensorstatuschange) | Disables listening for sensor status changes. |
| [on](arkts-sensorservice-sensor-on-f.md#on-2) | Subscribes to data of the acceleration sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-3) | Subscribes to data of the uncalibrated acceleration sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-4) | Subscribes to data of the ambient light sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-5) | Subscribes to data of the ambient temperature sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-6) | Subscribes to data of the barometer sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-7) | Subscribes to data of the gravity sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-8) | Subscribes to data of the gyroscope sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-9) | Subscribes to data of the uncalibrated gyroscope sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-10) | Subscribes to data of the Hall effect sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-11) | Subscribes to data of the heart rate sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-12) | Subscribes to data of the humidity sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-13) | Subscribes to data of the linear acceleration sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-14) | Subscribes to data of the magnetic field sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-15) | Subscribes to data of the uncalibrated magnetic field sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-16) | Subscribes to data of the orientation sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-17) | Subscribes to data of the pedometer sensor. The step counter sensor's data reporting is subject to some delay, and the delay is determined by specific product implementations. |
| [on](arkts-sensorservice-sensor-on-f.md#on-18) | Subscribes to data of the pedometer detection sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-19) | Subscribes to data of the proximity sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-20) | Subscribes to data of the rotation vector sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-21) | Subscribes to the significant motion sensor data. |
| [on](arkts-sensorservice-sensor-on-f.md#on-22) | Subscribes to data of the wear detection sensor. |
| [on](arkts-sensorservice-sensor-on-f.md#on-23) | Subscribes to the fused pressure sensor data. |
| [on](arkts-sensorservice-sensor-on-f.md#on-24) | Subscribes to data changes of the acceleration sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-25) | Subscribes to data changes of the uncalibrated acceleration sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-26) | Subscribes to data changes of the ambient light sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-27) | Subscribes to data changes of the ambient temperature sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-28) | Subscribes to data changes of the barometer sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-29) | Subscribes to data changes of the gravity sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-30) | Subscribes to data changes of the gyroscope sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-31) | Subscribes to data changes of the uncalibrated gyroscope sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-32) | Subscribes to data changes of the Hall effect sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-33) | Subscribes to data changes of the heart rate sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-34) | Subscribes to data changes of the humidity sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-35) | Subscribes to data changes of the linear acceleration sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-36) | Subscribes to data changes of the magnetic field sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-37) | Subscribes to data changes of the uncalibrated magnetic field sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-38) | Subscribes to data changes of the orientation sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-39) | Subscribes to data changes of the pedometer sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-40) | Subscribes to data changes of the pedometer detection sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-41) | Subscribes to data changes of the proximity sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-42) | Subscribes to data changes of the rotation vector sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-43) | Subscribes to data changes of the significant motion sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#on-44) | Subscribes to data changes of the wear detection sensor. If this API is called multiple times for the same application, the last call takes effect. |
| [on](arkts-sensorservice-sensor-on-f.md#onsensorstatuschange) | Enables listening for sensor status changes. This API asynchronously returns the result through a callback. |
| [once](arkts-sensorservice-sensor-once-f.md#once) | Obtains data of the acceleration sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-1) | Obtains data of the uncalibrated acceleration sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-2) | Obtains data of the ambient light sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-3) | Obtains data of the temperature sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-4) | Obtains data of the barometer sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-5) | Obtains data of the gravity sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-6) | Obtains data of the gyroscope sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-7) | Obtains data of the uncalibrated gyroscope sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-8) | Obtains data of the Hall effect sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-9) | Obtains data of the heart rate sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-10) | Obtains data of the humidity sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-11) | Obtains data of the linear acceleration sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-12) | Obtains data of the magnetic field sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-13) | Obtains data of the uncalibrated magnetic field sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-14) | Obtains data of the orientation sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-15) | Obtains data of the pedometer sensor once. The step counter sensor's data reporting is subject to some delay, and the delay is determined by specific product implementations. |
| [once](arkts-sensorservice-sensor-once-f.md#once-16) | Obtains data of the pedometer sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-17) | Obtains data of the proximity sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-18) | Obtains data of the rotation vector sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-19) | Obtains the significant motion sensor data once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-20) | Obtains data of the wear detection sensor once. |
| [once](arkts-sensorservice-sensor-once-f.md#once-21) | Subscribes to only one data change of the acceleration sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-22) | Subscribes to only one data change of the uncalibrated acceleration sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-23) | Subscribes to only one data change of the ambient light sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-24) | Subscribes to only one data change of the ambient temperature sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-25) | Subscribes to only one data change of the barometer sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-26) | Subscribes to only one data change of the gravity sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-27) | Subscribes to only one data change of the gyroscope sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-28) | Subscribes to only one data change of the uncalibrated gyroscope sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-29) | Subscribes to only one data change of the Hall effect sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-30) | Subscribes to only one data change of the heart rate sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-31) | Subscribes to only one data change of the humidity sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-32) | Subscribes to only one data change of the linear acceleration sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-33) | Subscribes to only one data change of the magnetic field sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-34) | Subscribes to only one data change of the uncalibrated magnetic field sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-35) | Subscribes to only one data change of the orientation sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-36) | Subscribes to only one data change of the pedometer sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-37) | Subscribes to only one data change of the pedometer detection sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-38) | Subscribes to only one data change of the proximity sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-39) | Subscribes to only one data change of the rotation vector sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-40) | Subscribes to only one data change of the significant motion sensor. |
| [once](arkts-sensorservice-sensor-once-f.md#once-41) | Subscribes to only one data change of the wear detection sensor. |
| [transformCoordinateSystem](arkts-sensorservice-sensor-transformcoordinatesystem-f.md#transformcoordinatesystem) | Rotates a rotation vector so that it can represent the coordinate system in different ways. This API uses an asynchronous callback to return the result. |
| [transformCoordinateSystem](arkts-sensorservice-sensor-transformcoordinatesystem-f.md#transformcoordinatesystem-1) | Rotates a rotation vector so that it can represent the coordinate system in different ways. This API uses a promise to return the result. |
| [transformRotationMatrix](arkts-sensorservice-sensor-transformrotationmatrix-f.md#transformrotationmatrix) | Transforms a rotation vector based on the coordinate system. This API uses an asynchronous callback to return the result. |
| [transformRotationMatrix](arkts-sensorservice-sensor-transformrotationmatrix-f.md#transformrotationmatrix-1) | Transforms a rotation vector based on the coordinate system. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [off](arkts-sensorservice-sensor-off-f-sys.md#off) | Unsubscribes from data of the color sensor. |
| [off](arkts-sensorservice-sensor-off-f-sys.md#off-1) | Unsubscribes from data of the color sensor. |
| [off](arkts-sensorservice-sensor-off-f-sys.md#off-2) | Unsubscribes from data of the SAR sensor. |
| [off](arkts-sensorservice-sensor-off-f-sys.md#off-3) | Unsubscribes from data of the SAR sensor. |
| [on](arkts-sensorservice-sensor-on-f-sys.md#on) | Subscribes to data of the color sensor. |
| [on](arkts-sensorservice-sensor-on-f-sys.md#on-1) | Subscribes to data of the Sodium Adsorption Ratio (SAR) sensor. |
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
