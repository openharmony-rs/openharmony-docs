# @system.file (File Storage)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @liuhonggang123; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

> **NOTE**
>
> - Module maintenance policy:
>   - For lite wearables, this module is constantly maintained and available.
>   - For other device types, this module is no longer maintained since API version 10, and you are advised to use [`@ohos.file.fs`](js-apis-file-fs.md) instead.
> - The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import file from '@system.file';
```


## file.move

move(Object): void

Moves a specified file to a given location.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.moveFile](js-apis-file-fs.md#fileiomovefile) instead.

**System Capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| srcUri | string | Yes| URI of the file to move. The value can contain a maximum of 128 characters, excluding the following characters: "\*+,:;&lt;=&gt;?[]\|\x7F.|
| dstUri | string | Yes| URI of the location to which the file is to move. The value can contain a maximum of 128 characters, excluding the following characters: "\*+,:;&lt;=&gt;?[]\|\x7F.|
| success | Function | No| Callback invoked when the API call is successful. This API returns the URI of the destination location.|
| fail | Function | No| Callback invoked when the API call fails.|
| complete | Function | No| Callback invoked when the API call is complete.|

**Error codes**

| Error Code| Description|
| -------- | -------- |
| 202 | Incorrect parameters are detected.|
| 300 | An I/O error occurs.|
| 301 | The file or directory does not exist.|

**ArkTS Example:**

```ts
import file from '@system.file';

export default {    
  move() {        
    file.move({            
      srcUri: 'internal://app/myfiles1',            
      dstUri: 'internal://app/myfiles2',            
      success: function(uri) {                
        console.info('call success callback success');            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },        
    });    
  }
}
```

**JS Example:**

```xml
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="move" class="button" onclick="move"></input>
</div>
```

```css
/* xxx.css */
.container {
  display: flex;
  justify-content: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}

.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}

.button {
  font-size: 30px;
  text-align: center;
  width: 250px;
  height: 60px;
  background-color: #0078D7;
  color: white;
  border-radius: 5px;
}
```

```js
// xxx.js
import file from '@system.file';

export default {
  move() {
    file.move({
      srcUri: 'internal://app/myfiles1',
      dstUri: 'internal://app/myfiles2',
      success: function(uri) {
        console.info('call success callback success');
      },
      fail: function(data, code) {
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);
      },
    });
  }
}
```


## file.copy

copy(Object): void

Copies a file to the given URI.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.copyFile](js-apis-file-fs.md#fileiocopyfile) instead.

**System Capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| srcUri | string | Yes| URI of the file to copy.|
| dstUri | string | Yes| URI of the location to which the copy is to be saved.<br>The directory of application resources and URI of the **tmp** type are not supported.|
| success | Function | No| Callback invoked when the API call is successful. This API returns the URI of the destination location.|
| fail | Function | No| Callback invoked when the API call fails.|
| complete | Function | No| Callback invoked when the API call is complete.|

**Error codes**

| Error Code| Description|
| -------- | -------- |
| 202 | Incorrect parameters are detected.|
| 300 | An I/O error occurs.|
| 301 | The file or directory does not exist.|

**ArkTS Example:**

```ts
import file from '@system.file';

export default {    
  copy() {        
    file.copy({            
      srcUri: 'internal://app/file.txt',            
      dstUri: 'internal://app/file_copy.txt',            
      success: function(uri) {                
        console.info('call success callback success');            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },
    });    
  }
}
```

**JS Example:**

```xml
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="copy" class="button" onclick="copy"></input>
</div>
```

```css
/* xxx.css */
.container {
  display: flex;
  justify-content: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}

.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}

.button {
  font-size: 30px;
  text-align: center;
  width: 250px;
  height: 60px;
  background-color: #0078D7;
  color: white;
  border-radius: 5px;
}
```

```js
// xxx.js
import file from '@system.file';

export default {    
  copy() {        
    file.copy({            
      srcUri: 'internal://app/file.txt',            
      dstUri: 'internal://app/file_copy.txt',            
      success: function(uri) {                
        console.info('call success callback success');            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },
    });    
  }
}
```


## file.list

list(Object): void

Obtains all files in the specified directory.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.listFile](js-apis-file-fs.md#fileiolistfile) instead.

**System Capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| uri | string | Yes| URI of the directory. The value can contain a maximum of 128 characters, excluding the following characters: "\*+,:;&lt;=&gt;?[]\|\x7F.|
| success | Function | No| Callback invoked when the API call is successful.|
| fail | Function | No| Callback invoked when the API call fails.|
| complete | Function | No| Callback invoked when the API call is complete.|

**Return value of success()**

| Name| Type| Description|
| -------- | -------- | -------- |
| fileList | Array&lt;FileInfo&gt; | File list. The format of each file is as follows:<br>{<br>uri:'file1',<br>lastModifiedTime:1589965924479,<br>length:10240,<br>type:&nbsp;'file'<br>} |

**Table 1** FileInfo

| Name| Type| Description|
| -------- | -------- | -------- |
| uri | string | URI of the file.|
| lastModifiedTime | number | Timestamp when the file is stored the last time, which is the number of milliseconds elapsed since 1970/01/01 00:00:00 GMT.|
| length | number | File size, in bytes.|
| type | string | File type. Available values are as follows:<br>- &nbsp;**dir**: directory<br>-&nbsp;**file**: file|

**Error codes**

| Error Code| Description|
| -------- | -------- |
| 202 | Incorrect parameters are detected.|
| 300 | An I/O error occurs.|
| 301 | The file or directory does not exist.|

**ArkTS Example:**

```ts
import file from '@system.file';

export default {    
  list() {        
    file.list({            
      uri: 'internal://app/pic',            
      success: function(data) {                
        console.info(JSON.stringify(data.fileList));            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },        
    });    
  }
}
```

**JS Example:**

```xml
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="list" class="button" onclick="list"></input>
</div>
```

```css
/* xxx.css */
.container {
  display: flex;
  justify-content: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}

.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}

.button {
  font-size: 30px;
  text-align: center;
  width: 250px;
  height: 60px;
  background-color: #0078D7;
  color: white;
  border-radius: 5px;
}
```

```js
// xxx.js
import file from '@system.file';

export default {    
  list() {        
    file.list({            
      uri: 'internal://app/pic',            
      success: function(data) {                
        console.info(JSON.stringify(data.fileList));            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },        
    });    
  }
}
```


## file.get

get(Object): void

Obtains information about a local file.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.stat](js-apis-file-fs.md#fileiostat) instead.

**System Capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| uri | string | Yes| URI of the file.|
| recursive | boolean | No| Whether to obtain the subdirectory file list recursively. The value **true** means to obtain the subdirectory file list recursively; the value **false** means the opposite.|
| success | Function | No| Callback invoked when the API call is successful.|
| fail | Function | No| Callback invoked when the API call fails.|
| complete | Function | No| Callback invoked when the API call is complete.|

**Return value of success()**

| Name| Type| Description|
| -------- | -------- | -------- |
| uri | string | URI of the file.|
| length | number | File length, in bytes.|
| lastModifiedTime | number | Timestamp when the file is stored the last time, which is the number of milliseconds elapsed since 1970/01/01 00:00:00 GMT.|
| type | string | File type. Available values are as follows:<br>-&nbsp;**dir**: directory<br>-&nbsp;**file**: file|
| subFiles | Array | List of files.|

**Error codes**

| Error Code| Description|
| -------- | -------- |
| 202 | Incorrect parameters are detected.|
| 300 | An I/O error occurs.|
| 301 | The file or directory does not exist.|

**ArkTS Example:**

```ts
import file from '@system.file';

export default {    
  get() {        
    file.get({            
      uri: 'internal://app/file',            
      success: function(data) {                
        console.info(data.uri);            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },
    });    
  }
}
```

**JS Example:**

```xml
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="get" class="button" onclick="get"></input>
</div>
```

```css
/* xxx.css */
.container {
  display: flex;
  justify-content: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}

.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}

.button {
  font-size: 30px;
  text-align: center;
  width: 250px;
  height: 60px;
  background-color: #0078D7;
  color: white;
  border-radius: 5px;
}
```

```js
// xxx.js
import file from '@system.file';

export default {    
  get() {        
    file.get({            
      uri: 'internal://app/file',            
      success: function(data) {                
        console.info(data.uri);            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },
    });    
  }
}
```


## file.delete

delete(Object): void

Deletes a local file.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.unlink](js-apis-file-fs.md#fileiounlink) instead.

**System Capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| uri | string | Yes| URI of the file to delete. It cannot be an application resource path.|
| success | Function | No| Callback invoked when the API call is successful.|
| fail | Function | No| Callback invoked when the API call fails.|
| complete | Function | No| Callback invoked when the API call is complete.|

**Error codes**

| Error Code| Description|
| -------- | -------- |
| 202 | Incorrect parameters are detected.|
| 300 | An I/O error occurs.|
| 301 | The file or directory does not exist.|

**ArkTS Example:**

```ts
import file from '@system.file';

export default {    
  delete() {        
    file.delete({            
      uri: 'internal://app/my_file',            
      success: function() {                
        console.info('call delete success.');            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },
    });    
  }
}
```

**JS Example:**

```xml
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="delete" class="button" onclick="delete"></input>
</div>
```

```css
/* xxx.css */
.container {
  display: flex;
  justify-content: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}

.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}

.button {
  font-size: 30px;
  text-align: center;
  width: 250px;
  height: 60px;
  background-color: #0078D7;
  color: white;
  border-radius: 5px;
}
```

```js
// xxx.js
import file from '@system.file';

export default {    
  delete() {        
    file.delete({            
      uri: 'internal://app/my_file',            
      success: function() {                
        console.info('call delete success.');            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },
    });    
  }
}
```


## file.writeText

writeText(Object): void

Writes text into a file. Only text files can be read and written.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.write](js-apis-file-fs.md#fileiowrite) instead.

**System Capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| uri | string | Yes| URI of a local file. If it does not exist, a file will be created.|
| text | string | Yes| String to write into the file.|
| encoding | string | No| Encoding format. The default format is **UTF-8**.|
| append | boolean | No| Whether to enable the append mode. The default value is **false**. The value **true** means to enable the append mode; the value **false** means the opposite.|
| success | Function | No| Callback invoked when the API call is successful.|
| fail | Function | No| Callback invoked when the API call fails.|
| complete | Function | No| Callback invoked when the API call is complete.|

**Error codes**

| Error Code| Description|
| -------- | -------- |
| 202 | Incorrect parameters are detected.|
| 300 | An I/O error occurs.|

**ArkTS Example:**

```ts
import file from '@system.file';

export default {    
  writeText() {        
    file.writeText({            
      uri: 'internal://app/test.txt',            
      text: 'Text that just for test.',            
      success: function() {                
        console.info('call writeText success.');            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },        
    });    
  }
}
```

**JS Example:**

```xml
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="writeText" class="button" onclick="writeText"></input>
</div>
```

```css
/* xxx.css */
.container {
  display: flex;
  justify-content: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}

.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}

.button {
  font-size: 30px;
  text-align: center;
  width: 250px;
  height: 60px;
  background-color: #0078D7;
  color: white;
  border-radius: 5px;
}
```

```js
// xxx.js
import file from '@system.file';

export default {    
  writeText() {        
    file.writeText({            
      uri: 'internal://app/test.txt',            
      text: 'Text that just for test.',            
      success: function() {                
        console.info('call writeText success.');            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },        
    });    
  }
}
```


## file.writeArrayBuffer

writeArrayBuffer(Object): void

Writes buffer data into a file. Only text files can be read and written.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.write](js-apis-file-fs.md#fileiowrite) instead.

**System Capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| uri | string | Yes| URI of a local file. If it does not exist, a file will be created.|
| buffer | Uint8Array | Yes| Buffer from which the data is derived.|
| position | number | No| Offset to the position where the writing starts, in bytes. The default value is **0**.|
| append | boolean | No| Whether to enable the append mode. The default value is **false**. If the value is **true**, the **position** parameter will become invalid. The value **true** means to enable the append mode; the value **false** means the opposite.|
| success | Function | No| Callback invoked when the API call is successful.|
| fail | Function | No| Callback invoked when the API call fails.|
| complete | Function | No| Callback invoked when the API call is complete.|

**Error codes**

| Error Code| Description|
| -------- | -------- |
| 202 | Incorrect parameters are detected.|
| 300 | An I/O error occurs.|

**ArkTS Example:**

```ts
import file from '@system.file';

export default {    
  writeArrayBuffer() {       
    file.writeArrayBuffer({           
      uri: 'internal://app/test',           
      buffer: new Uint8Array(8),// The buffer is of the Uint8Array type.
      success: function() {                
        console.info('call writeArrayBuffer success.');            
      },           
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },
    });    
  }
}
```

**JS Example:**

```xml
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="writeArrayBuffer" class="button" onclick="writeArrayBuffer"></input>
</div>
```

```css
/* xxx.css */
.container {
  display: flex;
  justify-content: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}

.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}

.button {
  font-size: 30px;
  text-align: center;
  width: 250px;
  height: 60px;
  background-color: #0078D7;
  color: white;
  border-radius: 5px;
}
```

```js
// xxx.js
import file from '@system.file';

export default {    
  writeArrayBuffer() {       
    file.writeArrayBuffer({           
      uri: 'internal://app/test',           
      buffer: new Uint8Array(8),// The buffer is of the Uint8Array type.
      success: function() {                
        console.info('call writeArrayBuffer success.');            
      },           
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },
    });    
  }
}
```


## file.readText

readText(Object): void

Reads text from a file. Only text files can be read and written.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.readText](js-apis-file-fs.md#fileioreadtext) instead.

**System Capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| uri | string | Yes| URI of a local file.|
| encoding | string | No| Encoding format. The default format is **UTF-8**.|
| position | number | No| Position where the reading starts, in bytes. The default value is the start position of the file.|
| length | number | No| Length of the text to be read, in bytes. The default value is **4096**.|
| success | Function | No| Callback invoked when the API call is successful.|
| fail | Function | No| Callback invoked when the API call fails.|
| complete | Function | No| Callback invoked when the API call is complete.|

**Return value of success()**

| Name| Type| Description|
| -------- | -------- | -------- |
| text | string | Text read from the specified file.|

**Error codes**

| Error Code| Description|
| -------- | -------- |
| 202 | Incorrect parameters are detected.|
| 300 | An I/O error occurs.|
| 301 | The file or directory does not exist.|
| 302 | The text to read exceeds 4 KB.|

**ArkTS Example:**

```ts
import file from '@system.file';

export default {    
  readText() {        
    file.readText({            
      uri: 'internal://app/text.txt',            
      success: function(data) {                
        console.info('call readText success: ' + data.text);            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },        
    });    
  }
}
```

**JS Example:**

```xml
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="readText" class="button" onclick="readText"></input>
</div>
```

```css
/* xxx.css */
.container {
  display: flex;
  justify-content: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}

.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}

.button {
  font-size: 30px;
  text-align: center;
  width: 250px;
  height: 60px;
  background-color: #0078D7;
  color: white;
  border-radius: 5px;
}
```

```js
// xxx.js
import file from '@system.file';

export default {    
  readText() {        
    file.readText({            
      uri: 'internal://app/text.txt',            
      success: function(data) {                
        console.info('call readText success: ' + data.text);            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },        
    });    
  }
}
```


## file.readArrayBuffer

readArrayBuffer(Object): void

Reads buffer data from a file. Only text files can be read and written.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.read](js-apis-file-fs.md#fileioread) instead.

**System Capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| uri | string | Yes| URI of a local file.|
| position | number | No| Position where the reading starts, in bytes. The default value is the start position of the file.|
| length | number | No| Length of data to read, in bytes. If this parameter is not set, the reading proceeds until the end of the file.|
| success | Function | No| Callback invoked when the API call is successful.|
| fail | Function | No| Callback invoked when the API call fails.|
| complete | Function | No| Callback invoked when the API call is complete.|

**Return value of success()**

| Name| Type| Description|
| -------- | -------- | -------- |
| buffer | Uint8Array | Data read.|

**Error codes**

| Error Code| Description|
| -------- | -------- |
| 202 | Incorrect parameters are detected.|
| 300 | An I/O error occurs.|
| 301 | The file or directory does not exist.|

**ArkTS Example:**

```ts
import file from '@system.file';

export default {    
  readArrayBuffer() {        
    file.readArrayBuffer({            
      uri: 'internal://app/test',            
      position: 10,            
      length: 200,            
      success: function(data) {                
        console.info('call readArrayBuffer success: ' + data.buffer);            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },
    });    
  }
}
```

**JS Example:**

```xml
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="readArrayBuffer" class="button" onclick="readArrayBuffer"></input>
</div>
```

```css
/* xxx.css */
.container {
  display: flex;
  justify-content: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}

.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}

.button {
  font-size: 30px;
  text-align: center;
  width: 250px;
  height: 60px;
  background-color: #0078D7;
  color: white;
  border-radius: 5px;
}
```

```js
// xxx.js
import file from '@system.file';

export default {    
  readArrayBuffer() {        
    file.readArrayBuffer({            
      uri: 'internal://app/test',            
      position: 10,            
      length: 200,            
      success: function(data) {                
        console.info('call readArrayBuffer success: ' + data.buffer);            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },
    });    
  }
}
```


## file.access

access(Object): void

Checks whether a file or directory exists.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.access](js-apis-file-fs.md#fileioaccess) instead.

**System Capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| uri | string | Yes| URI of the directory or file to check.|
| success | Function | No| Callback invoked when the API call is successful.|
| fail | Function | No| Callback invoked when the API call fails.|
| complete | Function | No| Callback invoked when the API call is complete.|

**Error codes**

| Error Code| Description|
| -------- | -------- |
| 202 | Incorrect parameters are detected.|
| 300 | An I/O error occurs.|
| 301 | The file or directory does not exist.|

**ArkTS Example:**

```ts
import file from '@system.file';

export default {    
  access() {        
    file.access({            
      uri: 'internal://app/test',            
      success: function() {                
        console.info('call access success.');            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },        
    });    
  }
}
```

**JS Example:**

```xml
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="access" class="button" onclick="access"></input>
</div>
```

```css
/* xxx.css */
.container {
  display: flex;
  justify-content: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}

.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}

.button {
  font-size: 30px;
  text-align: center;
  width: 250px;
  height: 60px;
  background-color: #0078D7;
  color: white;
  border-radius: 5px;
}
```

```js
// xxx.js
import file from '@system.file';

export default {    
  access() {        
    file.access({            
      uri: 'internal://app/test',            
      success: function() {                
        console.info('call access success.');            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },        
    });    
  }
}
```


## file.mkdir

mkdir(Object): void

Creates a directory.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.mkdir](js-apis-file-fs.md#fileiomkdir) instead.

**System Capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| uri | string | Yes| URI of the directory to delete.|
| recursive | boolean | No| Whether to recursively create the upper-level directory of the specified directory. The default value is **false**. The value **true** means to create upper-level directory recursively; the value false means the opposite.|
| success | Function | No| Callback invoked when the API call is successful.|
| fail | Function | No| Callback invoked when the API call fails.|
| complete | Function | No| Callback invoked when the API call is complete.|

**Error codes**

| Error Code| Description|
| -------- | -------- |
| 202 | Incorrect parameters are detected.|
| 300 | An I/O error occurs.|

**ArkTS Example:**

```ts
import file from '@system.file';

export default {    
  mkdir() {        
    file.mkdir({            
      uri: 'internal://app/test_directory',            
      success: function() {                
        console.info('call mkdir success.');            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },
    });    
  }
}
```

**JS Example:**

```xml
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="mkdir" class="button" onclick="mkdir"></input>
</div>
```

```css
/* xxx.css */
.container {
  display: flex;
  justify-content: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}

.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}

.button {
  font-size: 30px;
  text-align: center;
  width: 250px;
  height: 60px;
  background-color: #0078D7;
  color: white;
  border-radius: 5px;
}
```

```js
// xxx.js
import file from '@system.file';

export default {    
  mkdir() {        
    file.mkdir({            
      uri: 'internal://app/test_directory',            
      success: function() {                
        console.info('call mkdir success.');            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },
    });    
  }
}
```


## file.rmdir

rmdir(Object): void

Deletes a directory.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.rmdir](js-apis-file-fs.md#fileiormdir) instead.

**System Capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| uri | string | Yes| URI of the directory to delete.|
| recursive | boolean | No| Whether to recursively delete files and subdirectories of the specified directory. The default value is **false**. The value **true** means to recursively delete files and subdirectories of the specified directory; the value **false** means the opposite.|
| success | Function | No| Callback invoked when the API call is successful.|
| fail | Function | No| Callback invoked when the API call fails.|
| complete | Function | No| Callback invoked when the API call is complete.|

**Error codes**

| Error Code| Description|
| -------- | -------- |
| 202 | Incorrect parameters are detected.|
| 300 | An I/O error occurs.|
| 301 | The file or directory does not exist.|

**ArkTS Example:**

```ts
import file from '@system.file';

export default {    
  rmdir() {        
    file.rmdir({            
      uri: 'internal://app/test_directory',            
      success: function() {                
        console.info('call rmdir success.');            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },
    });    
  }
}
```

**JS Example:**

```xml
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="rmdir" class="button" onclick="rmdir"></input>
</div>
```

```css
/* xxx.css */
.container {
  display: flex;
  justify-content: column;
  align-items: center;
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}

.title {
  font-size: 100px;
  text-align: center;
  width: 200px;
  height: 100px;
}

.button {
  font-size: 30px;
  text-align: center;
  width: 250px;
  height: 60px;
  background-color: #0078D7;
  color: white;
  border-radius: 5px;
}
```

```js
// xxx.js
import file from '@system.file';

export default {    
  rmdir() {        
    file.rmdir({            
      uri: 'internal://app/test_directory',            
      success: function() {                
        console.info('call rmdir success.');            
      },            
      fail: function(data, code) {                
        console.error('call fail callback fail, code: ' + code + ', data: ' + data);            
      },
    });    
  }
}
```