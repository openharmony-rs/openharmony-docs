# Using AVPlayer to Set Playback URLs (ArkTS)

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chennotfound-->
<!--Designer: @chennotfound-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=8271a110bebcf2bb1afba336b05927aaf3c6256b translatedAt=2026-11-05T06:16:33.957Z pushedAt=2026-08-11T12:38:03.121Z nl=1 -->

This topic describes how to use the AVPlayer to set URLs in different playback scenarios.

This guide focuses only on the methods for setting playback URLs. For other scenarios and comprehensive sample code, see [Video Playback](video-playback.md).

This guide describes the following scenarios:

- [Setting URLs for Streaming Media Playback](#setting-urls-for-streaming-media-playback)

- [Setting URLs for Local Raw File Playback](#setting-urls-for-local-raw-file-playback)

## Setting URLs for Streaming Media Playback

**Case 1: playing HTTP/HTTPS media assets**

<!-- @[HTTP-HTTPS](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSURL/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let url = "https://vd3.bdstatic.com/mda-pdc2kmwtd2vxhiy4/cae_h264/1681502407203843413/mda-pdc2kmwtd2vxhiy4.mp4";
   this.avPlayer.url = url;
   ```

**Case 2: playing HLS media assets (VOD/live streaming)**

<!-- @[HLS](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSURL/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let url = 'http://media.iyuns.top:1000/720-270-480.m3u8';
   this.avPlayer.url = url;
   ```

**Case 3: setting the HTTP request header information for playback**

If the server needs to verify the HTTP request header, you can set the HTTP request header information through [createMediaSourceWithUrl](../../reference/apis-media-kit/arkts-apis-media-f.md#mediacreatemediasourcewithurl12).

<!-- @[HTTP-Head](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSURL/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let url = 'https://vd3.bdstatic.com/mda-nmh2004d24kf4bjh/hd/h264/1671326683061787710/mda-nmh2004d24kf4bjh.mp4';
   // Create a mediaSource instance to set the media source and customize the HTTP request. If required, set fields such as User-Agent, Cookie, and Referer as key-value pairs.
   let mediaSource : media.MediaSource = media.createMediaSourceWithUrl(url,  {'aa' : 'bb', 'cc' : 'dd'});
   // Set the playback strategy with a buffer duration of 20 seconds.
   let playbackStrategy : media.PlaybackStrategy =
     {preferredWidth: 1, preferredHeight: 2, preferredBufferDuration: 3, preferredHdr: false};
   // Set the media source and playback strategy for avPlayer.
   this.avPlayer.setMediaSource(mediaSource, playbackStrategy);
   ```

**Case 4: playing an online streaming media asset by parsing an M3U8 file in the local raw file folder**

If an application needs to play an online streaming media asset by parsing an M3U8 file in the local raw file folder, the application can obtain the file descriptor through [resourceManager.getRawFd](../../reference/apis-localization-kit/js-apis-resource-manager.md#getrawfd9), combine the file descriptor into fdUrl, and set the MIME type to **APPLICATION_M3U8** through [setMimeType](../../reference/apis-media-kit/arkts-apis-media-MediaSource.md#setmimetype12).

<!-- @[raw-m3u8](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSURL/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Obtain the file descriptor using the local m3u8 file name.
   let fileDescriptor = await this.context.resourceManager.getRawFd(this.m3u8FileName);
   // Construct the URL of the local m3u8 file using the file descriptor.
   let fdUrl : string = "fd://" + fileDescriptor.fd +
     "?offset=" + fileDescriptor.offset + "&size=" + fileDescriptor.length;
   // Set HTTP request headers as required.
   let headers : Record<string,string> = {"User-Agent" : "User-Agent-Value", "Cookie" : "Cookie-Value"};
   // Create a mediaSource using the local m3u8 URL and HTTP request headers.
   let mediaSource : media.MediaSource = media.createMediaSourceWithUrl(fdUrl, headers);
   
   // Set the media MIME type to APPLICATION_M3U8.
   let mimeType : media.AVMimeTypes = media.AVMimeTypes.APPLICATION_M3U8;
   mediaSource.setMimeType(mimeType);
   
   // Set the playback strategy with a buffer duration of 20 seconds.
   let playbackStrategy : media.PlaybackStrategy = {preferredBufferDuration: 20};
   // Set the media source and playback strategy for avPlayer.
   this.avPlayer.setMediaSource(mediaSource, playbackStrategy);
   ```

**Case 5: playing an online streaming media asset by parsing an M3U8 file in the application sandbox**

If an application needs to play an online streaming media asset by parsing an M3U8 file in the application sandbox, the application can obtain the file handle through [fileIo.openSync](../../reference/apis-core-file-kit/js-apis-file-fs.md#fileioopensync), combine the file handle into fdUrl, and set the MIME type to **APPLICATION_M3U8** through [setMimeType](../../reference/apis-media-kit/arkts-apis-media-MediaSource.md#setmimetype12).

<!-- @[fd-m3u8](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSURL/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let filePath = `${this.context.filesDir}/${this.m3u8FileName}`;
   // Obtain the file handle using fs.openSync.
   let file = fs.openSync(filePath, fs.OpenMode.READ_ONLY);
   let fd : string = file.fd.toString();
   // Construct the URL of the local m3u8 file using the file handle.
   let fdUrl : string = "fd://" + fd + "?offset=" + "0" + "&size=" + "0";
   
   // Set HTTP request headers as required.
   let headers : Record<string,string> = {"User-Agent" : "User-Agent-Value", "Cookie" : "Cookie-Value"};
   // Create a mediaSource using the local m3u8 URL and HTTP request headers.
   let mediaSource : media.MediaSource = media.createMediaSourceWithUrl(fdUrl, headers);
   
   // Set the media MIME type to APPLICATION_M3U8.
   let mimeType : media.AVMimeTypes = media.AVMimeTypes.APPLICATION_M3U8;
   mediaSource.setMimeType(mimeType);
   
   // Set the playback strategy with a buffer duration of 20 seconds.
   let playbackStrategy : media.PlaybackStrategy = {preferredBufferDuration: 20};
   // Set the media source and playback strategy for avPlayer.
   this.avPlayer.setMediaSource(mediaSource, playbackStrategy);
   ```

## Setting URLs for Local Raw File Playback

**Case 1: application sandbox file playback**

<!-- @[raw-url](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSURL/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   let fdPath = 'fd://';
   // Obtain the sandbox path filesDir through UIAbilityContext. The stage model is used as an example.
   let path = `${this.context.filesDir}/${this.fileName}`;
   // Open the resource file to obtain its fd and set url to trigger the initialized state.
   let file = await fs.open(path);
   fdPath = fdPath + '' + file.fd;
   this.avPlayer.url = fdPath;
   ```

**Case 2: local file playback**

> **NOTE**
> When the AVPlayer is used to play local resources, it exclusively occupies the file descriptor.

<!-- @[fdSrc](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSURL/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Call getRawFd of resourceManager in UIAbilityContext to obtain the media resource address.
   // The return value is {fd,offset,length}: fd is the HAP file descriptor, offset is the media resource offset, and length is the playback length.
   let fileDescriptor = await this.context.resourceManager.getRawFd(this.fileName);
   let avFileDescriptor: media.AVFileDescriptor =
     { fd: fileDescriptor.fd, offset: fileDescriptor.offset, length: fileDescriptor.length };
   // Set fdSrc to trigger the initialized state.
   this.avPlayer.fdSrc = avFileDescriptor;
   ```

## Running the Sample Project

1. Create a project, download the [sample project](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerArkTSURL), and copy its resources to the corresponding directories. You can also directly run the sample project.

    ```txt
    AVPlayerArkTSURL
    entry/src/main/ets/
    └── pages
        └── Index.ets (playback page)
    entry/src/main/resources/
    ├── base
    │   ├── element
    │   │   ├── color.json
    │   │   ├── float.json
    │   │   └── string.json
    │   └── media
    │       ├── ic_video_play.svg (play button image resource)
    │       └── ic_video_pause.svg (pause button image resource)
    └── rawfile
        ├── test.m3u8 (m3u8 resource)
        └── test_01.mp3 (audio resource)
    ```

2. Request the network permission in the **/entry/src/main/module.json5** file. Alternatively, replace the **module.json5** file with that in the sample project.

    ```json
    "requestPermissions": [
      {
        "name": "ohos.permission.INTERNET"
      },
      {
        "name": "ohos.permission.GET_WIFI_INFO"
      }
    ]
    ```

3. Comment out or uncomment the above examples in the **entry/src/main/ets/pages/Index.ets** file, and compile and run the application.

4. After installing the app, you can add the sample project's **/entry/src/main/resources/rawfile/test.m3u8** to the application sandbox using the following command to run the application sandbox-related examples: (```<FILESDIR>``` is the physical path. Taking the sample project as an example, you can obtain the application sandbox path by printing **this.context.filesDir** using **console.info**, and then find the physical path based on the ```application sandbox path and physical path mapping table``` in the [application sandbox guide](../../file-management/app-sandbox-directory.md)).

    ```txt
    hdc file send "[Directory]\test.m3u8" <FILESDIR>
    hdc file send "[Directory]\test_01.mp3" <FILESDIR>
    ```