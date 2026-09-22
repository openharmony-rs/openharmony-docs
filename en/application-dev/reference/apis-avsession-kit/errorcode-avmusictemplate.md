# Audio Template Error Codes
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @ccfriend-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=008efa88ee32d17b84c16292894f1139607c6cb8 translatedAt=2026-09-01T13:11:36.457Z pushedAt=2026-09-07T11:16:24.716Z -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 35000001 Audio Template Creation Failure

**Error Message**

Failed to create the AVMusicTemplate.

**Description**

Failed to create the audio template.

**Possible Causes**

The connection to the media enhancement service fails.

**Solution**

The device is restarted.

## 35000002 Audio Template Controller Creation Failure

**Error Message**

Failed to create the AVMusicTemplate controller.

**Description**

Failed to create the audio template controller.

**Possible Causes**

The **sessionId** parameter for creating the **AVMusicTemplateController** is invalid. The **sessionId** must be a valid string and correspond to an already created **AVMusicTemplate** instance.

**Solution**

1. Check whether **sessionId** is empty or valid. In an application process, a **sessionId** corresponds to an **AVMusicTemplateController**.
2. Check whether an application has created the **AVMusicTemplate** corresponding to the **sessionId**.

## 35000003 Template Listener Not Registered

**Error Message**

Template listener not registered.

**Description**

The template listener is not registered.

**Possible Causes**

The template listener fails to be registered.

**Solution**

1. Check whether the **AVMusicTemplate** instance is properly created in the application.
2. Check whether the functions related to the audio template in the application are abnormal, such as the creation of an **AVMusicTemplate** instance or registration of a controller.

## 35000004 Template Controller Callback Not Registered

**Error Message**

Controller callback not registered.

**Description**

The template controller callback is not registered.

**Possible Causes**

The controller callback fails to be registered.

**Solution**

1. Check whether the **AVMusicTemplateController** instance is properly created in the application.
2. Check whether other core features in the application are abnormal.

## 35000005 Audio Template Does Not Exist

**Error Message**

AVMusicTemplate does not exist.

**Description**

The audio template does not exist.

**Possible Causes**

The audio template has not been created.

**Solution**

1. Check whether the **sessionId** is empty and whether an **AVMusicTemplate** instance has been created for the **sessionId**.
2. Check whether other core features in the application are abnormal.

## 35000006 Template Controller Does Not Exist

**Error Message**

AVMusicTemplateController does not exist.

**Description**

The template controller does not exist.

**Possible Causes**

The **AVMusicTemplateController** does not exist.

**Solution**

1. Check whether the **AVMusicTemplateController** instance is properly created in the application.
2. Check whether other core features in the application are abnormal.

## 35000007 Template Controller Already Exists

**Error Message**

AVMusicTemplateController already exists.

**Description**

The template controller already exists.

**Possible Causes**

The **AVMusicTemplateController** already exists and does not need to be created again.

**Solution**

In an application process, a **sessionId** corresponds to an **AVMusicTemplateController**. You do not need to create it again.

## 35000008 Audio Template Management Service Does Not Exist

**Error Message**

AVMusicTemplate Manager services do not exist.

**Description**

The audio template management service does not exist.

**Possible Causes**

The media enhancement service fails to be started.

**Solution**

Restart the device.

## 35000009 Abnormal Audio Template Management Service

**Error Message**

AVMusicTemplate Manager services exception.

**Description**

The audio template management service is abnormal.

**Possible Causes**

The communication of the media enhancement service is abnormal.

**Solution**

1. Check whether other core features in the application are abnormal.
2. Restart the device.

## 35000010 Maximum Transmission Capacity Exceeded

**Error Message**

The data exceeds the maximum allowable transmission capacity.

**Description**

The data exceeds the maximum transmission capacity.

**Possible Causes**

The size of the metadata transmitted through the **AVMusicTemplate** APIs exceeds the 1 MB limit.

**Solution**

Transfer data larger than 1 MB in batches.

## 35000011 Data Writing Error, Invalid Data

**Error Message**

The data write error, data is invalid.

**Description**

Failed to write data. The data is invalid.

**Possible Causes**

Failed to write data.

**Solution**

Check whether the data to be transmitted contains invalid properties or values.

## 35000012 Audio Template Error

**Error Message**

AVMusicTemplate error.

**Description**

The audio template is incorrect.

**Possible Causes**

The audio content of the media enhancement service is incorrectly configured.

**Solution**

1. Check whether the API access parameters are correctly configured for the application and whether the API can be successfully called.
2. Check whether other core features in the application are abnormal.
