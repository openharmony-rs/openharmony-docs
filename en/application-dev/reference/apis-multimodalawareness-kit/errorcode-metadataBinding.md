# Metadata Binding Error Codes
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: Msdp-->
<!--Owner: @codexu62-->
<!--Designer: @yuxiaoyang-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 32100001 File Creation Failed 
**Error Message** 
Internal handling failed. File creation failed.  

**Symptom** 
This error code is reported if a service error occurs when a certain metadataBinding API is called. 

**Possible Cause** 
The service is abnormal. 

**Solution**
1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval. 
2. If the operation fails for three consecutive retries, return the original image. 


## 32100002 Encoding Failed 
**Error Message** 
Encoding failed. Possible causes: 1. Image processing error; 2. Channel coding error. 

**Symptom** 
This error code is reported if the **encodeImage** API fails because of an algorithm error.

**Possible Cause** 
Algorithm execution fails because of memory allocation failures or other reasons. 

**Procedure** 
1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval. 
2. If the operation fails for three consecutive retries, return the original image. 

## 32100003 Decoding Failed 
**Error Code Information** 
Decoding failed. Possible causes: 1. Image not encoded; 2. Image destroyed. 

**Symptom** 
This error code is reported if the **decodeImage** API fails because of an algorithm error.

**Possible Cause** 
Algorithm execution fails because of memory allocation failures or other reasons. 

**Procedure** 
1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval. 
2. If the operation fails for three consecutive retries, return an empty link. 


## 32100004 Subscription Failed 
**Error Code Information** 
Subscription failed. Possible causes: 1. Abnormal system capability; 2. IPC exception; 3. Algorithm loading exception. 

**Symptom** 
This error code is reported if subscription fails when the **on** API of the **metadataBinding** module is called.

**Possible Cause** 
Subscription to change events has failed. 

**Procedure** 
1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the operation fails for three consecutive times, stop the retry.  

## 32100005 Unsubscription Failed 

**Error Code Information** 
Unsubscription failed. Possible causes: 1. Abnormal system capability; 2. IPC exception. 

**Symptom** 
This error code is reported if unsubscription fails when the **off** API of the **metadataBinding** module is called. 

**Possible Cause** 
Unsubscription from change events has failed. 

**Solution**
1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the operation fails for three consecutive times, stop the retry. 
