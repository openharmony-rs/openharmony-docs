# @system.request (Upload and Download)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Request-->
<!--Owner: @huaxin05-->
<!--Designer: @hu-kai45-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->

The **system.request** module provides applications with basic upload and download capabilities.

> **NOTE**
> - The APIs of this module are deprecated since API version 9. You are advised to use [@ohos.request](js-apis-request.md) instead.
> 
> - The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import


```js
import { Request } from '@kit.BasicServicesKit';
```

## request.upload<sup>(deprecated)</sup>

upload(options: UploadRequestOptions): void

Uploads a file. This API returns no value.

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> This API has been supported since API version 3 and deprecated since API version 9. You are advised to use [request.uploadFile](js-apis-request.md#requestuploadfile9) instead.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [UploadRequestOptions](#uploadrequestoptionsdeprecated) | Yes| Upload configurations.|

**Example**

  ```js
  import  { Request, UploadRequestOptions, UploadResponse } from '@kit.BasicServicesKit';

  let uploadRequestOptions: UploadRequestOptions = {
    url: 'http://www.path.com',
    method: 'POST',
    files: [{
      filename: "test",
      name: "test",
      uri: "internal://cache/test.jpg",
      type: "jpg"
    }],
    data: [{
      name: "name123",
      value: "123"
    }],
    success: (data: UploadResponse) => {
      console.info('Succeeded in uploading, code:' + JSON.stringify(data.code));
    },
    fail: (data: string, code: number) => {
      console.info('Failed to upload, data: ' + data + 'code: ' + code);
    },
    complete: () => {
      console.info('Upload complete');
    }
  }

  try {
    Request.upload(uploadRequestOptions);
    console.info('Start Upload');
  } catch (err) {
    console.error('Failed to upload, err:' + err);
  }
  ```


## UploadRequestOptions<sup>(deprecated)</sup>

**System capability**: SystemCapability.MiscServices.Upload

> **NOTE**
>
> This API has been supported since API version 3 and deprecated since API version 9. You are advised to use [UploadConfig](js-apis-request.md#uploadconfig) instead.

**Parameters**
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| url | string | Yes| URL of the upload server.|
| data | Array&lt;[RequestData](#requestdatadeprecated)&gt; | No| Form data in the request body.|
| files | Array&lt;[RequestFile](#requestfiledeprecated)&gt; | Yes| List of files to upload, which is submitted through **multipart/form-data**.|
| header | Object | No| Request header.|
| method | string | No| Request method, which can be **'POST'** or **'PUT'**. The default value is **POST**.|
| success | Function | No| Called when API call is successful.|
| fail | Function | No| Called when API call has failed.|
| complete | Function | No| Called when API call is complete.|

**success parameter**
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| data | [UploadResponse](#uploadresponsedeprecated) | Yes| Information returned when the upload task is successful.|

**fail parameters**
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| data | any | Yes| Header information returned when the upload task fails.|
| code | number | Yes| HTTP status code returned when the upload task fails.|



## UploadResponse<sup>(deprecated)</sup>

**System capability**: SystemCapability.MiscServices.Upload

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| code | number | Yes| HTTP status code returned by the server.|
| data | string | Yes| Content returned by the server. The value type is determined by the type in the returned headers.|
| headers | Object | Yes| Headers returned by the server.|


## RequestFile<sup>(deprecated)</sup>

**System capability**: SystemCapability.MiscServices.Upload

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| filename | string | No| File name in the header when **multipart** is used.|
| name | string | No| Name of a form item when **multipart** is used. The default value is **file**.|
| uri | string | Yes| Local path for storing files.|
| type | string | No| Type of the file content. By default, the type is obtained based on the extension of the file name or URI.|


## RequestData<sup>(deprecated)</sup>

**System capability**: SystemCapability.MiscServices.Upload

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Name of the form element.|
| value | string | Yes| Value of the form element.|



## request.download<sup>(deprecated)</sup>

download(options: DownloadRequestOptions): void

Downloads a file. This API returns no value.

**System capability**: SystemCapability.MiscServices.Download

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [DownloadRequestOptions](#downloadrequestoptionsdeprecated) | Yes| Download configurations.|

**Example**

  ```js
  import  { Request, DownloadResponse, DownloadRequestOptions } from '@kit.BasicServicesKit';

  let downloadRequestOptions: DownloadRequestOptions = {
    url: 'http://www.path.com',
    filename: 'requestSystemTest',
    header: "",
    description: 'this is requestSystem download response',
    success: (data: DownloadResponse) => {
      console.info('Succeeded in downloading, code:' + JSON.stringify(data));
    },
    fail: (data: string, code: number) => {
      console.info('Failed to download, data: ' + data + 'code: ' + code);
    },
    complete: () => {
      console.info('Download complete');
    }
  }

  try {
    Request.download(downloadRequestOptions);
    console.info('Start download');
  } catch(err) {
    console.error('Failed to download, err:' + err);
  }
  ```


## DownloadRequestOptions<sup>(deprecated)</sup>

**System capability**: SystemCapability.MiscServices.Download

> **NOTE**
>
> This API has been supported since API version 3 and deprecated since API version 9. You are advised to use [UploadConfig](js-apis-request.md#uploadconfig) instead.

**Parameters**
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| url | string | Yes| Resource URL.|
| filename | string | No| Name of the file to download. The value is obtained from the current request or resource URL by default.|
| header | Object | No| Request header.|
| description | string | No| Download description. The default value is the file name.|
| success | Function | No| Called when API call is successful.|
| fail | Function | No| Called when API call has failed.|
| complete | Function | No| Called when API call is complete.|

**success parameter**
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| data | [DownloadResponse](#downloadresponsedeprecated) | Yes| Information returned when the download task is successful.|

**fail parameters**
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| data | any | Yes| Header information returned when the download task fails.|
| code | number | Yes| HTTP status code returned when the download task fails.|

## DownloadResponse<sup>(deprecated)</sup>

**System capability**: SystemCapability.MiscServices.Download

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| token | string | Yes| Download token, which is used to obtain the download status|


## request.onDownloadComplete<sup>(deprecated)</sup>

onDownloadComplete(options: OnDownloadCompleteOptions): void

Listens for download task status. This API returns no value.

**System capability**: SystemCapability.MiscServices.Download

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [OnDownloadCompleteOptions](#ondownloadcompleteoptionsdeprecated) | Yes| Configurations of the download task.|

**Example**

  ```js
  import  { Request, OnDownloadCompleteOptions, OnDownloadCompleteResponse } from '@kit.BasicServicesKit';

  let onDownloadCompleteOptions: OnDownloadCompleteOptions = {
    token: 'token-index',
    success: (data: OnDownloadCompleteResponse) => {
      console.info('Succeeded in downloading, uri:' + JSON.stringify(data.uri));
    },
    fail: (data: string, code: number) => {
      console.info('Failed to download, data: ' + data + 'code: ' + code);
    },
    complete: () => {
      console.info('Download complete');
    }
  }

  Request.onDownloadComplete(onDownloadCompleteOptions);
  ```


## OnDownloadCompleteOptions<sup>(deprecated)</sup>

**System capability**: SystemCapability.MiscServices.Download

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| token | string | Yes| Result token returned by the download API.|
| success | Function | No| Called when API call is successful.|
| fail | Function | No| Called when API call has failed.|
| complete | Function | No| Called when API call is complete.|

**success parameter**
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| data | [OnDownloadCompleteResponse](#ondownloadcompleteresponsedeprecated) | Yes| Information returned when the download task is successful.|

**fail parameters**
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| data | any | Yes| Header information returned when the download task fails.|
| code | number | Yes| HTTP status code returned when the download task fails.|


## OnDownloadCompleteResponse<sup>(deprecated)</sup>

**System capability**: SystemCapability.MiscServices.Download

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| uri | string | Yes| URI of the download file.|
