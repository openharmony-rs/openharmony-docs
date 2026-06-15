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

  | Name| Type| Read-Only| Optional| Description|
  | -------- | -------- | -------- | -------- | -------- |
  | url | string | No| No| URL of the upload server.|
  | data | Array&lt;[RequestData](#requestdatadeprecated)&gt; | No| Yes| Form data in the request body.|
  | files | Array&lt;[RequestFile](#requestfiledeprecated)&gt; | No| No| List of files to upload, which is submitted through **multipart/form-data**.|
  | header | Object | No| Yes| Request header.|
  | method | string | No| Yes| Request method, which can be **'POST'** or **'PUT'**. The default value is **POST**.|
  | success | (data: [UploadResponse](#uploadresponsedeprecated)) => void | No| Yes| Called when API call is successful.|
  | fail | (data: any, code: number) => void | No| Yes| Called when API call has failed. Response headers and the HTTP status code are returned.|
  | complete | () => void | No| Yes| Called when API call is complete.|



## UploadResponse<sup>(deprecated)</sup>

**System capability**: SystemCapability.MiscServices.Upload

  | Name| Type| Read-Only| Optional| Description|
  | -------- | -------- | -------- | -------- | -------- |
  | code | number | No| No| HTTP status code returned by the server.|
  | data | string | No| No| Content returned by the server. The value type is determined by the type in the response header.|
  | headers | Object | No| No| Response headers returned by the server.|


## RequestFile<sup>(deprecated)</sup>

**System capability**: SystemCapability.MiscServices.Upload

  | Name| Type| Read-Only| Optional| Description|
  | -------- | -------- | -------- | -------- | -------- |
  | filename | string | No| Yes| File name in the header when **multipart** is used.|
  | name | string | No| Yes| Name of a form item when **multipart** is used. The default value is **file**.|
  | uri | string | No| No| Local path for storing files.|
  | type | string | No| Yes| Type of the file content. By default, the type is obtained based on the extension of the file name or URI.|


## RequestData<sup>(deprecated)</sup>

**System capability**: SystemCapability.MiscServices.Upload

  | Name| Type| Read-Only| Optional| Description|
  | -------- | -------- | -------- | -------- | -------- |
  | name | string | No| No| Name of the form element.|
  | value | string | No| No| Value of the form element.|



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
  | Name| Type| Read-Only| Optional| Description|
  | -------- | -------- | -------- | -------- | -------- |
  | url | string | No| No| Resource URL.|
  | filename | string | No| Yes| Name of the file to download. The value is obtained from the current request or resource URL by default.|
  | header | Object | No| Yes| Request header.|
  | description | string | No| Yes| Download description. The default value is the file name.|
  | success | (data: [DownloadResponse](#downloadresponsedeprecated)) => void | No| Yes| Called when API call is successful.|
  | fail | (data: any, code: number) => void | No| Yes| Called when API call has failed. Response headers and the HTTP status code are returned.|
  | complete | () => void | No| Yes| Called when API call is complete.|

## DownloadResponse<sup>(deprecated)</sup>

**System capability**: SystemCapability.MiscServices.Download

  | Name| Type| Read-Only| Optional| Description|
  | -------- | -------- | -------- | -------- | -------- |
  | token | string | No| No| Download token, which is used to obtain the download status|


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

  | Name| Type| Read-Only| Optional| Description|
  | -------- | -------- | -------- | -------- | -------- |
  | token | string | No| No| Result token returned by the download API.|
  | success | (data: [OnDownloadCompleteResponse](#ondownloadcompleteresponsedeprecated)) => void | No| Yes| Called when API call is successful.|
  | fail | (data: any, code: number) => void | No| Yes| Called when API call has failed. Response headers and the HTTP status code are returned.|
  | complete | () => void | No| Yes| Called when API call is complete.|


## OnDownloadCompleteResponse<sup>(deprecated)</sup>

**System capability**: SystemCapability.MiscServices.Download

  | Name| Type| Read-Only| Optional| Description|
  | -------- | -------- | -------- | -------- | -------- |
  | uri | string | No| No| URI of the download file.|
