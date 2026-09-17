# capture_session.h

## Overview

The file declares the capture session concepts.

**Library**: libohcamera.so

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Related module**: [OH_Camera](capi-oh-camera.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [CaptureSession_Callbacks](capi-oh-camera-capturesession-callbacks.md) | CaptureSession_Callbacks | The struct describes the callbacks related to a capture session. |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) | Camera_CaptureSession | The struct describes the capture session object. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_CaptureSession_OnFocusStateChange)(Camera_CaptureSession* session, Camera_FocusState focusState)](#oh_capturesession_onfocusstatechange) | OH_CaptureSession_OnFocusStateChange | Defines the callback defined in the [CaptureSession_Callbacks](capi-oh-camera-capturesession-callbacks.md) struct and used to report focus status changes of a capture session. |
| [typedef void (\*OH_CaptureSession_OnError)(Camera_CaptureSession* session, Camera_ErrorCode errorCode)](#oh_capturesession_onerror) | OH_CaptureSession_OnError | Defines the callback defined in the [CaptureSession_Callbacks](capi-oh-camera-capturesession-callbacks.md) struct and used to report capture session errors. |
| [typedef void (\*OH_CaptureSession_OnSmoothZoomInfo)(Camera_CaptureSession* session, Camera_SmoothZoomInfo* smoothZoomInfo)](#oh_capturesession_onsmoothzoominfo) | OH_CaptureSession_OnSmoothZoomInfo | Defines the callback invoked when smooth zoom is triggered for a capture session. |
| [typedef void (\*OH_CaptureSession_OnAutoDeviceSwitchStatusChange)(Camera_CaptureSession* session, Camera_AutoDeviceSwitchStatusInfo* autoDeviceSwitchStatusInfo)](#oh_capturesession_onautodeviceswitchstatuschange) | OH_CaptureSession_OnAutoDeviceSwitchStatusChange | Capture session device switch status callback. |
| [typedef void (\*OH_CaptureSession_OnSystemPressureLevelChange)(Camera_CaptureSession* session, Camera_SystemPressureLevel systemPressureLevel)](#oh_capturesession_onsystempressurelevelchange) | OH_CaptureSession_OnSystemPressureLevelChange | Defines the callback used to listen for capture system pressure level changes. |
| [Camera_ErrorCode OH_CaptureSession_RegisterCallback(Camera_CaptureSession* session, CaptureSession_Callbacks* callback)](#oh_capturesession_registercallback) | - | Registers a callback to listen for capture session events. |
| [Camera_ErrorCode OH_CaptureSession_UnregisterCallback(Camera_CaptureSession* session, CaptureSession_Callbacks* callback)](#oh_capturesession_unregistercallback) | - | Unregisters the callback used to listen for capture session events. |
| [Camera_ErrorCode OH_CaptureSession_RegisterSmoothZoomInfoCallback(Camera_CaptureSession* session, OH_CaptureSession_OnSmoothZoomInfo smoothZoomInfoCallback)](#oh_capturesession_registersmoothzoominfocallback) | - | Registers a callback to listen for smooth zoom events. |
| [Camera_ErrorCode OH_CaptureSession_UnregisterSmoothZoomInfoCallback(Camera_CaptureSession* session, OH_CaptureSession_OnSmoothZoomInfo smoothZoomInfoCallback)](#oh_capturesession_unregistersmoothzoominfocallback) | - | Unregisters the callback used to listen for smooth zoom events. |
| [Camera_ErrorCode OH_CaptureSession_SetSessionMode(Camera_CaptureSession* session, Camera_SceneMode sceneMode)](#oh_capturesession_setsessionmode) | - | Sets a session mode. This API cannot be called after [OH_CaptureSession_BeginConfig](capi-capture-session-h.md#oh_capturesession_beginconfig). You are advised to call this function immediately after {@link OH_CameraManager_CreateCaptureSession}. |
| [Camera_ErrorCode OH_CaptureSession_AddSecureOutput(Camera_CaptureSession* session, Camera_PreviewOutput* previewOutput)](#oh_capturesession_addsecureoutput) | - | Marks a preview output stream as secure output. |
| [Camera_ErrorCode OH_CaptureSession_BeginConfig(Camera_CaptureSession* session)](#oh_capturesession_beginconfig) | - | Starts the configuration for a capture session. |
| [Camera_ErrorCode OH_CaptureSession_CommitConfig(Camera_CaptureSession* session)](#oh_capturesession_commitconfig) | - | Commits the configuration for a capture session. |
| [Camera_ErrorCode OH_CaptureSession_AddInput(Camera_CaptureSession* session, Camera_Input* cameraInput)](#oh_capturesession_addinput) | - | Adds a Camera_Input instance to a session. |
| [Camera_ErrorCode OH_CaptureSession_RemoveInput(Camera_CaptureSession* session, Camera_Input* cameraInput)](#oh_capturesession_removeinput) | - | Removes a Camera_Input instance from a session. |
| [Camera_ErrorCode OH_CaptureSession_AddPreviewOutput(Camera_CaptureSession* session, Camera_PreviewOutput* previewOutput)](#oh_capturesession_addpreviewoutput) | - | Adds a PreviewOutput instance to a session. |
| [Camera_ErrorCode OH_CaptureSession_RemovePreviewOutput(Camera_CaptureSession* session, Camera_PreviewOutput* previewOutput)](#oh_capturesession_removepreviewoutput) | - | Removes a PreviewOutput instance from a session. |
| [Camera_ErrorCode OH_CaptureSession_AddPhotoOutput(Camera_CaptureSession* session, Camera_PhotoOutput* photoOutput)](#oh_capturesession_addphotooutput) | - | Adds a PhotoOutput instance to a session. |
| [Camera_ErrorCode OH_CaptureSession_RemovePhotoOutput(Camera_CaptureSession* session, Camera_PhotoOutput* photoOutput)](#oh_capturesession_removephotooutput) | - | Removes a PhotoOutput instance from a session. |
| [Camera_ErrorCode OH_CaptureSession_AddVideoOutput(Camera_CaptureSession* session, Camera_VideoOutput* videoOutput)](#oh_capturesession_addvideooutput) | - | Adds a **VideoOutput** instance to a session. |
| [Camera_ErrorCode OH_CaptureSession_RemoveVideoOutput(Camera_CaptureSession* session, Camera_VideoOutput* videoOutput)](#oh_capturesession_removevideooutput) | - | Removes a VideoOutput instance from a session. |
| [Camera_ErrorCode OH_CaptureSession_AddMetadataOutput(Camera_CaptureSession* session, Camera_MetadataOutput* metadataOutput)](#oh_capturesession_addmetadataoutput) | - | Adds a MetadataOutput instance to a session. |
| [Camera_ErrorCode OH_CaptureSession_RemoveMetadataOutput(Camera_CaptureSession* session, Camera_MetadataOutput* metadataOutput)](#oh_capturesession_removemetadataoutput) | - | Removes a MetadataOutput instance from a session. |
| [Camera_ErrorCode OH_CaptureSession_Start(Camera_CaptureSession* session)](#oh_capturesession_start) | - | Starts a capture session. |
| [Camera_ErrorCode OH_CaptureSession_Stop(Camera_CaptureSession* session)](#oh_capturesession_stop) | - | Stops a capture session. |
| [Camera_ErrorCode OH_CaptureSession_Release(Camera_CaptureSession* session)](#oh_capturesession_release) | - | Releases a CaptureSession instance. |
| [Camera_ErrorCode OH_CaptureSession_HasFlash(Camera_CaptureSession* session, bool* hasFlash)](#oh_capturesession_hasflash) | - | Checks whether the device has flash. |
| [Camera_ErrorCode OH_CaptureSession_IsFlashModeSupported(Camera_CaptureSession* session, Camera_FlashMode flashMode, bool* isSupported)](#oh_capturesession_isflashmodesupported) | - | Checks whether a flash mode is supported. |
| [Camera_ErrorCode OH_CaptureSession_GetFlashMode(Camera_CaptureSession* session, Camera_FlashMode* flashMode)](#oh_capturesession_getflashmode) | - | Obtains the flash mode in use. |
| [Camera_ErrorCode OH_CaptureSession_SetFlashMode(Camera_CaptureSession* session, Camera_FlashMode flashMode)](#oh_capturesession_setflashmode) | - | Sets a flash mode for the device. |
| [typedef void (\*OH_CaptureSession_OnFlashStateChange)(const Camera_CaptureSession* session, OH_Camera_FlashState flashState)](#oh_capturesession_onflashstatechange) | OH_CaptureSession_OnFlashStateChange | Capture session flash state change callback. |
| [Camera_ErrorCode OH_CaptureSession_RegisterFlashStateChangeCallback(const Camera_CaptureSession* session, OH_CaptureSession_OnFlashStateChange flashStateChange)](#oh_capturesession_registerflashstatechangecallback) | - | Register flash state change event callback. |
| [Camera_ErrorCode OH_CaptureSession_UnregisterFlashStateChangeCallback(const Camera_CaptureSession* session, OH_CaptureSession_OnFlashStateChange flashStateChange)](#oh_capturesession_unregisterflashstatechangecallback) | - | Unregister flash state change callback. |
| [typedef void (\*OH_CaptureSession_OnExposureStateChange)(void* context, OH_Camera_ExposureState exposureState)](#oh_capturesession_onexposurestatechange) | OH_CaptureSession_OnExposureStateChange | Defines a callback function that is invoked when the exposure state changes. |
| [Camera_ErrorCode OH_CaptureSession_RegisterExposureStateChangeCallback(const Camera_CaptureSession* session, void* context, OH_CaptureSession_OnExposureStateChange callback)](#oh_capturesession_registerexposurestatechangecallback) | - | Registers a callback for exposure state changes.<br> After this callback is registered, the callback is invoked when the exposure state changes in the capture session. |
| [Camera_ErrorCode OH_CaptureSession_UnregisterExposureStateChangeCallback(const Camera_CaptureSession* session, void* context, OH_CaptureSession_OnExposureStateChange callback)](#oh_capturesession_unregisterexposurestatechangecallback) | - | Unregisters the callback for exposure state changes. |
| [Camera_ErrorCode OH_CaptureSession_IsExposureModeSupported(Camera_CaptureSession* session, Camera_ExposureMode exposureMode, bool* isSupported)](#oh_capturesession_isexposuremodesupported) | - | Checks whether an exposure mode is supported. |
| [Camera_ErrorCode OH_CaptureSession_GetExposureMode(Camera_CaptureSession* session, Camera_ExposureMode* exposureMode)](#oh_capturesession_getexposuremode) | - | Obtains the exposure mode in use. This API directly returns an invalid value if you have not set the exposure mode using [OH_CaptureSession_SetExposureMode](capi-capture-session-h.md#oh_capturesession_setexposuremode). |
| [Camera_ErrorCode OH_CaptureSession_IsWhiteBalanceModeSupported(Camera_CaptureSession* session, Camera_WhiteBalanceMode whiteBalanceMode, bool* isSupported)](#oh_capturesession_iswhitebalancemodesupported) | - | Checks whether the specified white balance mode is supported. |
| [Camera_ErrorCode OH_CaptureSession_GetWhiteBalanceMode(Camera_CaptureSession* session, Camera_WhiteBalanceMode* whiteBalanceMode)](#oh_capturesession_getwhitebalancemode) | - | Obtains the white balance mode in use. |
| [Camera_ErrorCode OH_CaptureSession_SetWhiteBalanceMode(Camera_CaptureSession* session, Camera_WhiteBalanceMode whiteBalanceMode)](#oh_capturesession_setwhitebalancemode) | - | Sets a white balance mode. |
| [Camera_ErrorCode OH_CaptureSession_GetWhiteBalanceRange(Camera_CaptureSession* session, int32_t *minColorTemperature, int32_t *maxColorTemperature)](#oh_capturesession_getwhitebalancerange) | - | Obtains the supported white balance color temperature range. |
| [Camera_ErrorCode OH_CaptureSession_GetWhiteBalance(Camera_CaptureSession* session, int32_t *colorTemperature)](#oh_capturesession_getwhitebalance) | - | Obtains the white balance color temperature. |
| [Camera_ErrorCode OH_CaptureSession_SetWhiteBalance(Camera_CaptureSession* session, int32_t colorTemperature)](#oh_capturesession_setwhitebalance) | - | Sets the white balance color temperature. Before setting this parameter, you are advised to use [OH_CaptureSession_GetWhiteBalanceRange](capi-capture-session-h.md#oh_capturesession_getwhitebalancerange) to obtain the supported white balance color temperature range. |
| [Camera_ErrorCode OH_CaptureSession_GetColorTintRange(const Camera_CaptureSession* session, int32_t *minColorTint, int32_t *maxColorTint)](#oh_capturesession_getcolortintrange) | - | Obtains the supported white balance color tint range. |
| [Camera_ErrorCode OH_CaptureSession_GetColorTint(const Camera_CaptureSession* session, int32_t *colorTint)](#oh_capturesession_getcolortint) | - | Obtains the white balance color tint. |
| [Camera_ErrorCode OH_CaptureSession_SetColorTint(Camera_CaptureSession* session, int32_t colorTint)](#oh_capturesession_setcolortint) | - | Sets the white balance color tint. |
| [Camera_ErrorCode OH_CaptureSession_SetExposureMode(Camera_CaptureSession* session, Camera_ExposureMode exposureMode)](#oh_capturesession_setexposuremode) | - | Sets an exposure mode for the device. |
| [Camera_ErrorCode OH_CaptureSession_GetMeteringPoint(Camera_CaptureSession* session, Camera_Point* point)](#oh_capturesession_getmeteringpoint) | - | Obtains the metering point in use. |
| [Camera_ErrorCode OH_CaptureSession_SetMeteringPoint(Camera_CaptureSession* session, Camera_Point point)](#oh_capturesession_setmeteringpoint) | - | Sets the metering point, which is the center point of the metering rectangle. |
| [Camera_ErrorCode OH_CaptureSession_IsExposureMeteringModeSupported(const Camera_CaptureSession* session, OH_Camera_ExposureMeteringMode exposureMeteringMode, bool* isSupported)](#oh_capturesession_isexposuremeteringmodesupported) | - | Check whether a specified exposure metering mode is supported. |
| [Camera_ErrorCode OH_CaptureSession_GetExposureMeteringMode(const Camera_CaptureSession* session, OH_Camera_ExposureMeteringMode* exposureMeteringMode)](#oh_capturesession_getexposuremeteringmode) | - | Get current exposure metering mode. |
| [Camera_ErrorCode OH_CaptureSession_SetExposureMeteringMode(const Camera_CaptureSession* session, OH_Camera_ExposureMeteringMode exposureMeteringMode)](#oh_capturesession_setexposuremeteringmode) | - | Set exposure metering mode. |
| [Camera_ErrorCode OH_CaptureSession_GetSupportedISORange(const Camera_CaptureSession* session, int32_t *minIsoValue, int32_t *maxIsoValue)](#oh_capturesession_getsupportedisorange) | - | Query the iso range. |
| [Camera_ErrorCode OH_CaptureSession_GetIso(const Camera_CaptureSession* session, int32_t* isoValue)](#oh_capturesession_getiso) | - | Get current iso sensitivity value, as defined in ISO 12232:2006. |
| [Camera_ErrorCode OH_CaptureSession_SetIso(const Camera_CaptureSession* session, int32_t isoValue)](#oh_capturesession_setiso) | - | Sets ISO sensitivity value, within the range of getSupportedIsoRange. This control can not effective if ExposureMode is set to EXPOSURE_MODE_LOCKED. |
| [typedef void (\*OH_CaptureSession_OnIsoChange)(Camera_CaptureSession* session, int32_t isoValue)](#oh_capturesession_onisochange) | OH_CaptureSession_OnIsoChange | Defines the callback used to listen for ISO changes in a camera session. |
| [Camera_ErrorCode OH_CaptureSession_RegisterIsoChangeCallback(Camera_CaptureSession* session, OH_CaptureSession_OnIsoChange isoChange)](#oh_capturesession_registerisochangecallback) | - | Registers a callback to listen for ISO changes. |
| [Camera_ErrorCode OH_CaptureSession_UnregisterIsoChangeCallback(Camera_CaptureSession* session, OH_CaptureSession_OnIsoChange isoChange)](#oh_capturesession_unregisterisochangecallback) | - | Unregisters the callback used to listen for ISO changes. |
| [Camera_ErrorCode OH_CaptureSession_GetSupportedPhysicalApertures(const Camera_CaptureSession* session, OH_Camera_PhysicalAperture** apertures, uint32_t* size)](#oh_capturesession_getsupportedphysicalapertures) | - | Gets the supported physical apertures list. Release the physical apertures memory by calling [OH_CaptureSession_DeletePhysicalApertures](capi-capture-session-h.md#oh_capturesession_deletephysicalapertures). |
| [Camera_ErrorCode OH_CaptureSession_GetPhysicalAperture(const Camera_CaptureSession* session, double* aperture)](#oh_capturesession_getphysicalaperture) | - | Gets the current physical aperture value |
| [Camera_ErrorCode OH_CaptureSession_DeletePhysicalApertures(const Camera_CaptureSession* session, OH_Camera_PhysicalAperture* apertures, uint32_t size)](#oh_capturesession_deletephysicalapertures) | - | Delete the physical apertures. |
| [Camera_ErrorCode OH_CaptureSession_SetPhysicalAperture(const Camera_CaptureSession* session, double aperture)](#oh_capturesession_setphysicalaperture) | - | Set physical aperture value. |
| [Camera_ErrorCode OH_CaptureSession_GetExposureBiasRange(Camera_CaptureSession* session, float* minExposureBias, float* maxExposureBias, float* step)](#oh_capturesession_getexposurebiasrange) | - | Obtains the exposure compensation values of the device. |
| [Camera_ErrorCode OH_CaptureSession_SetExposureBias(Camera_CaptureSession* session, float exposureBias)](#oh_capturesession_setexposurebias) | - | Sets an exposure compensation value for the device. |
| [Camera_ErrorCode OH_CaptureSession_GetExposureBias(Camera_CaptureSession* session, float* exposureBias)](#oh_capturesession_getexposurebias) | - | Obtains the exposure compensation value in use. |
| [Camera_ErrorCode OH_CaptureSession_GetSupportedExposureDurationRange(const Camera_CaptureSession* session, int32_t* minExposureDuration, int32_t* maxExposureDuration)](#oh_capturesession_getsupportedexposuredurationrange) | - | Get the supported range of exposure durations. Units: Microseconds. |
| [Camera_ErrorCode OH_CaptureSession_SetExposureDuration(const Camera_CaptureSession* session, int32_t exposureDuration)](#oh_capturesession_setexposureduration) | - | Set exposure duration. Units: Microseconds.This control is only effective if ExposureMode is set to EXPOSURE_MODE_MANUAL. If the sensor can't expose this duration exactly, it will shorten the duration to the nearest supported value, which is reporeted by Callback [OH_CaptureSession_OnExposureDurationChange](capi-capture-session-h.md#oh_capturesession_onexposuredurationchange). |
| [Camera_ErrorCode OH_CaptureSession_GetExposureDuration(const Camera_CaptureSession* session, int32_t* exposureDuration)](#oh_capturesession_getexposureduration) | - | Get current exposure duration. Units: Microseconds. |
| [typedef void (\*OH_CaptureSession_OnExposureDurationChange)(const Camera_CaptureSession* session, int32_t exposureDuration)](#oh_capturesession_onexposuredurationchange) | OH_CaptureSession_OnExposureDurationChange | Capture session exposure duration change callback. |
| [Camera_ErrorCode OH_CaptureSession_RegisterExposureInfoChangeCallback(const Camera_CaptureSession* session, OH_CaptureSession_OnExposureDurationChange exposureDurationChange)](#oh_capturesession_registerexposureinfochangecallback) | - | Register exposure info change event callback. After exposure parameters are changed, the system will returns the updated exposure infos. |
| [Camera_ErrorCode OH_CaptureSession_UnregisterExposureInfoChangeCallback(const Camera_CaptureSession* session, OH_CaptureSession_OnExposureDurationChange exposureDurationChange)](#oh_capturesession_unregisterexposureinfochangecallback) | - | Unregister exposure info change callback.Invoke this method after finishing camera operations. |
| [Camera_ErrorCode OH_CaptureSession_IsFocusModeSupported(Camera_CaptureSession* session, Camera_FocusMode focusMode, bool* isSupported)](#oh_capturesession_isfocusmodesupported) | - | Checks whether a focus mode is supported. |
| [Camera_ErrorCode OH_CaptureSession_GetFocusMode(Camera_CaptureSession* session, Camera_FocusMode* focusMode)](#oh_capturesession_getfocusmode) | - | Obtains the focus mode in use. |
| [Camera_ErrorCode OH_CaptureSession_SetFocusMode(Camera_CaptureSession* session, Camera_FocusMode focusMode)](#oh_capturesession_setfocusmode) | - | Sets a focus mode for the device. |
| [Camera_ErrorCode OH_CaptureSession_GetFocusPoint(Camera_CaptureSession* session, Camera_Point* focusPoint)](#oh_capturesession_getfocuspoint) | - | Obtains the focal point in use. |
| [Camera_ErrorCode OH_CaptureSession_SetFocusPoint(Camera_CaptureSession* session, Camera_Point focusPoint)](#oh_capturesession_setfocuspoint) | - | Sets a focal point for the device. |
| [Camera_ErrorCode OH_CaptureSession_GetZoomRatioRange(Camera_CaptureSession* session, float* minZoom, float* maxZoom)](#oh_capturesession_getzoomratiorange) | - | Obtains the supported zoom ratio range. |
| [Camera_ErrorCode OH_CaptureSession_GetZoomRatio(Camera_CaptureSession* session, float* zoom)](#oh_capturesession_getzoomratio) | - | Obtains the zoom ratio in use. |
| [Camera_ErrorCode OH_CaptureSession_SetZoomRatio(Camera_CaptureSession* session, float zoom)](#oh_capturesession_setzoomratio) | - | Sets a zoom ratio for the device. |
| [Camera_ErrorCode OH_CaptureSession_IsVideoStabilizationModeSupported(Camera_CaptureSession* session, Camera_VideoStabilizationMode mode, bool* isSupported)](#oh_capturesession_isvideostabilizationmodesupported) | - | Checks whether a video stabilization mode is supported. |
| [Camera_ErrorCode OH_CaptureSession_GetVideoStabilizationMode(Camera_CaptureSession* session, Camera_VideoStabilizationMode* mode)](#oh_capturesession_getvideostabilizationmode) | - | Obtains the video stabilization mode in use. |
| [Camera_ErrorCode OH_CaptureSession_SetVideoStabilizationMode(Camera_CaptureSession* session, Camera_VideoStabilizationMode mode)](#oh_capturesession_setvideostabilizationmode) | - | Sets a video stabilization mode for the device. |
| [Camera_ErrorCode OH_CaptureSession_CanAddInput(Camera_CaptureSession* session, Camera_Input* cameraInput, bool* isSuccessful)](#oh_capturesession_canaddinput) | - | Checks whether a Camera_Input instance can be added to a session. |
| [Camera_ErrorCode OH_CaptureSession_CanAddPreviewOutput(Camera_CaptureSession* session, Camera_PreviewOutput* cameraOutput, bool* isSuccessful)](#oh_capturesession_canaddpreviewoutput) | - | Checks whether a PreviewOutput instance can be added to a session. |
| [Camera_ErrorCode OH_CaptureSession_CanAddPhotoOutput(Camera_CaptureSession* session, Camera_PhotoOutput* cameraOutput, bool* isSuccessful)](#oh_capturesession_canaddphotooutput) | - | Checks whether a PhotoOutput instance can be added to a session. |
| [Camera_ErrorCode OH_CaptureSession_CanAddVideoOutput(Camera_CaptureSession* session, Camera_VideoOutput* cameraOutput, bool* isSuccessful)](#oh_capturesession_canaddvideooutput) | - | Checks whether a **VideoOutput** instance can be added to a session. |
| [Camera_ErrorCode OH_CaptureSession_CanPreconfig(Camera_CaptureSession* session, Camera_PreconfigType preconfigType, bool* canPreconfig)](#oh_capturesession_canpreconfig) | - | Checks whether a preconfigured resolution type is supported. |
| [Camera_ErrorCode OH_CaptureSession_CanPreconfigWithRatio(Camera_CaptureSession* session, Camera_PreconfigType preconfigType, Camera_PreconfigRatio preconfigRatio, bool* canPreconfig)](#oh_capturesession_canpreconfigwithratio) | - | Checks whether a preconfigured resolution type with an aspect ratio is supported. |
| [Camera_ErrorCode OH_CaptureSession_Preconfig(Camera_CaptureSession* session, Camera_PreconfigType preconfigType)](#oh_capturesession_preconfig) | - | Sets a preconfigured resolution type. |
| [Camera_ErrorCode OH_CaptureSession_PreconfigWithRatio(Camera_CaptureSession* session, Camera_PreconfigType preconfigType, Camera_PreconfigRatio preconfigRatio)](#oh_capturesession_preconfigwithratio) | - | Sets a preconfigured resolution type with an aspect ratio. |
| [Camera_ErrorCode OH_CaptureSession_GetExposureValue(Camera_CaptureSession* session, float* exposureValue)](#oh_capturesession_getexposurevalue) | - | Obtains the exposure value. |
| [Camera_ErrorCode OH_CaptureSession_GetFocalLength(Camera_CaptureSession* session, float* focalLength)](#oh_capturesession_getfocallength) | - | Obtains the current focal length. |
| [Camera_ErrorCode OH_CaptureSession_IsFocusDistanceSupported(const Camera_CaptureSession* session, bool* isSupported)](#oh_capturesession_isfocusdistancesupported) | - | Check whether focus distance is supported. |
| [Camera_ErrorCode OH_CaptureSession_GetFocusDistance(const Camera_CaptureSession* session, float* focusDistance)](#oh_capturesession_getfocusdistance) | - | Get current focus distance, ranging from 0.0 to 1.0, with 0.0 being shortest distance at which the lens can focus and 1.0 the furthest. The default value is 1.0. |
| [Camera_ErrorCode OH_CaptureSession_SetFocusDistance(const Camera_CaptureSession* session, float focusDistance)](#oh_capturesession_setfocusdistance) | - | Sets focus distance. Possible distance values range from 0.0 to 1.0, with 0.0 being shortest distance at which the lens can focus and 1.0 the furthest. The default value is 1.0. |
| [Camera_ErrorCode OH_CaptureSession_SetSmoothZoom(Camera_CaptureSession* session, float targetZoom, Camera_SmoothZoomMode smoothZoomMode)](#oh_capturesession_setsmoothzoom) | - | Sets smooth zoom. |
| [Camera_ErrorCode OH_CaptureSession_GetSupportedColorSpaces(Camera_CaptureSession* session, OH_NativeBuffer_ColorSpace** colorSpace, uint32_t* size)](#oh_capturesession_getsupportedcolorspaces) | - | Obtains the supported color spaces. |
| [Camera_ErrorCode OH_CaptureSession_DeleteColorSpaces(Camera_CaptureSession* session, OH_NativeBuffer_ColorSpace* colorSpace)](#oh_capturesession_deletecolorspaces) | - | Deletes color spaces. |
| [Camera_ErrorCode OH_CaptureSession_GetActiveColorSpace(Camera_CaptureSession* session, OH_NativeBuffer_ColorSpace* colorSpace)](#oh_capturesession_getactivecolorspace) | - | Obtains the active color space. |
| [Camera_ErrorCode OH_CaptureSession_SetActiveColorSpace(Camera_CaptureSession* session, OH_NativeBuffer_ColorSpace colorSpace)](#oh_capturesession_setactivecolorspace) | - | Sets the active color space. |
| [Camera_ErrorCode OH_CaptureSession_RegisterAutoDeviceSwitchStatusCallback(Camera_CaptureSession* session, OH_CaptureSession_OnAutoDeviceSwitchStatusChange autoDeviceSwitchStatusChange)](#oh_capturesession_registerautodeviceswitchstatuscallback) | - | Register device switch event callback. |
| [Camera_ErrorCode OH_CaptureSession_UnregisterAutoDeviceSwitchStatusCallback(Camera_CaptureSession* session, OH_CaptureSession_OnAutoDeviceSwitchStatusChange autoDeviceSwitchStatusChange)](#oh_capturesession_unregisterautodeviceswitchstatuscallback) | - | Unregister device switch event callback. |
| [Camera_ErrorCode OH_CaptureSession_IsAutoDeviceSwitchSupported(Camera_CaptureSession* session, bool* isSupported)](#oh_capturesession_isautodeviceswitchsupported) | - | Check whether auto device switch is supported. |
| [Camera_ErrorCode OH_CaptureSession_EnableAutoDeviceSwitch(Camera_CaptureSession* session, bool enabled)](#oh_capturesession_enableautodeviceswitch) | - | Enable auto switch or not for the camera device. |
| [Camera_ErrorCode OH_CaptureSession_SetQualityPrioritization(Camera_CaptureSession* session, Camera_QualityPrioritization qualityPrioritization)](#oh_capturesession_setqualityprioritization) | - | Set quality prioritization. |
| [Camera_ErrorCode OH_CaptureSession_IsMacroSupported(Camera_CaptureSession* session, bool* isSupported)](#oh_capturesession_ismacrosupported) | - | Checks whether macro photography is supported. |
| [Camera_ErrorCode OH_CaptureSession_EnableMacro(Camera_CaptureSession* session, bool enabled)](#oh_capturesession_enablemacro) | - | Enables or disables macro photography for the camera device. |
| [typedef void (\*OH_CaptureSession_OnMacroStatusChange)(Camera_CaptureSession* session, bool isMacroDetected)](#oh_capturesession_onmacrostatuschange) | OH_CaptureSession_OnMacroStatusChange | Defines the callback used to listen for macro status changes of a camera session. |
| [Camera_ErrorCode OH_CaptureSession_RegisterMacroStatusChangeCallback(Camera_CaptureSession* session, OH_CaptureSession_OnMacroStatusChange macroStatusChange)](#oh_capturesession_registermacrostatuschangecallback) | - | Registers a callback to listen for macro status changes of a camera session. |
| [Camera_ErrorCode OH_CaptureSession_UnregisterMacroStatusChangeCallback(Camera_CaptureSession* session, OH_CaptureSession_OnMacroStatusChange macroStatusChange)](#oh_capturesession_unregistermacrostatuschangecallback) | - | Unregisters the callback used to listen for macro status changes of a camera session. |
| [Camera_ErrorCode OH_CaptureSession_RegisterSystemPressureLevelChangeCallback(Camera_CaptureSession* session, OH_CaptureSession_OnSystemPressureLevelChange systemPressureLevelChange)](#oh_capturesession_registersystempressurelevelchangecallback) | - | Registers a callback to listen for capture system pressure level changes. |
| [Camera_ErrorCode OH_CaptureSession_UnregisterSystemPressureLevelChangeCallback(Camera_CaptureSession* session, OH_CaptureSession_OnSystemPressureLevelChange systemPressureLevelChange)](#oh_capturesession_unregistersystempressurelevelchangecallback) | - | Unregisters the callback used to listen for capture system pressure level changes. |
| [Camera_ErrorCode OH_CaptureSession_IsControlCenterSupported(Camera_CaptureSession* session, bool* isSupported)](#oh_capturesession_iscontrolcentersupported) | - | Checks whether the camera controller is supported. |
| [Camera_ErrorCode OH_CaptureSession_GetSupportedEffectTypes(Camera_CaptureSession* session, Camera_ControlCenterEffectType** types, uint32_t* size)](#oh_capturesession_getsupportedeffecttypes) | - | Obtains the effect types supported by the camera controller. |
| [Camera_ErrorCode OH_CaptureSession_DeleteSupportedEffectTypes(Camera_CaptureSession* session, Camera_ControlCenterEffectType* types, uint32_t size)](#oh_capturesession_deletesupportedeffecttypes) | - | Deletes the effect types supported by the camera controller. |
| [Camera_ErrorCode OH_CaptureSession_EnableControlCenter(Camera_CaptureSession* session, bool enabled)](#oh_capturesession_enablecontrolcenter) | - | Enables or disables the camera controller. |
| [typedef void (\*OH_CaptureSession_OnControlCenterEffectStatusChange)(Camera_CaptureSession* session, Camera_ControlCenterStatusInfo* controlCenterStatusInfo)](#oh_capturesession_oncontrolcentereffectstatuschange) | OH_CaptureSession_OnControlCenterEffectStatusChange | Defines the callback used to listen for effect status changes of a camera controller. |
| [Camera_ErrorCode OH_CaptureSession_RegisterControlCenterEffectStatusChangeCallback(Camera_CaptureSession* session, OH_CaptureSession_OnControlCenterEffectStatusChange controlCenterEffectStatusChange)](#oh_capturesession_registercontrolcentereffectstatuschangecallback) | - | Registers a callback to listen for effect status changes of a camera controller. |
| [Camera_ErrorCode OH_CaptureSession_UnregisterControlCenterEffectStatusChangeCallback(Camera_CaptureSession* session, OH_CaptureSession_OnControlCenterEffectStatusChange controlCenterEffectStatusChange)](#oh_capturesession_unregistercontrolcentereffectstatuschangecallback) | - | Unregisters the callback used to listen for effect status changes of a camera controller. |
| [Camera_ErrorCode OH_CaptureSession_GetRAWCaptureZoomRatioRange(const Camera_CaptureSession* session, float* minZoom, float* maxZoom)](#oh_capturesession_getrawcapturezoomratiorange) | - | Query the raw zoom range. |
| [Camera_ErrorCode OH_CaptureSession_IsOISModeSupported(const Camera_CaptureSession* session, OH_Camera_OISMode oisMode, bool* isSupported)](#oh_capturesession_isoismodesupported) | - | Checks if the specified OIS mode is supported. |
| [Camera_ErrorCode OH_CaptureSession_GetSupportedOISBiasRange(const Camera_CaptureSession* session, OH_Camera_OISAxes oisAxis, float* minBias, float* maxBias, float* step)](#oh_capturesession_getsupportedoisbiasrange) | - | Gets the supported bias range for the specified OIS axis. |
| [Camera_ErrorCode OH_CaptureSession_GetCurrentOISMode(const Camera_CaptureSession* session, OH_Camera_OISMode* oisMode)](#oh_capturesession_getcurrentoismode) | - | Gets the current OIS mode. |
| [Camera_ErrorCode OH_CaptureSession_GetCurrentCustomOISBias(const Camera_CaptureSession* session, float* pitchBias, float* yawBias)](#oh_capturesession_getcurrentcustomoisbias) | - | Gets the current custom bias values for all OIS axes. |
| [Camera_ErrorCode OH_CaptureSession_SetOISMode(const Camera_CaptureSession* session, OH_Camera_OISMode oisMode)](#oh_capturesession_setoismode) | - | Sets the OIS mode. |
| [Camera_ErrorCode OH_CaptureSession_SetOISModeCustom(const Camera_CaptureSession* session, float pitchBias, float yawBias)](#oh_capturesession_setoismodecustom) | - | Sets custom OIS bias values for all axes. |
| [Camera_ErrorCode OH_CaptureSession_GetZoomPointInfos(const Camera_CaptureSession* session, uint32_t* size, OH_Camera_ZoomPointInfo** zoomPointInfo)](#oh_capturesession_getzoompointinfos) | - | Gets the zoom point infos. Release the zoom point infos memory by calling [OH_CaptureSession_DeleteZoomPointInfos](capi-capture-session-h.md#oh_capturesession_deletezoompointinfos). |
| [Camera_ErrorCode OH_CaptureSession_DeleteZoomPointInfos(const Camera_CaptureSession* session, OH_Camera_ZoomPointInfo* zoomPointInfo)](#oh_capturesession_deletezoompointinfos) | - | Delete the zoom point infos. |
| [bool OH_CaptureSession_IsLockFocusTrackingSupported(const Camera_CaptureSession* session)](#oh_capturesession_islockfocustrackingsupported) | - | Checks whether the lock focus tracking is supported. |
| [Camera_ErrorCode OH_CaptureSession_LockFocusTracking(Camera_CaptureSession* session, Camera_Point focusPoint)](#oh_capturesession_lockfocustracking) | - | Lock focus tracking, can be unlocked by [OH_CaptureSession_UnlockFocusTracking](capi-capture-session-h.md#oh_capturesession_unlockfocustracking). |
| [Camera_ErrorCode OH_CaptureSession_UnlockFocusTracking(Camera_CaptureSession* session)](#oh_capturesession_unlockfocustracking) | - | Unlock focus tracking. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_CaptureSession_OnFocusStateChange)(Camera_CaptureSession* session, Camera_FocusState focusState) | Defines the callback defined in the [CaptureSession_Callbacks](capi-oh-camera-capturesession-callbacks.md) struct and used to report focus status changes of a capture session.<br>**Since**: 11 |
| void (*OH_CaptureSession_OnError)(Camera_CaptureSession* session, Camera_ErrorCode errorCode) | Defines the callback defined in the [CaptureSession_Callbacks](capi-oh-camera-capturesession-callbacks.md) struct and used to report capture session errors.<br>**Since**: 11 |
| void (*OH_CaptureSession_OnSmoothZoomInfo)(Camera_CaptureSession* session, Camera_SmoothZoomInfo* smoothZoomInfo) | Defines the callback invoked when smooth zoom is triggered for a capture session.<br>**Since**: 12 |
| void (*OH_CaptureSession_OnAutoDeviceSwitchStatusChange)(Camera_CaptureSession* session, Camera_AutoDeviceSwitchStatusInfo* autoDeviceSwitchStatusInfo) | Capture session device switch status callback.<br>**Since**: 13 |
| void (*OH_CaptureSession_OnSystemPressureLevelChange)(Camera_CaptureSession* session, Camera_SystemPressureLevel systemPressureLevel) | Defines the callback used to listen for capture system pressure level changes.<br>**Since**: 20 |
| void (*OH_CaptureSession_OnFlashStateChange)(const Camera_CaptureSession* session, OH_Camera_FlashState flashState) | Capture session flash state change callback.<br>**Since**: 24 |
| void (*OH_CaptureSession_OnExposureStateChange)(void* context, OH_Camera_ExposureState exposureState) | Defines a callback function that is invoked when the exposure state changes.<br>**Since**: 26.0.0 |
| void (*OH_CaptureSession_OnIsoChange)(Camera_CaptureSession* session, int32_t isoValue) | Defines the callback used to listen for ISO changes in a camera session.<br>**Since**: 22 |
| void (*OH_CaptureSession_OnExposureDurationChange)(const Camera_CaptureSession* session, int32_t exposureDuration) | Capture session exposure duration change callback.<br>**Since**: 24 |
| void (*OH_CaptureSession_OnMacroStatusChange)(Camera_CaptureSession* session, bool isMacroDetected) | Defines the callback used to listen for macro status changes of a camera session.<br>**Since**: 20 |
| void (*OH_CaptureSession_OnControlCenterEffectStatusChange)(Camera_CaptureSession* session, Camera_ControlCenterStatusInfo* controlCenterStatusInfo) | Defines the callback used to listen for effect status changes of a camera controller.<br>**Since**: 20 |

## Function description

### OH_CaptureSession_OnFocusStateChange()

```c
typedef void (*OH_CaptureSession_OnFocusStateChange)(Camera_CaptureSession* session, Camera_FocusState focusState)
```

**Description**

Defines the callback defined in the [CaptureSession_Callbacks](capi-oh-camera-capturesession-callbacks.md) struct and used to report focus status changes of a capture session.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)\* session | Pointer to the Camera_CaptureSession instance that transfers the callback. |
| Camera_FocusState focusState | Focus status. |

### OH_CaptureSession_OnError()

```c
typedef void (*OH_CaptureSession_OnError)(Camera_CaptureSession* session, Camera_ErrorCode errorCode)
```

**Description**

Defines the callback defined in the [CaptureSession_Callbacks](capi-oh-camera-capturesession-callbacks.md) struct and used to report capture session errors.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)\* session | Pointer to the Camera_CaptureSession instance that transfers the callback. |
| Camera_ErrorCode errorCode | Error code reported in a capture session. |

**Reference**:

CAMERA_SERVICE_FATAL_ERROR


### OH_CaptureSession_OnSmoothZoomInfo()

```c
typedef void (*OH_CaptureSession_OnSmoothZoomInfo)(Camera_CaptureSession* session, Camera_SmoothZoomInfo* smoothZoomInfo)
```

**Description**

Defines the callback invoked when smooth zoom is triggered for a capture session.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)\* session | Pointer to the Camera_CaptureSession instance that transfers the callback. |
| Camera_SmoothZoomInfo\* smoothZoomInfo | Pointer to the smooth zoom information passed by the callback. |

### OH_CaptureSession_OnAutoDeviceSwitchStatusChange()

```c
typedef void (*OH_CaptureSession_OnAutoDeviceSwitchStatusChange)(Camera_CaptureSession* session, Camera_AutoDeviceSwitchStatusInfo* autoDeviceSwitchStatusInfo)
```

**Description**

Capture session device switch status callback.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)\* session | the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) which deliver the callback. |
| Camera_AutoDeviceSwitchStatusInfo\* autoDeviceSwitchStatusInfo | the {@link Camera_AutoDeviceSwitchStatusInfo} which delivered by the callback. |

### OH_CaptureSession_OnSystemPressureLevelChange()

```c
typedef void (*OH_CaptureSession_OnSystemPressureLevelChange)(Camera_CaptureSession* session, Camera_SystemPressureLevel systemPressureLevel)
```

**Description**

Defines the callback used to listen for capture system pressure level changes.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)\* session | Pointer to the Camera_CaptureSession instance that transfers the callback. |
| Camera_SystemPressureLevel systemPressureLevel | Pointer to the system pressure level passed by the callback. |

### OH_CaptureSession_RegisterCallback()

```c
Camera_ErrorCode OH_CaptureSession_RegisterCallback(Camera_CaptureSession* session, CaptureSession_Callbacks* callback)
```

**Description**

Registers a callback to listen for capture session events.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the Camera_CaptureSession instance that transfers the callback. |
| [CaptureSession_Callbacks](capi-oh-camera-capturesession-callbacks.md)* callback | Pointer to the target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_UnregisterCallback()

```c
Camera_ErrorCode OH_CaptureSession_UnregisterCallback(Camera_CaptureSession* session, CaptureSession_Callbacks* callback)
```

**Description**

Unregisters the callback used to listen for capture session events.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the Camera_CaptureSession instance that transfers the callback. |
| [CaptureSession_Callbacks](capi-oh-camera-capturesession-callbacks.md)* callback | Pointer to the target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_RegisterSmoothZoomInfoCallback()

```c
Camera_ErrorCode OH_CaptureSession_RegisterSmoothZoomInfoCallback(Camera_CaptureSession* session, OH_CaptureSession_OnSmoothZoomInfo smoothZoomInfoCallback)
```

**Description**

Registers a callback to listen for smooth zoom events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the Camera_CaptureSession instance that transfers the callback. |
| [OH_CaptureSession_OnSmoothZoomInfo](capi-capture-session-h.md#oh_capturesession_onsmoothzoominfo) smoothZoomInfoCallback | Pointer to the target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_UnregisterSmoothZoomInfoCallback()

```c
Camera_ErrorCode OH_CaptureSession_UnregisterSmoothZoomInfoCallback(Camera_CaptureSession* session, OH_CaptureSession_OnSmoothZoomInfo smoothZoomInfoCallback)
```

**Description**

Unregisters the callback used to listen for smooth zoom events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the Camera_CaptureSession instance that transfers the callback. |
| [OH_CaptureSession_OnSmoothZoomInfo](capi-capture-session-h.md#oh_capturesession_onsmoothzoominfo) smoothZoomInfoCallback | Pointer to the target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_SetSessionMode()

```c
Camera_ErrorCode OH_CaptureSession_SetSessionMode(Camera_CaptureSession* session, Camera_SceneMode sceneMode)
```

**Description**

Sets a session mode. This API cannot be called after [OH_CaptureSession_BeginConfig](capi-capture-session-h.md#oh_capturesession_beginconfig). You are advised to call this function immediately after {@link OH_CameraManager_CreateCaptureSession}.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_SceneMode sceneMode | Scene mode. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed.      <br>CAMERA_SESSION_CONFIG_LOCKED: The session configuration is locked. |

### OH_CaptureSession_AddSecureOutput()

```c
Camera_ErrorCode OH_CaptureSession_AddSecureOutput(Camera_CaptureSession* session, Camera_PreviewOutput* previewOutput)
```

**Description**

Marks a preview output stream as secure output.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_PreviewOutput* previewOutput | Pointer to the target Camera_PreviewOutput instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed.      <br>CAMERA_SESSION_CONFIG_LOCKED: The session configuration is locked. |

### OH_CaptureSession_BeginConfig()

```c
Camera_ErrorCode OH_CaptureSession_BeginConfig(Camera_CaptureSession* session)
```

**Description**

Starts the configuration for a capture session.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_CONFIG_LOCKED: The session configuration is locked. |

### OH_CaptureSession_CommitConfig()

```c
Camera_ErrorCode OH_CaptureSession_CommitConfig(Camera_CaptureSession* session)
```

**Description**

Commits the configuration for a capture session.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CaptureSession_AddInput()

```c
Camera_ErrorCode OH_CaptureSession_AddInput(Camera_CaptureSession* session, Camera_Input* cameraInput)
```

**Description**

Adds a Camera_Input instance to a session.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_Input* cameraInput | Pointer to the Camera_Input instance to add. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed. |

### OH_CaptureSession_RemoveInput()

```c
Camera_ErrorCode OH_CaptureSession_RemoveInput(Camera_CaptureSession* session, Camera_Input* cameraInput)
```

**Description**

Removes a Camera_Input instance from a session.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_Input* cameraInput | Pointer to the Camera_Input instance to remove. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed. |

### OH_CaptureSession_AddPreviewOutput()

```c
Camera_ErrorCode OH_CaptureSession_AddPreviewOutput(Camera_CaptureSession* session, Camera_PreviewOutput* previewOutput)
```

**Description**

Adds a PreviewOutput instance to a session.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_PreviewOutput* previewOutput | Pointer to the PreviewOutput instance to add. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed. |

### OH_CaptureSession_RemovePreviewOutput()

```c
Camera_ErrorCode OH_CaptureSession_RemovePreviewOutput(Camera_CaptureSession* session, Camera_PreviewOutput* previewOutput)
```

**Description**

Removes a PreviewOutput instance from a session.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_PreviewOutput* previewOutput | Pointer to the PreviewOutput instance to remove. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed. |

### OH_CaptureSession_AddPhotoOutput()

```c
Camera_ErrorCode OH_CaptureSession_AddPhotoOutput(Camera_CaptureSession* session, Camera_PhotoOutput* photoOutput)
```

**Description**

Adds a PhotoOutput instance to a session.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_PhotoOutput* photoOutput | Pointer to the PhotoOutput instance to add. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed. |

### OH_CaptureSession_RemovePhotoOutput()

```c
Camera_ErrorCode OH_CaptureSession_RemovePhotoOutput(Camera_CaptureSession* session, Camera_PhotoOutput* photoOutput)
```

**Description**

Removes a PhotoOutput instance from a session.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_PhotoOutput* photoOutput | Pointer to the PhotoOutput instance to remove. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed. |

### OH_CaptureSession_AddVideoOutput()

```c
Camera_ErrorCode OH_CaptureSession_AddVideoOutput(Camera_CaptureSession* session, Camera_VideoOutput* videoOutput)
```

**Description**

Adds a **VideoOutput** instance to a session.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_VideoOutput* videoOutput | Pointer to the **VideoOutput** instance to add. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed. |

### OH_CaptureSession_RemoveVideoOutput()

```c
Camera_ErrorCode OH_CaptureSession_RemoveVideoOutput(Camera_CaptureSession* session, Camera_VideoOutput* videoOutput)
```

**Description**

Removes a VideoOutput instance from a session.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_VideoOutput* videoOutput | Pointer to the VideoOutput instance to remove. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed. |

### OH_CaptureSession_AddMetadataOutput()

```c
Camera_ErrorCode OH_CaptureSession_AddMetadataOutput(Camera_CaptureSession* session, Camera_MetadataOutput* metadataOutput)
```

**Description**

Adds a MetadataOutput instance to a session.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_MetadataOutput* metadataOutput | Pointer to the MetadataOutput instance to add. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed. |

### OH_CaptureSession_RemoveMetadataOutput()

```c
Camera_ErrorCode OH_CaptureSession_RemoveMetadataOutput(Camera_CaptureSession* session, Camera_MetadataOutput* metadataOutput)
```

**Description**

Removes a MetadataOutput instance from a session.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_MetadataOutput* metadataOutput | Pointer to the MetadataOutput instance to remove. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed. |

### OH_CaptureSession_Start()

```c
Camera_ErrorCode OH_CaptureSession_Start(Camera_CaptureSession* session)
```

**Description**

Starts a capture session.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the Camera_CaptureSession instance to start. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CaptureSession_Stop()

```c
Camera_ErrorCode OH_CaptureSession_Stop(Camera_CaptureSession* session)
```

**Description**

Stops a capture session.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the Camera_CaptureSession instance to stop. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CaptureSession_Release()

```c
Camera_ErrorCode OH_CaptureSession_Release(Camera_CaptureSession* session)
```

**Description**

Releases a CaptureSession instance.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the Camera_CaptureSession instance to release. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CaptureSession_HasFlash()

```c
Camera_ErrorCode OH_CaptureSession_HasFlash(Camera_CaptureSession* session, bool* hasFlash)
```

**Description**

Checks whether the device has flash.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| bool* hasFlash | Pointer to the check result for whether the device has flash. **true** if the device has flash, **<br>false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_IsFlashModeSupported()

```c
Camera_ErrorCode OH_CaptureSession_IsFlashModeSupported(Camera_CaptureSession* session, Camera_FlashMode flashMode, bool* isSupported)
```

**Description**

Checks whether a flash mode is supported.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_FlashMode flashMode | Flash mode to check. |
| bool* isSupported | Pointer to the check result for the support of the flash mode. **true** if supported, **false**<br>otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_GetFlashMode()

```c
Camera_ErrorCode OH_CaptureSession_GetFlashMode(Camera_CaptureSession* session, Camera_FlashMode* flashMode)
```

**Description**

Obtains the flash mode in use.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_FlashMode* flashMode | Pointer to the flash mode. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_SetFlashMode()

```c
Camera_ErrorCode OH_CaptureSession_SetFlashMode(Camera_CaptureSession* session, Camera_FlashMode flashMode)
```

**Description**

Sets a flash mode for the device.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_FlashMode flashMode | Flash mode to set. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_OnFlashStateChange()

```c
typedef void (*OH_CaptureSession_OnFlashStateChange)(const Camera_CaptureSession* session, OH_Camera_FlashState flashState)
```

**Description**

Capture session flash state change callback.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)\* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) which deliver the callback. |
| OH_Camera_FlashState flashState | The {@link OH_Camera_FlashState} which delivered by the callback. |

### OH_CaptureSession_RegisterFlashStateChangeCallback()

```c
Camera_ErrorCode OH_CaptureSession_RegisterFlashStateChangeCallback(const Camera_CaptureSession* session, OH_CaptureSession_OnFlashStateChange flashStateChange)
```

**Description**

Register flash state change event callback.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| [OH_CaptureSession_OnFlashStateChange](capi-capture-session-h.md#oh_capturesession_onflashstatechange) flashStateChange | The [OH_CaptureSession_OnFlashStateChange](capi-capture-session-h.md#oh_capturesession_onflashstatechange) to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect. |

### OH_CaptureSession_UnregisterFlashStateChangeCallback()

```c
Camera_ErrorCode OH_CaptureSession_UnregisterFlashStateChangeCallback(const Camera_CaptureSession* session, OH_CaptureSession_OnFlashStateChange flashStateChange)
```

**Description**

Unregister flash state change callback.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| [OH_CaptureSession_OnFlashStateChange](capi-capture-session-h.md#oh_capturesession_onflashstatechange) flashStateChange | The [OH_CaptureSession_OnFlashStateChange](capi-capture-session-h.md#oh_capturesession_onflashstatechange) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect. |

### OH_CaptureSession_OnExposureStateChange()

```c
typedef void (*OH_CaptureSession_OnExposureStateChange)(void* context, OH_Camera_ExposureState exposureState)
```

**Description**

Defines a callback function that is invoked when the exposure state changes.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| void\* context | Indicates the pointer to the user-defined context. |
| OH_Camera_ExposureState exposureState | Indicates the current exposure state. |

### OH_CaptureSession_RegisterExposureStateChangeCallback()

```c
Camera_ErrorCode OH_CaptureSession_RegisterExposureStateChangeCallback(const Camera_CaptureSession* session, void* context, OH_CaptureSession_OnExposureStateChange callback)
```

**Description**

Registers a callback for exposure state changes.<br> After this callback is registered, the callback is invoked when the exposure state changes in the capture session.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| void* context | Indicates the pointer to the user-defined context. |
| [OH_CaptureSession_OnExposureStateChange](capi-capture-session-h.md#oh_capturesession_onexposurestatechange) callback | [OH_CaptureSession_OnExposureStateChange](capi-capture-session-h.md#oh_capturesession_onexposurestatechange) Indicates the callback to register. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect. |

### OH_CaptureSession_UnregisterExposureStateChangeCallback()

```c
Camera_ErrorCode OH_CaptureSession_UnregisterExposureStateChangeCallback(const Camera_CaptureSession* session, void* context, OH_CaptureSession_OnExposureStateChange callback)
```

**Description**

Unregisters the callback for exposure state changes.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| void* context | Indicates the pointer to the user-defined context specified when the callback was registered. |
| [OH_CaptureSession_OnExposureStateChange](capi-capture-session-h.md#oh_capturesession_onexposurestatechange) callback | [OH_CaptureSession_OnExposureStateChange](capi-capture-session-h.md#oh_capturesession_onexposurestatechange) Indicates the callback to unregister. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect. |

### OH_CaptureSession_IsExposureModeSupported()

```c
Camera_ErrorCode OH_CaptureSession_IsExposureModeSupported(Camera_CaptureSession* session, Camera_ExposureMode exposureMode, bool* isSupported)
```

**Description**

Checks whether an exposure mode is supported.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_ExposureMode exposureMode | Exposure mode to check. |
| bool* isSupported | Pointer to the check result for the support of the exposure mode. **true** if supported, **false**<br>otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_GetExposureMode()

```c
Camera_ErrorCode OH_CaptureSession_GetExposureMode(Camera_CaptureSession* session, Camera_ExposureMode* exposureMode)
```

**Description**

Obtains the exposure mode in use. This API directly returns an invalid value if you have not set the exposure mode using [OH_CaptureSession_SetExposureMode](capi-capture-session-h.md#oh_capturesession_setexposuremode).

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_ExposureMode* exposureMode | Pointer to the exposure mode. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_IsWhiteBalanceModeSupported()

```c
Camera_ErrorCode OH_CaptureSession_IsWhiteBalanceModeSupported(Camera_CaptureSession* session, Camera_WhiteBalanceMode whiteBalanceMode, bool* isSupported)
```

**Description**

Checks whether the specified white balance mode is supported.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_WhiteBalanceMode whiteBalanceMode | White balance mode. |
| bool* isSupported | Pointer to the check result for the support of the specified white balance mode. **true** if supported, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The function is successfully called.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The camera session is not configured. |

### OH_CaptureSession_GetWhiteBalanceMode()

```c
Camera_ErrorCode OH_CaptureSession_GetWhiteBalanceMode(Camera_CaptureSession* session, Camera_WhiteBalanceMode* whiteBalanceMode)
```

**Description**

Obtains the white balance mode in use.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_WhiteBalanceMode* whiteBalanceMode | Pointer to the white balance mode. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The function is successfully called.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The camera session is not configured. |

### OH_CaptureSession_SetWhiteBalanceMode()

```c
Camera_ErrorCode OH_CaptureSession_SetWhiteBalanceMode(Camera_CaptureSession* session, Camera_WhiteBalanceMode whiteBalanceMode)
```

**Description**

Sets a white balance mode.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_WhiteBalanceMode whiteBalanceMode | White balance mode. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The setting is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The camera session is not configured. |

### OH_CaptureSession_GetWhiteBalanceRange()

```c
Camera_ErrorCode OH_CaptureSession_GetWhiteBalanceRange(Camera_CaptureSession* session, int32_t *minColorTemperature, int32_t *maxColorTemperature)
```

**Description**

Obtains the supported white balance color temperature range.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| int32_t *minColorTemperature | Pointer to the minimum supported color temperature, in Kelvin. |
| int32_t *maxColorTemperature | Pointer to the maximum supported color temperature, in Kelvin. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The function is successfully called.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The camera session is not configured. |

### OH_CaptureSession_GetWhiteBalance()

```c
Camera_ErrorCode OH_CaptureSession_GetWhiteBalance(Camera_CaptureSession* session, int32_t *colorTemperature)
```

**Description**

Obtains the white balance color temperature.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| int32_t *colorTemperature | Pointer to the white balance color temperature, in Kelvin. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The function is successfully called.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The camera session is not configured. |

### OH_CaptureSession_SetWhiteBalance()

```c
Camera_ErrorCode OH_CaptureSession_SetWhiteBalance(Camera_CaptureSession* session, int32_t colorTemperature)
```

**Description**

Sets the white balance color temperature. Before setting this parameter, you are advised to use [OH_CaptureSession_GetWhiteBalanceRange](capi-capture-session-h.md#oh_capturesession_getwhitebalancerange) to obtain the supported white balance color temperature range.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| int32_t colorTemperature | White balance color temperature, in Kelvin. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The setting is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The camera session is not configured. |

### OH_CaptureSession_GetColorTintRange()

```c
Camera_ErrorCode OH_CaptureSession_GetColorTintRange(const Camera_CaptureSession* session, int32_t *minColorTint, int32_t *maxColorTint)
```

**Description**

Obtains the supported white balance color tint range.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to a [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| int32_t *minColorTint | Pointer to the minimum color tint. |
| int32_t *maxColorTint | Pointer to the maximum color tint. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | Result code.          {@link CAMERA_OK} is returned if the function is called successfully.<br>        {@link CAMERA_INVALID_ARGUMENT} is returned if an input parameter<br>                is missing or the parameter type is incorrect.<br>        {@link CAMERA_SESSION_NOT_CONFIG} is returned if the session is not configured when the function is called. |

### OH_CaptureSession_GetColorTint()

```c
Camera_ErrorCode OH_CaptureSession_GetColorTint(const Camera_CaptureSession* session, int32_t *colorTint)
```

**Description**

Obtains the white balance color tint.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to a [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| int32_t *colorTint | Pointer to the color tint. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | Result code.          {@link CAMERA_OK} is returned if the function is called successfully.<br>        {@link CAMERA_INVALID_ARGUMENT} is returned if an input<br>                parameter is missing or the parameter type is incorrect.<br>        {@link CAMERA_SESSION_NOT_CONFIG} is returned if the session is not configured when the function is called. |

### OH_CaptureSession_SetColorTint()

```c
Camera_ErrorCode OH_CaptureSession_SetColorTint(Camera_CaptureSession* session, int32_t colorTint)
```

**Description**

Sets the white balance color tint.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to a [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| int32_t colorTint | Color tint. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | <ul>          <li>{@link CAMERA_OK} The operation is successful.</li><br>        <li>{@link CAMERA_INVALID_ARGUMENT} A parameter is missing or the parameter type is incorrect.</li><br>        <li>{@link CAMERA_SESSION_NOT_CONFIG} The capture session is not configured.</li>          </ul> |

### OH_CaptureSession_SetExposureMode()

```c
Camera_ErrorCode OH_CaptureSession_SetExposureMode(Camera_CaptureSession* session, Camera_ExposureMode exposureMode)
```

**Description**

Sets an exposure mode for the device.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_ExposureMode exposureMode | Exposure mode to set. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_GetMeteringPoint()

```c
Camera_ErrorCode OH_CaptureSession_GetMeteringPoint(Camera_CaptureSession* session, Camera_Point* point)
```

**Description**

Obtains the metering point in use.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_Point* point | Pointer to the metering point. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_SetMeteringPoint()

```c
Camera_ErrorCode OH_CaptureSession_SetMeteringPoint(Camera_CaptureSession* session, Camera_Point point)
```

**Description**

Sets the metering point, which is the center point of the metering rectangle.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_Point point | Metering point to set. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_IsExposureMeteringModeSupported()

```c
Camera_ErrorCode OH_CaptureSession_IsExposureMeteringModeSupported(const Camera_CaptureSession* session, OH_Camera_ExposureMeteringMode exposureMeteringMode, bool* isSupported)
```

**Description**

Check whether a specified exposure metering mode is supported.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| OH_Camera_ExposureMeteringMode exposureMeteringMode | The {@link OH_Camera_ExposureMeteringMode} to be checked. |
| bool* isSupported | Pointer to the result of whether exposure mode supported. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_GetExposureMeteringMode()

```c
Camera_ErrorCode OH_CaptureSession_GetExposureMeteringMode(const Camera_CaptureSession* session, OH_Camera_ExposureMeteringMode* exposureMeteringMode)
```

**Description**

Get current exposure metering mode.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| OH_Camera_ExposureMeteringMode* exposureMeteringMode | Pointer to the {@link OH_Camera_ExposureMeteringMode} instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation not allowed, session or inputdevice maybe abnormal.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_SetExposureMeteringMode()

```c
Camera_ErrorCode OH_CaptureSession_SetExposureMeteringMode(const Camera_CaptureSession* session, OH_Camera_ExposureMeteringMode exposureMeteringMode)
```

**Description**

Set exposure metering mode.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| OH_Camera_ExposureMeteringMode exposureMeteringMode | The target {@link OH_Camera_ExposureMeteringMode} to set. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation not allowed, session or inputdevice maybe abnormal.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_GetSupportedISORange()

```c
Camera_ErrorCode OH_CaptureSession_GetSupportedISORange(const Camera_CaptureSession* session, int32_t *minIsoValue, int32_t *maxIsoValue)
```

**Description**

Query the iso range.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| int32_t *minIsoValue | the minimum of iso value. |
| int32_t *maxIsoValue | the Maximum of iso value. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation not allowed, session or inputdevice maybe abnormal.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_GetIso()

```c
Camera_ErrorCode OH_CaptureSession_GetIso(const Camera_CaptureSession* session, int32_t* isoValue)
```

**Description**

Get current iso sensitivity value, as defined in ISO 12232:2006.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| int32_t* isoValue | Pointer to the current iso sensitivity value. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation not allowed, session or inputdevice maybe abnormal.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_SetIso()

```c
Camera_ErrorCode OH_CaptureSession_SetIso(const Camera_CaptureSession* session, int32_t isoValue)
```

**Description**

Sets ISO sensitivity value, within the range of getSupportedIsoRange. This control can not effective if ExposureMode is set to EXPOSURE_MODE_LOCKED.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| int32_t isoValue | Indicates target iso value to set. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation not allowed, session or inputdevice maybe abnormal.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_OnIsoChange()

```c
typedef void (*OH_CaptureSession_OnIsoChange)(Camera_CaptureSession* session, int32_t isoValue)
```

**Description**

Defines the callback used to listen for ISO changes in a camera session.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)\* session | Pointer to the **Camera_CaptureSession** instance. |
| int32_t isoValue | ISO value obtained in the callback. |

### OH_CaptureSession_RegisterIsoChangeCallback()

```c
Camera_ErrorCode OH_CaptureSession_RegisterIsoChangeCallback(Camera_CaptureSession* session, OH_CaptureSession_OnIsoChange isoChange)
```

**Description**

Registers a callback to listen for ISO changes.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the Camera_CaptureSession instance. |
| [OH_CaptureSession_OnIsoChange](capi-capture-session-h.md#oh_capturesession_onisochange) isoChange | Callback of the **OH_CaptureSession_OnIsoChange** type, which is used to listen for ISO changes. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_UnregisterIsoChangeCallback()

```c
Camera_ErrorCode OH_CaptureSession_UnregisterIsoChangeCallback(Camera_CaptureSession* session, OH_CaptureSession_OnIsoChange isoChange)
```

**Description**

Unregisters the callback used to listen for ISO changes.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the Camera_CaptureSession instance. |
| [OH_CaptureSession_OnIsoChange](capi-capture-session-h.md#oh_capturesession_onisochange) isoChange | Callback of the **OH_CaptureSession_OnIsoChange** type, which is used to listen for ISO changes. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_GetSupportedPhysicalApertures()

```c
Camera_ErrorCode OH_CaptureSession_GetSupportedPhysicalApertures(const Camera_CaptureSession* session, OH_Camera_PhysicalAperture** apertures, uint32_t* size)
```

**Description**

Gets the supported physical apertures list. Release the physical apertures memory by calling [OH_CaptureSession_DeletePhysicalApertures](capi-capture-session-h.md#oh_capturesession_deletephysicalapertures).

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance |
| OH_Camera_PhysicalAperture** apertures | pointer to an array for storing physical aperture values |
| uint32_t* size | the size of physical apertures. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} success<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation not allowed, session or inputdevice maybe abnormal.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_GetPhysicalAperture()

```c
Camera_ErrorCode OH_CaptureSession_GetPhysicalAperture(const Camera_CaptureSession* session, double* aperture)
```

**Description**

Gets the current physical aperture value

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance |
| double* aperture | returned current aperture value |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} success<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation not allowed, session or inputdevice maybe abnormal.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_DeletePhysicalApertures()

```c
Camera_ErrorCode OH_CaptureSession_DeletePhysicalApertures(const Camera_CaptureSession* session, OH_Camera_PhysicalAperture* apertures, uint32_t size)
```

**Description**

Delete the physical apertures.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| OH_Camera_PhysicalAperture* apertures | pointer to an array for storing physical aperture values |
| uint32_t size | the array size of the physical apertures. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect. |

### OH_CaptureSession_SetPhysicalAperture()

```c
Camera_ErrorCode OH_CaptureSession_SetPhysicalAperture(const Camera_CaptureSession* session, double aperture)
```

**Description**

Set physical aperture value.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance |
| double aperture | the aperture value to set |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} success<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation not allowed, session or inputdevice maybe abnormal.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_GetExposureBiasRange()

```c
Camera_ErrorCode OH_CaptureSession_GetExposureBiasRange(Camera_CaptureSession* session, float* minExposureBias, float* maxExposureBias, float* step)
```

**Description**

Obtains the exposure compensation values of the device.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| float* minExposureBias | Pointer to the minimum exposure compensation value. |
| float* maxExposureBias | Pointer to the maximum exposure compensation value. |
| float* step | Pointer to the exposure compensation step. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_SetExposureBias()

```c
Camera_ErrorCode OH_CaptureSession_SetExposureBias(Camera_CaptureSession* session, float exposureBias)
```

**Description**

Sets an exposure compensation value for the device.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| float exposureBias | Exposure compensation value to set. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_GetExposureBias()

```c
Camera_ErrorCode OH_CaptureSession_GetExposureBias(Camera_CaptureSession* session, float* exposureBias)
```

**Description**

Obtains the exposure compensation value in use.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| float* exposureBias | Pointer to the exposure compensation value. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_GetSupportedExposureDurationRange()

```c
Camera_ErrorCode OH_CaptureSession_GetSupportedExposureDurationRange(const Camera_CaptureSession* session, int32_t* minExposureDuration, int32_t* maxExposureDuration)
```

**Description**

Get the supported range of exposure durations. Units: Microseconds.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| int32_t* minExposureDuration | Pointer to the minimum of exposure duration. |
| int32_t* maxExposureDuration | Pointer to the maximum of exposure duration. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation not allowed, session or inputdevice maybe abnormal.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_SetExposureDuration()

```c
Camera_ErrorCode OH_CaptureSession_SetExposureDuration(const Camera_CaptureSession* session, int32_t exposureDuration)
```

**Description**

Set exposure duration. Units: Microseconds.This control is only effective if ExposureMode is set to EXPOSURE_MODE_MANUAL. If the sensor can't expose this duration exactly, it will shorten the duration to the nearest supported value, which is reporeted by Callback [OH_CaptureSession_OnExposureDurationChange](capi-capture-session-h.md#oh_capturesession_onexposuredurationchange).

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| int32_t exposureDuration | the target exposure duration to set. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation not allowed, session or inputdevice maybe abnormal.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_GetExposureDuration()

```c
Camera_ErrorCode OH_CaptureSession_GetExposureDuration(const Camera_CaptureSession* session, int32_t* exposureDuration)
```

**Description**

Get current exposure duration. Units: Microseconds.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| int32_t* exposureDuration | Pointer to the current exposure duration. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation not allowed, session or inputdevice maybe abnormal.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_OnExposureDurationChange()

```c
typedef void (*OH_CaptureSession_OnExposureDurationChange)(const Camera_CaptureSession* session, int32_t exposureDuration)
```

**Description**

Capture session exposure duration change callback.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)\* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) which deliver the callback. |
| int32_t exposureDuration | The exposure duration which delivered by the callback. |

### OH_CaptureSession_RegisterExposureInfoChangeCallback()

```c
Camera_ErrorCode OH_CaptureSession_RegisterExposureInfoChangeCallback(const Camera_CaptureSession* session, OH_CaptureSession_OnExposureDurationChange exposureDurationChange)
```

**Description**

Register exposure info change event callback. After exposure parameters are changed, the system will returns the updated exposure infos.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| [OH_CaptureSession_OnExposureDurationChange](capi-capture-session-h.md#oh_capturesession_onexposuredurationchange) exposureDurationChange | The [OH_CaptureSession_OnExposureDurationChange](capi-capture-session-h.md#oh_capturesession_onexposuredurationchange) to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>{@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect. |

### OH_CaptureSession_UnregisterExposureInfoChangeCallback()

```c
Camera_ErrorCode OH_CaptureSession_UnregisterExposureInfoChangeCallback(const Camera_CaptureSession* session, OH_CaptureSession_OnExposureDurationChange exposureDurationChange)
```

**Description**

Unregister exposure info change callback.Invoke this method after finishing camera operations.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| [OH_CaptureSession_OnExposureDurationChange](capi-capture-session-h.md#oh_capturesession_onexposuredurationchange) exposureDurationChange | The [OH_CaptureSession_OnExposureDurationChange](capi-capture-session-h.md#oh_capturesession_onexposuredurationchange) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>{@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect. |

### OH_CaptureSession_IsFocusModeSupported()

```c
Camera_ErrorCode OH_CaptureSession_IsFocusModeSupported(Camera_CaptureSession* session, Camera_FocusMode focusMode, bool* isSupported)
```

**Description**

Checks whether a focus mode is supported.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_FocusMode focusMode | Focus mode to check. |
| bool* isSupported | Pointer to the check result for the support of the focus mode. **true** if supported, **false**<br>otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_GetFocusMode()

```c
Camera_ErrorCode OH_CaptureSession_GetFocusMode(Camera_CaptureSession* session, Camera_FocusMode* focusMode)
```

**Description**

Obtains the focus mode in use.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_FocusMode* focusMode | Pointer to the focus mode. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_SetFocusMode()

```c
Camera_ErrorCode OH_CaptureSession_SetFocusMode(Camera_CaptureSession* session, Camera_FocusMode focusMode)
```

**Description**

Sets a focus mode for the device.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_FocusMode focusMode | Focus mode to set. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_GetFocusPoint()

```c
Camera_ErrorCode OH_CaptureSession_GetFocusPoint(Camera_CaptureSession* session, Camera_Point* focusPoint)
```

**Description**

Obtains the focal point in use.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_Point* focusPoint | Pointer to the focal point. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_SetFocusPoint()

```c
Camera_ErrorCode OH_CaptureSession_SetFocusPoint(Camera_CaptureSession* session, Camera_Point focusPoint)
```

**Description**

Sets a focal point for the device.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_Point focusPoint | Focal point to set. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_GetZoomRatioRange()

```c
Camera_ErrorCode OH_CaptureSession_GetZoomRatioRange(Camera_CaptureSession* session, float* minZoom, float* maxZoom)
```

**Description**

Obtains the supported zoom ratio range.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| float* minZoom | Pointer to the minimum zoom ratio. |
| float* maxZoom | Pointer to the maximum zoom ratio. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_GetZoomRatio()

```c
Camera_ErrorCode OH_CaptureSession_GetZoomRatio(Camera_CaptureSession* session, float* zoom)
```

**Description**

Obtains the zoom ratio in use.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| float* zoom | Pointer to the zoom ratio. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_SetZoomRatio()

```c
Camera_ErrorCode OH_CaptureSession_SetZoomRatio(Camera_CaptureSession* session, float zoom)
```

**Description**

Sets a zoom ratio for the device.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| float zoom | Target zoom ratio. It takes some time for the zoom ratio to take effect at the bottom layer. To obtain the correct zoom ratio, you need to wait for one to two frames. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_IsVideoStabilizationModeSupported()

```c
Camera_ErrorCode OH_CaptureSession_IsVideoStabilizationModeSupported(Camera_CaptureSession* session, Camera_VideoStabilizationMode mode, bool* isSupported)
```

**Description**

Checks whether a video stabilization mode is supported.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_VideoStabilizationMode mode | Video stabilization mode to check. |
| bool* isSupported | Pointer to the check result for the support of the video stabilization mode. **true** if supported, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_GetVideoStabilizationMode()

```c
Camera_ErrorCode OH_CaptureSession_GetVideoStabilizationMode(Camera_CaptureSession* session, Camera_VideoStabilizationMode* mode)
```

**Description**

Obtains the video stabilization mode in use.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_VideoStabilizationMode* mode | Pointer to the video stabilization mode. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_SetVideoStabilizationMode()

```c
Camera_ErrorCode OH_CaptureSession_SetVideoStabilizationMode(Camera_CaptureSession* session, Camera_VideoStabilizationMode mode)
```

**Description**

Sets a video stabilization mode for the device.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_VideoStabilizationMode mode | Video stabilization mode to set. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_CanAddInput()

```c
Camera_ErrorCode OH_CaptureSession_CanAddInput(Camera_CaptureSession* session, Camera_Input* cameraInput, bool* isSuccessful)
```

**Description**

Checks whether a Camera_Input instance can be added to a session.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_Input* cameraInput | Pointer to the Camera_Input instance to check. |
| bool* isSuccessful | Pointer to the check result for whether the Camera_Input instance can be added to the session. **<br>true** if it can be added to the session, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_CanAddPreviewOutput()

```c
Camera_ErrorCode OH_CaptureSession_CanAddPreviewOutput(Camera_CaptureSession* session, Camera_PreviewOutput* cameraOutput, bool* isSuccessful)
```

**Description**

Checks whether a PreviewOutput instance can be added to a session.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_PreviewOutput* cameraOutput | Pointer to the PreviewOutput instance to check. |
| bool* isSuccessful | Pointer to the check result for whether the PreviewOutput instance can be added to the session. *<br>*true** if it can be added to the session, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_CanAddPhotoOutput()

```c
Camera_ErrorCode OH_CaptureSession_CanAddPhotoOutput(Camera_CaptureSession* session, Camera_PhotoOutput* cameraOutput, bool* isSuccessful)
```

**Description**

Checks whether a PhotoOutput instance can be added to a session.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_PhotoOutput* cameraOutput | Pointer to the PhotoOutput instance to check. |
| bool* isSuccessful | Pointer to the check result for whether the PhotoOutput instance can be added to the session. **<br>true** if it can be added to the session, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_CanAddVideoOutput()

```c
Camera_ErrorCode OH_CaptureSession_CanAddVideoOutput(Camera_CaptureSession* session, Camera_VideoOutput* cameraOutput, bool* isSuccessful)
```

**Description**

Checks whether a **VideoOutput** instance can be added to a session.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_VideoOutput* cameraOutput | Pointer to the **VideoOutput** instance to check. |
| bool* isSuccessful | Pointer to the check result for whether the VideoOutput instance can be added to the session. **<br>true** if it can be added to the session, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_CanPreconfig()

```c
Camera_ErrorCode OH_CaptureSession_CanPreconfig(Camera_CaptureSession* session, Camera_PreconfigType preconfigType, bool* canPreconfig)
```

**Description**

Checks whether a preconfigured resolution type is supported.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_PreconfigType preconfigType | Target preconfigured resolution type. |
| bool* canPreconfig | Pointer to the check result for the support of the preconfigured resolution type. **true** if supported, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_CanPreconfigWithRatio()

```c
Camera_ErrorCode OH_CaptureSession_CanPreconfigWithRatio(Camera_CaptureSession* session, Camera_PreconfigType preconfigType, Camera_PreconfigRatio preconfigRatio, bool* canPreconfig)
```

**Description**

Checks whether a preconfigured resolution type with an aspect ratio is supported.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_PreconfigType preconfigType | Target preconfigured resolution type. |
| Camera_PreconfigRatio preconfigRatio | Target preconfigured aspect ratio. |
| bool* canPreconfig | Pointer to the check result for the support of the preconfigured resolution type. **true** if supported, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_Preconfig()

```c
Camera_ErrorCode OH_CaptureSession_Preconfig(Camera_CaptureSession* session, Camera_PreconfigType preconfigType)
```

**Description**

Sets a preconfigured resolution type.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_PreconfigType preconfigType | Target preconfigured resolution type. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CaptureSession_PreconfigWithRatio()

```c
Camera_ErrorCode OH_CaptureSession_PreconfigWithRatio(Camera_CaptureSession* session, Camera_PreconfigType preconfigType, Camera_PreconfigRatio preconfigRatio)
```

**Description**

Sets a preconfigured resolution type with an aspect ratio.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_PreconfigType preconfigType | Target preconfigured resolution type. |
| Camera_PreconfigRatio preconfigRatio | Target preconfigured aspect ratio. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CaptureSession_GetExposureValue()

```c
Camera_ErrorCode OH_CaptureSession_GetExposureValue(Camera_CaptureSession* session, float* exposureValue)
```

**Description**

Obtains the exposure value.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| float* exposureValue | Pointer to the exposure value. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CaptureSession_GetFocalLength()

```c
Camera_ErrorCode OH_CaptureSession_GetFocalLength(Camera_CaptureSession* session, float* focalLength)
```

**Description**

Obtains the current focal length.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| float* focalLength | Pointer to the focal length. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_IsFocusDistanceSupported()

```c
Camera_ErrorCode OH_CaptureSession_IsFocusDistanceSupported(const Camera_CaptureSession* session, bool* isSupported)
```

**Description**

Check whether focus distance is supported.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| bool* isSupported | Pointer to the result of whether focus distance is supported. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_GetFocusDistance()

```c
Camera_ErrorCode OH_CaptureSession_GetFocusDistance(const Camera_CaptureSession* session, float* focusDistance)
```

**Description**

Get current focus distance, ranging from 0.0 to 1.0, with 0.0 being shortest distance at which the lens can focus and 1.0 the furthest. The default value is 1.0.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| float* focusDistance | Pointer to the current focus distance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation not allowed, session or inputdevice maybe abnormal.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_SetFocusDistance()

```c
Camera_ErrorCode OH_CaptureSession_SetFocusDistance(const Camera_CaptureSession* session, float focusDistance)
```

**Description**

Sets focus distance. Possible distance values range from 0.0 to 1.0, with 0.0 being shortest distance at which the lens can focus and 1.0 the furthest. The default value is 1.0.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| float focusDistance | The focus distance to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation not allowed, session or inputdevice maybe abnormal.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_SetSmoothZoom()

```c
Camera_ErrorCode OH_CaptureSession_SetSmoothZoom(Camera_CaptureSession* session, float targetZoom, Camera_SmoothZoomMode smoothZoomMode)
```

**Description**

Sets smooth zoom.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| float targetZoom | Target zoom ratio. |
| Camera_SmoothZoomMode smoothZoomMode | Smooth zoom mode. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_GetSupportedColorSpaces()

```c
Camera_ErrorCode OH_CaptureSession_GetSupportedColorSpaces(Camera_CaptureSession* session, OH_NativeBuffer_ColorSpace** colorSpace, uint32_t* size)
```

**Description**

Obtains the supported color spaces.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| OH_NativeBuffer_ColorSpace** colorSpace | Double pointer to the list of supported color spaces, which are defined in the OH_NativeBuffer_ColorSpace struct, if the function is successfully called. |
| uint32_t* size | Pointer to the size of the list of supported color spaces. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_DeleteColorSpaces()

```c
Camera_ErrorCode OH_CaptureSession_DeleteColorSpaces(Camera_CaptureSession* session, OH_NativeBuffer_ColorSpace* colorSpace)
```

**Description**

Deletes color spaces.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| OH_NativeBuffer_ColorSpace* colorSpace | Pointer to the list of color spaces, which are defined in the OH_NativeBuffer_ColorSpace struct. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_GetActiveColorSpace()

```c
Camera_ErrorCode OH_CaptureSession_GetActiveColorSpace(Camera_CaptureSession* session, OH_NativeBuffer_ColorSpace* colorSpace)
```

**Description**

Obtains the active color space.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| OH_NativeBuffer_ColorSpace* colorSpace | Pointer to the OH_NativeBuffer_ColorSpace instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_SetActiveColorSpace()

```c
Camera_ErrorCode OH_CaptureSession_SetActiveColorSpace(Camera_CaptureSession* session, OH_NativeBuffer_ColorSpace colorSpace)
```

**Description**

Sets the active color space.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| OH_NativeBuffer_ColorSpace colorSpace | Target OH_NativeBuffer_ColorSpace instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_RegisterAutoDeviceSwitchStatusCallback()

```c
Camera_ErrorCode OH_CaptureSession_RegisterAutoDeviceSwitchStatusCallback(Camera_CaptureSession* session, OH_CaptureSession_OnAutoDeviceSwitchStatusChange autoDeviceSwitchStatusChange)
```

**Description**

Register device switch event callback.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| [OH_CaptureSession_OnAutoDeviceSwitchStatusChange](capi-capture-session-h.md#oh_capturesession_onautodeviceswitchstatuschange) autoDeviceSwitchStatusChange | the [OH_CaptureSession_OnAutoDeviceSwitchStatusChange](capi-capture-session-h.md#oh_capturesession_onautodeviceswitchstatuschange) to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link #CAMERA_OK} if the method call succeeds.<br>        {@link #CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect. |

### OH_CaptureSession_UnregisterAutoDeviceSwitchStatusCallback()

```c
Camera_ErrorCode OH_CaptureSession_UnregisterAutoDeviceSwitchStatusCallback(Camera_CaptureSession* session, OH_CaptureSession_OnAutoDeviceSwitchStatusChange autoDeviceSwitchStatusChange)
```

**Description**

Unregister device switch event callback.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| [OH_CaptureSession_OnAutoDeviceSwitchStatusChange](capi-capture-session-h.md#oh_capturesession_onautodeviceswitchstatuschange) autoDeviceSwitchStatusChange | the [OH_CaptureSession_OnAutoDeviceSwitchStatusChange](capi-capture-session-h.md#oh_capturesession_onautodeviceswitchstatuschange) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link #CAMERA_OK} if the method call succeeds.<br>        {@link #CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect. |

### OH_CaptureSession_IsAutoDeviceSwitchSupported()

```c
Camera_ErrorCode OH_CaptureSession_IsAutoDeviceSwitchSupported(Camera_CaptureSession* session, bool* isSupported)
```

**Description**

Check whether auto device switch is supported.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| bool* isSupported | the result of whether auto device switch supported. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link #CAMERA_OK} if the method call succeeds.<br>        {@link #CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link #CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_EnableAutoDeviceSwitch()

```c
Camera_ErrorCode OH_CaptureSession_EnableAutoDeviceSwitch(Camera_CaptureSession* session, bool enabled)
```

**Description**

Enable auto switch or not for the camera device.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| bool enabled | the flag of enable auto switch or not. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link #CAMERA_OK} if the method call succeeds.<br>        {@link #CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link #CAMERA_SESSION_NOT_CONFIG} if the capture session not config.<br>        {@link #CAMERA_SERVICE_FATAL_ERROR} if camera service fatal error. |

### OH_CaptureSession_SetQualityPrioritization()

```c
Camera_ErrorCode OH_CaptureSession_SetQualityPrioritization(Camera_CaptureSession* session, Camera_QualityPrioritization qualityPrioritization)
```

**Description**

Set quality prioritization.

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| Camera_QualityPrioritization qualityPrioritization | the target {@link Camera_QualityPrioritization} to set. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link #CAMERA_OK} if the method call succeeds.<br>        {@link #CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link #CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_IsMacroSupported()

```c
Camera_ErrorCode OH_CaptureSession_IsMacroSupported(Camera_CaptureSession* session, bool* isSupported)
```

**Description**

Checks whether macro photography is supported.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| bool* isSupported | Pointer to the check result for the support of macro photography. **true** if supported, **false**<br>otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | @return      <br>CAMERA_OK = 0: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_EnableMacro()

```c
Camera_ErrorCode OH_CaptureSession_EnableMacro(Camera_CaptureSession* session, bool enabled)
```

**Description**

Enables or disables macro photography for the camera device.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| bool enabled | Whether to enable or disable macro capability. **true** to enable, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | @return      <br>CAMERA_OK = 0: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured.      <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed. |

### OH_CaptureSession_OnMacroStatusChange()

```c
typedef void (*OH_CaptureSession_OnMacroStatusChange)(Camera_CaptureSession* session, bool isMacroDetected)
```

**Description**

Defines the callback used to listen for macro status changes of a camera session.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)\* session | Pointer to the Camera_CaptureSession instance. |
| bool isMacroDetected | Whether the camera is in macro mode. **true** if the camera is in macro mode, **false**<br>otherwise. |

### OH_CaptureSession_RegisterMacroStatusChangeCallback()

```c
Camera_ErrorCode OH_CaptureSession_RegisterMacroStatusChangeCallback(Camera_CaptureSession* session, OH_CaptureSession_OnMacroStatusChange macroStatusChange)
```

**Description**

Registers a callback to listen for macro status changes of a camera session.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the Camera_CaptureSession instance. |
| [OH_CaptureSession_OnMacroStatusChange](capi-capture-session-h.md#oh_capturesession_onmacrostatuschange) macroStatusChange | Callback used to return the macro status change. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_UnregisterMacroStatusChangeCallback()

```c
Camera_ErrorCode OH_CaptureSession_UnregisterMacroStatusChangeCallback(Camera_CaptureSession* session, OH_CaptureSession_OnMacroStatusChange macroStatusChange)
```

**Description**

Unregisters the callback used to listen for macro status changes of a camera session.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the Camera_CaptureSession instance. |
| [OH_CaptureSession_OnMacroStatusChange](capi-capture-session-h.md#oh_capturesession_onmacrostatuschange) macroStatusChange | Callback used to return the macro status change. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_RegisterSystemPressureLevelChangeCallback()

```c
Camera_ErrorCode OH_CaptureSession_RegisterSystemPressureLevelChangeCallback(Camera_CaptureSession* session, OH_CaptureSession_OnSystemPressureLevelChange systemPressureLevelChange)
```

**Description**

Registers a callback to listen for capture system pressure level changes.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the Camera_CaptureSession instance that transfers the callback. |
| [OH_CaptureSession_OnSystemPressureLevelChange](capi-capture-session-h.md#oh_capturesession_onsystempressurelevelchange) systemPressureLevelChange | Target callback, which is OH_CaptureSession_OnSystemPressureLevelChange. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_UnregisterSystemPressureLevelChangeCallback()

```c
Camera_ErrorCode OH_CaptureSession_UnregisterSystemPressureLevelChangeCallback(Camera_CaptureSession* session, OH_CaptureSession_OnSystemPressureLevelChange systemPressureLevelChange)
```

**Description**

Unregisters the callback used to listen for capture system pressure level changes.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the Camera_CaptureSession instance that transfers the callback. |
| [OH_CaptureSession_OnSystemPressureLevelChange](capi-capture-session-h.md#oh_capturesession_onsystempressurelevelchange) systemPressureLevelChange | Target callback, which is OH_CaptureSession_OnSystemPressureLevelChange. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_IsControlCenterSupported()

```c
Camera_ErrorCode OH_CaptureSession_IsControlCenterSupported(Camera_CaptureSession* session, bool* isSupported)
```

**Description**

Checks whether the camera controller is supported.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| bool* isSupported | Pointer to the check result for the support of the camera controller. **true** if supported, **<br>false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK = 0: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_GetSupportedEffectTypes()

```c
Camera_ErrorCode OH_CaptureSession_GetSupportedEffectTypes(Camera_CaptureSession* session, Camera_ControlCenterEffectType** types, uint32_t* size)
```

**Description**

Obtains the effect types supported by the camera controller.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_ControlCenterEffectType** types | Double pointer to the list of supported effect types, which are defined in the Camera_ControlCenterEffectType struct, if the function is successfully called. |
| uint32_t* size | Pointer to the size of the list of supported effect types. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. |

### OH_CaptureSession_DeleteSupportedEffectTypes()

```c
Camera_ErrorCode OH_CaptureSession_DeleteSupportedEffectTypes(Camera_CaptureSession* session, Camera_ControlCenterEffectType* types, uint32_t size)
```

**Description**

Deletes the effect types supported by the camera controller.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| Camera_ControlCenterEffectType* types | Pointer to the list of effect types, which are defined in the Camera_ControlCenterEffectType struct. |
| uint32_t size | Size of the list of supported effect types. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_EnableControlCenter()

```c
Camera_ErrorCode OH_CaptureSession_EnableControlCenter(Camera_CaptureSession* session, bool enabled)
```

**Description**

Enables or disables the camera controller.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the target Camera_CaptureSession instance. |
| bool enabled | Whether to enable the camera controller. **true** to enable, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK = 0: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CaptureSession_OnControlCenterEffectStatusChange()

```c
typedef void (*OH_CaptureSession_OnControlCenterEffectStatusChange)(Camera_CaptureSession* session, Camera_ControlCenterStatusInfo* controlCenterStatusInfo)
```

**Description**

Defines the callback used to listen for effect status changes of a camera controller.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)\* session | Pointer to the Camera_CaptureSession instance that transfers the callback. |
| Camera_ControlCenterStatusInfo\* controlCenterStatusInfo | Pointer to the effect status information passed by the callback. |

### OH_CaptureSession_RegisterControlCenterEffectStatusChangeCallback()

```c
Camera_ErrorCode OH_CaptureSession_RegisterControlCenterEffectStatusChangeCallback(Camera_CaptureSession* session, OH_CaptureSession_OnControlCenterEffectStatusChange controlCenterEffectStatusChange)
```

**Description**

Registers a callback to listen for effect status changes of a camera controller.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the Camera_CaptureSession instance that transfers the callback. |
| [OH_CaptureSession_OnControlCenterEffectStatusChange](capi-capture-session-h.md#oh_capturesession_oncontrolcentereffectstatuschange) controlCenterEffectStatusChange | Target callback, which is OH_CaptureSession_OnControlCenterEffectStatusChange. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_UnregisterControlCenterEffectStatusChangeCallback()

```c
Camera_ErrorCode OH_CaptureSession_UnregisterControlCenterEffectStatusChangeCallback(Camera_CaptureSession* session, OH_CaptureSession_OnControlCenterEffectStatusChange controlCenterEffectStatusChange)
```

**Description**

Unregisters the callback used to listen for effect status changes of a camera controller.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the Camera_CaptureSession instance that transfers the callback. |
| [OH_CaptureSession_OnControlCenterEffectStatusChange](capi-capture-session-h.md#oh_capturesession_oncontrolcentereffectstatuschange) controlCenterEffectStatusChange | Target callback, which is OH_CaptureSession_OnControlCenterEffectStatusChange. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CaptureSession_GetRAWCaptureZoomRatioRange()

```c
Camera_ErrorCode OH_CaptureSession_GetRAWCaptureZoomRatioRange(const Camera_CaptureSession* session, float* minZoom, float* maxZoom)
```

**Description**

Query the raw zoom range.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| float* minZoom | the minimum of zoom value. |
| float* maxZoom | the Maximum of zoom value. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation not allowed, session or inputdevice maybe abnormal.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_IsOISModeSupported()

```c
Camera_ErrorCode OH_CaptureSession_IsOISModeSupported(const Camera_CaptureSession* session, OH_Camera_OISMode oisMode, bool* isSupported)
```

**Description**

Checks if the specified OIS mode is supported.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to a session. |
| OH_Camera_OISMode oisMode | The OIS mode {@link OH_Camera_OISMode} to check. |
| bool* isSupported | Output parameter indicating support status. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameters are invalid.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation is not allowed.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_GetSupportedOISBiasRange()

```c
Camera_ErrorCode OH_CaptureSession_GetSupportedOISBiasRange(const Camera_CaptureSession* session, OH_Camera_OISAxes oisAxis, float* minBias, float* maxBias, float* step)
```

**Description**

Gets the supported bias range for the specified OIS axis.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to a session. |
| OH_Camera_OISAxes oisAxis | The OIS axis {@link OH_Camera_OISAxes} |
| float* minBias | Output parameter for minimum bias value. |
| float* maxBias | Output parameter for maximum bias value. |
| float* step | Output parameter for bias step value. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameters are invalid.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation is not allowed.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_GetCurrentOISMode()

```c
Camera_ErrorCode OH_CaptureSession_GetCurrentOISMode(const Camera_CaptureSession* session, OH_Camera_OISMode* oisMode)
```

**Description**

Gets the current OIS mode.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to a session. |
| OH_Camera_OISMode* oisMode | Output parameter for current OIS mode {@link OH_Camera_OISMode}. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameters are invalid.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation is not allowed.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_GetCurrentCustomOISBias()

```c
Camera_ErrorCode OH_CaptureSession_GetCurrentCustomOISBias(const Camera_CaptureSession* session, float* pitchBias, float* yawBias)
```

**Description**

Gets the current custom bias values for all OIS axes.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to a session. |
| float* pitchBias | Output parameter for pitch axis bias value. |
| float* yawBias | Output parameter for yaw axis bias value. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameters are invalid.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation is not allowed.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_SetOISMode()

```c
Camera_ErrorCode OH_CaptureSession_SetOISMode(const Camera_CaptureSession* session, OH_Camera_OISMode oisMode)
```

**Description**

Sets the OIS mode.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to a session. |
| OH_Camera_OISMode oisMode | The OIS mode {@link OH_Camera_OISMode} to set. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameters are invalid.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation is not allowed.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_SetOISModeCustom()

```c
Camera_ErrorCode OH_CaptureSession_SetOISModeCustom(const Camera_CaptureSession* session, float pitchBias, float yawBias)
```

**Description**

Sets custom OIS bias values for all axes.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to a session. |
| float pitchBias | Bias value for pitch axis. |
| float yawBias | Bias value for yaw axis. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameters are invalid.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation is not allowed.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_GetZoomPointInfos()

```c
Camera_ErrorCode OH_CaptureSession_GetZoomPointInfos(const Camera_CaptureSession* session, uint32_t* size, OH_Camera_ZoomPointInfo** zoomPointInfo)
```

**Description**

Gets the zoom point infos. Release the zoom point infos memory by calling [OH_CaptureSession_DeleteZoomPointInfos](capi-capture-session-h.md#oh_capturesession_deletezoompointinfos).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| uint32_t* size | Pointer to the size of queried zoom point info. |
| OH_Camera_ZoomPointInfo** zoomPointInfo | Double pointer to the queried zoom point info. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} is returned if the function is called successfully.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameters are invalid.<br>        {@link CAMERA_OPERATION_NOT_ALLOWED} if operation is not allowed.<br>        {@link CAMERA_SESSION_NOT_CONFIG} if the capture session not config. |

### OH_CaptureSession_DeleteZoomPointInfos()

```c
Camera_ErrorCode OH_CaptureSession_DeleteZoomPointInfos(const Camera_CaptureSession* session, OH_Camera_ZoomPointInfo* zoomPointInfo)
```

**Description**

Delete the zoom point infos.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| OH_Camera_ZoomPointInfo* zoomPointInfo | the target {@link Camera_ZoomPointInfo} list to be deleted if the method call succeeds. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link CAMERA_OK} if the method call succeeds.<br>        {@link CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect. |

### OH_CaptureSession_IsLockFocusTrackingSupported()

```c
bool OH_CaptureSession_IsLockFocusTrackingSupported(const Camera_CaptureSession* session)
```

**Description**

Checks whether the lock focus tracking is supported.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true if supported, false otherwise. |

### OH_CaptureSession_LockFocusTracking()

```c
Camera_ErrorCode OH_CaptureSession_LockFocusTracking(Camera_CaptureSession* session, Camera_Point focusPoint)
```

**Description**

Lock focus tracking, can be unlocked by [OH_CaptureSession_UnlockFocusTracking](capi-capture-session-h.md#oh_capturesession_unlockfocustracking).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |
| Camera_Point focusPoint | Pointer to the lock focus tracking point. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | <ul>          <li>{@link CAMERA_OK} The operation is successful.</li><br>        <li>{@link CAMERA_INVALID_ARGUMENT} A parameter is missing or the parameter type is incorrect.</li><br>        <li>{@link CAMERA_SESSION_NOT_CONFIG} The capture session is not configured.</li><br>        <li>{@link CAMERA_SERVICE_FATAL_ERROR} The camera service is abnormal.</li>          </ul> |

### OH_CaptureSession_UnlockFocusTracking()

```c
Camera_ErrorCode OH_CaptureSession_UnlockFocusTracking(Camera_CaptureSession* session)
```

**Description**

Unlock focus tracking.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md)* session | Pointer to the [Camera_CaptureSession](capi-oh-camera-camera-capturesession.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | <ul>          <li>{@link CAMERA_OK} The operation is successful.</li><br>        <li>{@link CAMERA_INVALID_ARGUMENT} A parameter is missing or the parameter type is incorrect.</li><br>        <li>{@link CAMERA_SESSION_NOT_CONFIG} The capture session is not configured.</li><br>        <li>{@link CAMERA_SERVICE_FATAL_ERROR} The camera service is abnormal.</li>          </ul> |


