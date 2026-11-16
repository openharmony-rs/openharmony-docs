# Metadata Binding Error Codes
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: Msdp-->
<!--Owner: @codexu62-->
<!--Designer: @yuxiaoyang-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=2fe43cf7ea77cdd21cfa7d17dc93a663c83e8548 translatedAt=2026-11-04T06:10:26.760Z pushedAt=2026-11-04T08:04:44.813Z nl=1 -->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 32100001 File Creation Failed
**Error Message**  
Internal handling failed.

**Description**  
This error code is reported when file creation fails while an API of the metadata binding module is being called.  

**Possible Cause**  
The service is abnormal.  

**Solution**
1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.  
2. If the operation fails for three consecutive retries, return the original image.  

<!--Del-->
## 32100002 Encoding Failed
**Error Message**  
Encoding failed. Possible causes: 1. Image processing error; 2. Channel coding error. 

**Description**  
This error code is reported when encoding fails due to an algorithm issue while the metadata binding encoding API encodeImage is being called.

**Possible Cause**  
Algorithm execution fails because of memory allocation failures or other reasons.  

**Procedure**  
1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.  
2. If the operation fails for three consecutive retries, return the original image.  

## 32100003 Decoding Failed
**Error Message**  
Decoding failed. Possible causes: 1. Image not encoded; 2. Image destroyed. 

**Description**  
This error code is reported when decoding fails due to an algorithm issue while the metadata binding decoding API decodeImage is being called.

**Possible Cause**  
Algorithm execution fails because of memory allocation failures or other reasons.  

**Procedure**  
1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.  
2. If the operation fails for three consecutive retries, return an empty link.  
<!--DelEnd-->  


## 32100004 Subscription Failed
**Error Message**  
Subscription Failed. Possible causes: 1. Abnormal system capability. 2. IPC communication abnormality. 3. Algorithm loading exception. 

**Symptom**  
This error code is reported if subscription fails when the **on** API of the **metadataBinding** module is called.

**Possible Cause**  
Subscription to change events has failed.  

**Procedure**  
1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the operation fails for three consecutive times, stop the retry.  

## 32100005 Unsubscription Failed

**Error Message**  
Unsubscription Failed. Possible causes: 1. Abnormal system capability. 2. IPC communication abnormality.

**Symptom**  
This error code is reported if unsubscription fails when the **off** API of the **metadataBinding** module is called.  

**Possible Cause**  
Unsubscription from change events has failed.  

**Solution**
1. Retry the operation at a specified interval (for example, 1s) or at an exponential increase interval.
2. If the operation fails for three consecutive times, stop the retry.