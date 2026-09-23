# Media Error Codes
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chennotfound-->
<!--Designer: @chris2981-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 5400101 Memory Allocation Failed

**Error Message**

No memory.

**Description**

Failed to allocate memory.

**Possible Causes**

1. The number of instances exceeds 16.
2. The new or malloc process fails, causing a null pointer.

**Solution**

Destroy this instance and re-create it. If the re-creation fails, stop related operations.

## 5400102 Unsupported Operation

**Error Message**

Operation not allowed.

**Description**

This operation is not allowed.

**Possible Causes**

1. This operation is not allowed in the current state.
2. The number of screen capture instances of the app exceeds 2, or the number of screen capture instances created on the device exceeds 16.

**Solution**

1. Switch the instance to the correct state and perform the operation.
2. Release all created instances.

The following are common cases when the SoundPool service returns error code 5400102.


### Scenario 1: Failed to load an audio file by calling **load** due to invalid resources.

If error code 5400102 is returned when [load](js-apis-inner-multimedia-soundPool.md#load) is called, locate the fault based on the system logs.

**Criterion**

The following error message is displayed in the app process log:

```text
Failed to load sound, the resource path is invalid, please check input parameters
```

The preceding error message is supported since API version 23.

**Possible Causes**

The resource does not exist or the provided path is incorrect.

**Solution**

Ensure that the required audio resource exists and the path is spelled correctly.

The following are common cases when the AVPlayer service returns error code 5400102.


### Scenario 1: Failed to change the resource for playback.

**Possible Causes**

1. The player is not in the idle state (such as prepared, playing, paused, completed, or stopped). It is not allowed to directly set a new playback resource such as **url**, **fdSrc**, or **dataSrc**. AVPlayer requires that the player be reset to the idle state before the resource is changed.
2. After only **stop()** is called, the player is not reset to the idle state and a new playback resource is set. You can only switch the player to the stopped state by calling **stop()**, but it will not return to the idle state. You need to call **reset()** for the player return to the idle state.
3. The state machine of the player cannot properly switch between different states. The correct state transition sequence is not followed, and necessary state transition steps are skipped.

**Solution**

1. Check the current player state. Before changing the playback resource, you must call **avPlayer.reset()** to restore the player to the idle state instead of calling only **avPlayer.stop()**. You can only call **reset()** for the player to return to the **idle** state after calling **stop()** to switch the player to the stopped state.
2. Set a new playback resource (**url**, **fdSrc**, or **dataSrc**) when the player is in the idle state. After the setting is successful, the player automatically switches to the initialized state.
3. Perform operations in the correct state transition sequence: idle → initialized → prepared → playing. Do not skip any state or perform operations in reverse order.
4. If the error persists after you change the resource for multiple times, you are advised to call **avPlayer.release()** to destroy the current instance, create a new AVPlayer instance, and then set the resource.

### Scenario 2: Failed to play the file.

**Possible Causes**

1. The end of the media file to be played contains data that does not comply with the format or the tail information of the file is damaged. As a result, when the demuxer parses the end of the file, an abnormal state is triggered, and an error indicating the operation is not allowed is reported.
2. The encapsulation format of the media file is incorrect. For example, the moov box of the MP4 file is located at the end of the file, the mdat box data is incomplete, or an error occurs in the demuxer during parsing.
3. The player is invoked to perform a playback control operation (such as seek, pause, or play) when the file parsing is abnormal. The current state does not support this operation.

   For example:

   (1) When **play** is called without setting the data source, the error message is "errorCode 5400102 The current state is idle."Play operation only supports prepared/paused/completed.

   (2) When **play** is called when the player is in the initialized state, the error message is "errorCode 5400102 The current state is initialized."Play operation only supports prepared/paused/completed.

   (3) When **play** is called after **reset** is called when the player is in the playing state, the error message is "errorCode 5400102 the current state is idle."Play operation only supports prepared/paused/completed.

   (4) When **seek** is called when the player is in the initialized state, the error message is "errorCode 5400102, errorMsg Operate Not Permit: The current state is initialized, seek operation only support prepared/playing/paused/completed state."

**Solution**

1. Check whether the media file is complete. If non-standard data is detected at the end of the file, a status error may be triggered. You are advised to use another playback tool to check whether the file can be played properly.
2. Check whether the encapsulation format of the media file is standard. Non-standard encapsulation may cause the demuxer to be in an abnormal state, triggering an error indicating that the operation is not allowed.
3. If the player enters the error state due to a file exception, call **avPlayer.reset()** to reset the player to the idle state. Replace the media file with a normal one and play it again.
4. If the player is still in the error state after the reset, you are advised to call **avPlayer.release()** to release resources and create an AVPlayer instance again.

## 5400103 I/O Error

**Error Message**

I/O error.

**Description**

An I/O error occurs.

**Possible Causes**

The data interaction between the media and other modules (graphics, audio, network, HDI, and camera) is abnormal.

**Solution**

Ensure that the network is normal, destroy this instance, and re-create it. If the re-creation fails, stop related operations.

### Scenario 1: The audio renderer fails to be started.

**Error Message**

I/O error: audio render failed.

**Description**

The audio renderer fails to be started.

**Possible Causes**

1. The audio output channel of the device is exclusively occupied by another app (for example, the device is in a call or recording audio). As a result, the audio renderer cannot obtain the output resources.
2. The audio stream parameter configuration (sampling rate, number of audio channels, and encoding format) does not match the source file or exceeds the range supported by the device. As a result, the renderer cannot be started based on the specified parameters.
3. The system audio service is abnormal or not properly initialized, and the audio Hardware Device Interface (HDI) driver fails to be loaded. As a result, the renderer fails to be created.

**Solution**

1. Check whether the audio output device (speaker or headset) is properly connected and whether the volume is not muted or set to 0.
2. Check whether another app is exclusively using the audio output channel (for example, during a call or recording). If so, wait until the channel is released before playing audio.
3. Check whether the parameter configuration (sampling rate, number of audio channels, and encoding format) of the audio stream matches the source file. If the parameters do not match, the renderer will fail to start.
4. If no exception is found after the preceding checks, call **avPlayer.release()** to destroy the current instance, create a new AVPlayer instance, and try to play the audio again.
5. If the error persists after the instance is recreated, you are advised to record detailed logs, stop the playback, and try again after the audio service of the system is restored.

### Scenario 2: The video decoder fails to be started or fails to decode the audio.

**Error Message**

I/O error: video decode failed.

**Description**

The video decoder fails to be started or fails to decode the audio.

**Possible Causes**

1. The encoding format (such as H.264, H.265, or VP8) of the video resources is not supported by the decoder of the current device, or the profile/level of the camera stream exceeds the hardware decoding capability.
2. The video stream data is incomplete or damaged, or the network is unstable, causing the loss of key frame data. As a result, the decoder cannot be started or continuously decode data.

   For example, when streaming media is played and the HLS returns an HTML segment (**content-Type** is set to **text/html**), the error message "errorCode 5400103, errorMsg IO Error: DEM_PARSE_ERR-unkown error, media data source error unknow, video/avc." is displayed.

3. The decoder is abnormal. **start** or **reset** is called when the player is in the error state, or the decoding fails due to insufficient or abnormal underlying HDI driver resources.

**Solution**

1. Check whether the encoding format (such as H.264, H.265, or VP8) of the video resources is supported by the system.
2. Check whether the camera stream parameters (resolution, frame rate, and profile/level) exceed the range supported by the hardware decoder. If so, use software decoding or reduce the data rate.
3. Check whether methods such as **start** or **reset** are called when the decoder is in an error state. Ensure that the correct state transition sequence is followed. For details, see [Using AVPlayer to Play Videos (ArkTS)](../../media/media/video-playback.md).
4. Check whether the network connection is stable. An unstable network may cause incomplete stream data, leading to decoding failures.
5. If no exception is found after the preceding checks, call **avPlayer.release()** to destroy the current instance, create a new AVPlayer instance, and try to play the audio again.
6. If the error persists after the instance is recreated, you are advised to record detailed logs, stop the playback, and check whether the error is caused by an HDI driver exception.

### Scenario 3: The video decoder fails to be initialized.

**Error Message**

I/O error: video mimeType Decode create failed.

**Description**

The video decoder fails to be initialized.

**Possible Causes**

1. The MIME type (such as video/avc or video/hevc) of the video resources is not supported by the current device, and the corresponding decoder instance cannot be created.
2. The encapsulation format of the video resources is not standard or the file is damaged. As a result, the decapsulator cannot correctly identify the MIME type, and the decoder fails to be created.
3. The available system resources are insufficient, for example, the available memory is insufficient or the GPU resources are fully occupied. As a result, the decoder plugin cannot be properly loaded or the required resources for initialization fail to be allocated.

**Solution**

1. Check whether the MIME type (such as video/avc or video/hevc) of the video resources is supported by the device.
2. Check whether the encapsulation format of the video resources is correct. If the encapsulation format is not standard or the encapsulation is damaged, the MIME type parsing may be abnormal, and the corresponding decoder instance cannot be created.
3. Check whether there are sufficient system resources (memory and GPU) for decoder initialization. If the memory is insufficient, the decoder may fail to be created.
4. If no exception is found after the preceding checks, call **avPlayer.release()** to destroy the current instance, create a new AVPlayer instance, and try to play the audio again.
5. If the error persists after the instance is recreated, you are advised to record detailed logs, stop the playback, and check whether the underlying decoder plugin is properly loaded.

### Scenario 4: Failed to open the file.

**Error Message**

I/O error: open file failed.

**Description**

Failed to open the file.

**Possible Causes**

1. The file path is incorrect or the file does not exist. The local path format is incorrect or the sandbox path is invalid. The network URL cannot be accessed.
2. The app has not obtained the necessary file access permission (such as **ohos.permission.READ_MEDIA**). As a result, the system rejects the file opening request.
3. The file is exclusively locked by another process or is being written. As a result, a concurrent access conflict occurs and the file fails to be opened.
4. The file is damaged or in an incorrect format. As a result, the decapsulator cannot correctly parse the file header information.
5. The network is not properly connected or the HTTP server is abnormal (such as 404, 403, or 500). As a result, the network file cannot be opened.

**Solution**

1. Check whether the file path is correct. Check whether the file exists and whether the path format is correct. For example, a local path starts with the sandbox path, and a network path starts with http:// or https://.
2. Check whether the app has obtained the file access permission. For local files, check whether the app has requested **ohos.permission.READ_MEDIA** or other necessary file read/write permissions.
3. Check whether the file is occupied or locked by another process. If the file is being written or exclusively accessed by another app, the file may fail to be opened.
4. Check whether the file is damaged. You are advised to use another player or tool to open the same file and check whether the file can be read properly.
5. If the file is a network file, check whether the network connection is normal and whether the HTTP request returns a correct response status code (such as 200) to rule out network timeout or server errors.
6. If no exception is found after the preceding checks, call **avPlayer.release()** to destroy the current instance, create a new AVPlayer instance, and try to play the audio again.
7. If the error persists after the instance is recreated, you are advised to record detailed logs, stop the playback, and check whether the underlying file system or network module is abnormal.

### Scenario 5: Failed to read data from or write data to the file.

**Error Message**

I/O error: file access failed.

**Description**

Failed to read data from or write data to the file.

**Possible Causes**

1. The app does not have the read/write permission on the file (such as **ohos.permission.READ_MEDIA** or **ohos.permission.WRITE_MEDIA**), and the system rejects the read/write request.
2. The device storage space is insufficient. When the disk is full or nearly full, read/write operations cannot be performed properly.
3. The file is modified or deleted by another process during the read/write operation. Concurrent access causes data inconsistency or read/write conflicts.
4. The file is damaged or incomplete. After the data verification fails, the read/write operation is interrupted.
5. The Internet connection of the network flow file is interrupted, and data transmission fails. As a result, an error is reported during the read operation.

**Solution**

1. Check whether the file access permission has been correctly granted and whether the app has requested the read/write permissions (such as **ohos.permission.READ_MEDIA** and **ohos.permission.WRITE_MEDIA**).
2. Check whether the file storage space is sufficient. If the disk space is insufficient, the read/write operation may fail.
3. Check whether the file is modified or deleted by another process during the read/write operation. Concurrent access may cause file content inconsistency or read/write conflicts.
4. Check whether the file is damaged. You are advised to download or restore the file before playing it again.
5. If the file is a network stream file, check whether the network connection is normal. Network interruption may cause data read failures.
6. If no exception is found after the preceding checks, call **avPlayer.release()** to destroy the current instance, create a new AVPlayer instance, and try to play the audio again.
7. If the error persists after the instance is recreated, you are advised to record detailed logs, stop the playback, and check whether the underlying file system or storage module is abnormal.

### Scenario 6: An I/O error occurs in the HTTP data source.

**Error Message**

I/O error: data source io error.

**Description**

An I/O error occurs in the HTTP data source.

**Possible Causes**

1. The Internet connection is abnormal (for example, Wi-Fi is disabled or the cellular signal is weak), and the device cannot access HTTP resources.
2. The HTTP server returns an error status code (for example, 404 indicating that the resource does not exist), and no valid data can be obtained from the data source.
3. The media resource URL is invalid or has expired, and the server resource is unreachable.
4. Data download is interrupted due to network fluctuation, the TCP connection is disconnected, or data packets are lost.
5. The HTTP request timeout interval is too short, causing frequent timeout interruptions in weak network environments.

**Solution**

1. Check whether the network connection is normal. Check the device's network connection status (Wi-Fi/cellular) and ensure that HTTP resources can be accessed.
2. Check the response status code of the HTTP request to rule out server errors (such as 404 indicating the resources cannot be found).
3. Check whether the media resource URL is correct and accessible. Try to access the URL directly in a browser or other network tools to verify that the resource is available.
4. Check whether the data download is interrupted due to network fluctuations. If possible, switch the network environment (for example, from cellular to Wi-Fi) and try again.
5. Check whether the timeout interval of the HTTP request is properly configured. If the timeout interval is too short, I/O errors may be frequently triggered in weak network environments.
6. If no exception is found after the preceding checks, call **avPlayer.release()** to destroy the current instance, create a new AVPlayer instance, and try to play the audio again.
7. If the error persists after the instance is recreated, you are advised to record detailed logs, stop the playback, and check whether the network module or HTTP protocol stack is abnormal.

### Scenario 7: The decapsulation cache is full.

**Error Message**

I/O error: demuxer buffer malloc failed.

**Description**

The decapsulation cache is full.

**Possible Causes**

1. The available memory of the device is insufficient. As a result, the decapsulation cache fails to be allocated, and no sufficient buffer space can be allocated for the stream data.
2. The bit rate of media resources is too high. High-bitrate data requires larger cache space, which exceeds the upper limit of the preset decapsulation buffer capacity.
3. Multiple player instances run concurrently. The decapsulation caches of these instances occupy the system memory at the same time, and the total cache requirement exceeds the available memory.
4. Insufficient network bandwidth causes data stacking. The download speed cannot keep up with the usage speed, and the cache keeps increasing until it overflows.

**Solution**

1. Check whether the available memory of the device is sufficient. If the memory is insufficient, the decapsulation cache may fail to be allocated. Close background apps to release memory and try again.
2. Check whether the bitrate of the media resource is too high. High-bitrate resources require larger cache space. Try playing a version with a lower bitrate.
3. Check whether the data download speed is slower than the playback speed due to insufficient network bandwidth. If the cache keeps stacking up and eventually overflows, try playing the content in a better network environment.
4. Check whether multiple player instances are running at the same time. If multiple instances occupy the cache concurrently, the total cache usage may exceed the limit. Reduce the number of concurrent instances and try again.
5. If no exception is found after the preceding checks, call **avPlayer.release()** to destroy the current instance, create a new AVPlayer instance, and try to play the audio again.
6. If the error persists after the instance is recreated, you are advised to record detailed logs, stop the playback, and check whether the underlying memory management module is abnormal.

### Scenario 8: The surface operation failed.

**Error Message**

I/O error: get input surface failed.

**Description**

The surface operation failed.

**Possible Causes**

1. **avPlayer.surfaceId** is called to set the surface when the AVPlayer status is incorrect. As a result, the request for obtaining the input surface fails.
2. The surface ID is invalid. **XComponent** or other components that can provide the surface are not correctly initialized, and the generated surface ID is unavailable.
3. The **BufferQueue** configuration of the surface is incorrect. The connection between the consumer (decoder) and the producer (renderer) is not properly established, and the input surface cannot be obtained.
4. The same surface is bound to multiple players or other components at the same time. As a result, the surface operation fails due to resource competition.
5. The underlying graphics module or surface management service is abnormal, and an error is returned when the surface-related API is called.

**Solution**

1. Check whether the AVPlayer is in the correct state (prepared or a state before prepared) before calling **avPlayer.surfaceId** to set the surface. If the state is incorrect, the surface may fail to be set.
2. Check whether the input surface ID is valid. Ensure that **XComponent** or other components that provide the surface have been correctly initialized and generated a valid surface ID.
3. Check whether the connection between the consumer (decoder) and producer (renderer) of the surface is normal.
4. Check whether multiple components are contending for the same surface resource. Ensure that the same surface is not bound to multiple players or other components at the same time.
5. If no exception is found after the preceding checks, call **avPlayer.release()** to destroy the current instance, create a new AVPlayer instance, and try to play the audio again.
6. If the error persists after the instance is recreated, you are advised to record detailed logs, stop the playback, and check whether the underlying graphics module or surface management service is abnormal.

### Scenario 9: Back-stop processing is processed on unknown errors.

**Error Message**

I/O error: unknown error.

**Description**

Back-stop processing is processed on unknown errors.

**Possible Causes**

1. The data interaction between the media and other modules (graphics, audio, network, HDI, and camera) is abnormal. An internal exception occurs in an associated module, causing an unpredictable I/O error.
2. System resources (CPU, memory, and GPU) are insufficient, and data transmission between modules times out or is lost.
3. The media resource file is incomplete or the format is incorrect, triggering an uncovered boundary exception.
4. The underlying driver or service is abnormal. The HDI fails to be called, but the error code is not correctly identified or classified by the upper layer.

**Solution**

1. View the complete log to check whether there are more specific error subtypes or errors reported by associated modules (such as graphics, audio, network, HDI, and camera). If so, check the errors reported by the associated modules first.
2. Check whether the network connection is normal. Some unknown errors may be indirectly caused by network exceptions.
3. Check whether the system resources (CPU, memory, and GPU) of the device are sufficient. Insufficient resources may cause abnormal interaction between modules.
4. Check whether the media resource file is complete and in the correct format. Damaged or non-standard resource files may trigger various unpredictable errors.
5. If the fault persists after the preceding checks, call **avPlayer.release()** to destroy the current instance, create a new AVPlayer instance, and try to play the video again.
6. If the error persists after the instance is recreated, you are advised to record detailed logs, stop the playback, and send the logs to the development team for further troubleshooting.

## 5400104 Operation Timeout

**Error Message**

Operation timeout.

**Description**

The operation timed out.

**Possible Causes**

1. The network connection times out. (The default network timeout period is 15 seconds, and the timer starts after the buffered event is reported.)
2. Accessing other modules times out.

**Solution**

1. Check whether the network is normal.
2. Destroy this instance and re-create it. If the re-creation fails, stop related operations.

## 5400105 Play Service Dead

**Error Message**

Service died.

**Description**

The playback service is dead.

**Possible Causes**

The playback service is dead.

**Solution**

Destroy this instance and re-create it. If the re-creation fails, stop related operations.

## 5400106 Format Not Supported

**Error Message**

Unsupported format.

**Description**

The format is not supported.

**Possible Causes**

The file format is not supported.

**Solution**

Use a supported format.

For details about the supported formats, see [Media Kit Overview](../../media/media/media-kit-intro.md).

### Scenario: Decapsulation fails.

**Error Message**

unsupport container format type.

**Description**

Decapsulation fails.

**Possible Causes**

1. The encapsulation format (such as MP4, MKV, FLV, or TS) of the media resource is not supported by the system.

   For example, when the player is used to play an AV1 video, the error message is "errorCode 5400106, errorMsg Unsupported Format: VID_DEC_ERR-unsupport interface, unsupport video decoder type, video/av1-."

2. The media resource file is damaged or incomplete. As a result, the decapsulator cannot correctly identify the container type.

   For example:

   (1) When the video file to be played is damaged (the mp4 ftyp header is normal, but the moov and media data are missing), the error message is "errorCode 5400106, errorMsg Unsupported Format: CONTAINER_ERR-unsupport interface, unsupport container format type, null-".

   (2) When an empty file is opened during playback, the error message is "errorCode 5400106, errorMsg Unsupported Format: CONTAINER_ERR-unsupport interface, unsupport container format type, null-".

   (3) When an MP4 file disguised as a text file is played, the error message is "errorCode 5400106, errorMsg Unsupported Format: CONTAINER_ERR-unsupport interface, unsupport container format type, null-".

3. The URL or file path of the media resource is incorrect, causing invalid data to be loaded.
4. The network stream resource data is incomplete due to network interruption. The decapsulator lacks key header information and cannot identify the format.
5. The resource contains DRM protection or other cryptographic mechanisms that cannot be normally parsed by a standard decapsulator.

**Solution**

1. Check whether the encapsulation format (such as MP4, MKV, FLV, or TS) of the media resource is supported by the system.
2. Check whether the media resource file is damaged or incomplete. Non-standard encapsulation may cause the decapsulator to fail to correctly identify the container type. You can use other playback tools to check whether the file can be played properly.
3. Check whether the URL or file path of the media resource is correct. An incorrect path may cause invalid data to be loaded, which will be identified by the decapsulator as an unsupported format.
4. For network stream resources, check whether the network connection is normal. Network interruption may cause incomplete data. The decapsulator cannot identify the format due to the lack of key header information.
5. Check whether the resource contains DRM protection or other cryptographic mechanisms. Encrypted resources may not be properly parsed by a standard decapsulator.
6. If no exception is found after the preceding checks, call **avPlayer.release()** to destroy the current instance, create a new AVPlayer instance, and try to play the audio again.
7. If the error persists after the instance is recreated, you are advised to record detailed logs, stop the playback, and check whether the underlying decapsulator is loaded abnormally or the supported format range is insufficient.

## 5400107 Audio Focus Conflict

**Error Message**

Audio interrupted.

**Description**

Recording fails due to audio focus conflicts.

**Possible Causes**

Another process occupies the audio focus.

**Solution**

Destroy the current instance and check whether another process is recording. If you can stop the other process, you can create the current instance again.

## 5400108 Parameter Value Out of Range

**Error Message**

The parameter check failed, parameter value out of range.

**Description**

The parameter check fails because the value is beyond the allowable range.

**Possible Causes**

The value of the parameter exceeds the expected range.

**Solution**

Adjust the parameter value to fall within the acceptable range.

<!--Del-->
## 5400109 Session ID Does Not Exist

**Error Message**

Sessions not exist. Return by promise.

**Description**

This error is reported when the session ID does not exists.

**Possible Causes**

The session ID does not exist.

**Solution**

Pass in a correct session ID.
<!--DelEnd-->

## 5411001 Failed to Parse or Connect to the Server Address

**Error Message**

Can not find host.

**Description**

An error occurred when parsing or connecting to the server address.

**Possible Causes**

1. The server address is incorrect.
2. The server address fails to be parsed.

**Solution**

Try another server address.

## 5411002 Network Connection Timeout

**Error Message**

Connection timeout.

**Description**

Network connection times out.

**Possible Causes**

The network is abnormal.

**Solution**

1. Check whether the network is normal.
2. Destroy this instance and re-create it. If the re-creation fails, stop related operations.

## 5411003 Data or Link Exception Caused by Network Exceptions

**Error Message**

Network abnormal.

**Description**

Data or links are abnormal due to network exceptions.

**Possible Causes**

The network is abnormal.

**Solution**

Destroy this instance and re-create it. If the re-creation fails, stop related operations.

## 5411004 Network Disabled

**Error Message**

Network unavailable.

**Description**

The network is unavailable.

**Possible Causes**

The network is disabled.

**Solution**

1. Check whether the network is disabled.
2. Destroy this instance and re-create it. If the re-creation fails, stop related operations.

## 5411005 Access Denied

**Error Message**

No permission.

**Description**

No access permission.

**Possible Causes**

No access permission.

**Solution**

1. Check whether you have the access permission.
2. Destroy this instance and re-create it. If the re-creation fails, stop related operations.

## 5411006 Client Request Parameter Is Incorrect or Exceeds the Processing Capability

**Error Message**

Network access denied.

**Description**

The client request parameter is incorrect or exceeds the processing capability.

**Possible Causes**

The client request parameter is incorrect or exceeds the processing capability.

**Solution**

1. Correct the request parameter.
2. Destroy this instance and re-create it. If the re-creation fails, stop related operations.

## 5411007 No Resource Available

**Error Message**

Cannot find available network resources.

**Description**

No network resource is available.

**Possible Causes**

The server address is abnormal.

**Solution**

1. Check whether the server address is correct.
2. Destroy this instance and re-create it. If the re-creation fails, stop related operations.

## 5411008 Server Fails to Verify the Client Certificate

**Error Message**

SSL client cert needed.

**Description**

The SSL client is untrusted, and the server fails to verify the client certificate.

**Possible Causes**

The certificate is not carried, is invalid, or has expired.

**Solution**

1. Check whether the SSL certificate is normal.
2. Destroy this instance and re-create it. If the re-creation fails, stop related operations.

## 5411009 SSL Connection Failed

**Error Message**

SSL connection failed.

**Description**

SSL connection failed.

**Possible Causes**

SSL connection failed.

**Solution**

1. Check whether the SSL connection has expired.
2. Destroy this instance and re-create it. If the re-creation fails, stop related operations.

## 5411010 Client Fails to Verify the Server Certificate

**Error Message**

SSL server cert untrusted.

**Description**

The SSL server is untrusted, and the client fails to verify the server certificate.

**Possible Causes**

The certificate is not carried, is invalid, or has expired.

**Solution**

1. Check whether the SSL certificate is normal.
2. Destroy this instance and re-create it. If the re-creation fails, stop related operations.

## 5411011 Unsupported Request Due to Network Protocol Errors

**Error Message**

Unsupported request.

**Description**

The client request parameter is incorrect or exceeds the processing capability.

**Possible Causes**

The client request parameter is incorrect or exceeds the processing capability.

**Solution**

1. Check whether the client request parameter is correct.
2. Destroy this instance and re-create it. If the re-creation fails, stop related operations.

## 5411012 Request Not Supported Due to HTTP Plaintext Interception

**Error Message**

Http cleartext traffic is not permitted.

**Description**

HTTP plaintext access is not allowed.

**Possible Causes**

The client has configured **forbidding HTTP plaintext access** for the related domain name in the **network_config.json** file.

**Solution**

1. Check whether HTTP plaintext access interception is performed for the related domain name in the **network_config.json** file.
2. If interception is not required, configure the domain name permission by referring to [Configuring Plaintext HTTP Access Permissions](../../network/http-request.md#configuring-plaintext-http-access-permissions).

## 5410002 Seek in SEEK_CONTINUOUS Mode Is Not Supported

**Error Message**

Seek continuous is unsupported.

**Description**

The media source or device does not support the seek operation in SEEK_CONTINUOUS mode.

**Possible Causes**

The media source or device does not support the seek operation in SEEK_CONTINUOUS mode.

**Solution**

1. This error code informs the client about the behavior when seeking is not supported in SEEK_CONTINUOUS mode. The client does not need to handle this.

## 5410003 Super Resolution Is Not Supported

**Error Message**

Super resolution not supported.

**Description**

The media source or device does not support super resolution.

**Possible Causes**

Super resolution is available only for non-HDR and non-DRM videos with a resolution of 1080p or lower. If the media source does not meet the super resolution requirements or the current device does not support super resolution, this error is reported when an API related to super resolution is called.

**Solution**

Do not call super resolution related APIs for the media source on the current device.

## 5410004 Super Resolution Is Not Enabled

**Error Message**

Super resolution not enabled.

**Description**

Super resolution is not enabled. As a result, super resolution related APIs are unavailable.

**Possible Causes**

Super resolution is not enabled by using [PlaybackStrategy](./arkts-apis-media-i.md#playbackstrategy12).

**Solution**

Enable super resolution before calling related APIs.
