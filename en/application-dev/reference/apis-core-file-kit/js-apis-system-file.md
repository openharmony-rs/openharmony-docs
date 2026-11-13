# @system.file (File Storage)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @bao-yangyang; @maokelong95-->
<!--Designer: @Hun_Dun-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=25d29e3212d7772c81a1c241ce23ffa36f144075 translatedAt=2026-11-03T05:02:21.131Z pushedAt=2026-11-04T03:11:33.556Z nl=1 -->

> **NOTE**
>
> - Module maintenance policy:
>   - For lite wearables, this module is constantly maintained and available.
>   - For other device types, this module is no longer maintained since API version 10, and you are advised to use [@ohos.file.fs](js-apis-file-fs.md) instead.
> - The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.

The following describes the URIs in the ArkTS examples:
  1. The URI must be in the `internal://app/xxx` format.
  2. `internal://app/` is a fixed prefix that indicates the application root directory, and `xxx` is the directory or file name created by the developer.

## Modules to Import

```ts
import file from '@system.file';
```

## File

### move

static move(options: FileMoveOption): void

Moves a specified file to a given location.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.moveFile](js-apis-file-fs.md#fileiomovefile) instead.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| options | [FileMoveOption](#filemoveoption) | Yes | File move option. |

**Example**

ArkTS example:

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

JS example:

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
### copy

static copy(options: FileCopyOption): void

Copies a file to the given URI.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.copyFile](js-apis-file-fs.md#fileiocopyfile) instead.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| options | [FileCopyOption](#filecopyoption) | Yes | File copy option. |

**Example**

ArkTS example:

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

JS example:

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

### list

static list(options: FileListOption): void

Obtains all files in the specified directory.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.listFile](js-apis-file-fs.md#fileiolistfile) instead.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| options | [FileListOption](#filelistoption) | Yes | Option for obtaining all files in the specified directory. |

**Example**

ArkTS example:

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

JS example:

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

### get

static get(options: FileGetOption): void

Obtains information about a local file.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.stat](js-apis-file-fs.md#fileiostat) instead.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| options | [FileGetOption](#filegetoption) | Yes | Option for obtaining information about a specified local file. |

**Example**

ArkTS example:

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

JS example:

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
### delete

static delete(options: FileDeleteOption): void

Deletes a local file.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.unlink](js-apis-file-fs.md#fileiounlink) instead.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| options | [FileDeleteOption](#filedeleteoption) | Yes | Option for deleting a local file. |

**Example**

ArkTS example:

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

JS example:

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


### writeText

static writeText(options: FileWriteTextOption): void

Writes text into a file. Only text files can be read and written.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.write](js-apis-file-fs.md#fileiowrite) instead.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| options | [FileWriteTextOption](#filewritetextoption) | Yes | Option for writing text content to the specified file. |

**Example**

ArkTS example:

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

JS example:

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

### writeArrayBuffer

static writeArrayBuffer(options: FileWriteArrayBufferOption): void

Writes buffer data into a file. Only text files can be read and written.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.write](js-apis-file-fs.md#fileiowrite) instead.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| options | [FileWriteArrayBufferOption](#filewritearraybufferoption) | Yes | Option for writing buffer content to the specified file. |

**Example**

ArkTS example:

```ts
import file from '@system.file';

export default {    
  writeArrayBuffer() {       
    file.writeArrayBuffer({           
      uri: 'internal://app/test',           
      buffer: new Uint8Array(8),// buffer is of the Uint8Array type
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

JS example:

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
      buffer: new Uint8Array(8),// buffer is of the Uint8Array type
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


### readText

static readText(options: FileReadTextOption): void

Reads text from a file. Only text files can be read and written.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.readText](js-apis-file-fs.md#fileioreadtext) instead.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| options | [FileReadTextOption](#filereadtextoption) | Yes | Option for reading text content from the specified file. |

**Example**

ArkTS example:

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

JS example:

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


### readArrayBuffer

static readArrayBuffer(options: FileReadArrayBufferOption): void

Reads buffer data from a file. Only text files can be read and written.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.read](js-apis-file-fs.md#fileioread) instead.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| options | [FileReadArrayBufferOption](#filereadarraybufferoption) | Yes | Option for reading buffer content from the specified file. |

**Example**

ArkTS example:

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

JS example:

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


### access

static access(options: FileAccessOption): void

Checks whether a file or directory exists.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.access](js-apis-file-fs.md#fileioaccess) instead.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| options | [FileAccessOption](#fileaccessoption) | Yes | Option for checking whether a file or directory exists. |

**Example**

ArkTS example:

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

JS example:

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


### mkdir

static mkdir(options: FileMkdirOption): void

Creates a directory.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.mkdir](js-apis-file-fs.md#fileiomkdir) instead.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| options | [FileMkdirOption](#filemkdiroption) | Yes | Option for creating the specified directory. |

**Example**

ArkTS example:

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

JS example:

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

### rmdir

static rmdir(options: FileRmdirOption): void

Deletes a directory.

> **NOTE**
>
> This API is deprecated since API version 10 for all device types except lite wearables. Use [fileIo.rmdir](js-apis-file-fs.md#fileiormdir) instead.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| options | [FileRmdirOption](#filermdiroption) | Yes | Option for deleting the specified directory. |

**Example**

ArkTS example:

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

JS example:

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

## FileResponse

File response. Contains file information.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

| Name | Type | Read-Only | Optional | Description |
| ------ | ------ | ---- | ---- | ----- |
| uri | string | No | No | URI of the file. |
| length | number | No | No | File length, in bytes. |
| lastModifiedTime | number | No | No | Timestamp when the file is saved, which is the number of milliseconds from 1970/01/01&nbsp;00:00:00 to the current time. |
| type | 'dir' \| 'file' | No | No | File type. The options are as follows:<br/> -dir: directory;<br/> -file: file. |
| subFiles | Array&lt;[FileResponse](#fileresponse)&gt; | No | Yes | File list. |

## FileListResponse

File list response, which contains the file list information.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

| Name | Type | Read-Only | Optional | Description |
| ------ | ------ | ---- | ---- | ----- |
| fileList | Array&lt;[FileResponse](#fileresponse)&gt; | No | No | File list obtained. The format of each file is as follows:<br/>{<br/>uri:'file1',<br/>lastModifiedTime:1589965924479,<br/>length:10240,<br/>type:&nbsp;'file'<br/>} |

## FileReadTextResponse

Text read response, containing the text content read.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

| Name | Type | Read-Only | Optional | Description |
| ------ | ------ | ---- | ---- | ----- |
| text | string | No | No | Text content read. |

## FileReadArrayBufferResponse

File read response, containing the read file content.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

| Name | Type | Read-Only | Optional | Description |
| ------ | ------ | ---- | ---- | ----- |
| buffer | Uint8Array | No | No | Read file content. |

## FileMoveOption

Optional type that supports the move interface usage.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

| Name | Type | Read-Only | Optional | Description |
| ------ | ------ | ---- | ---- | ----- |
| srcUri | string | No | No | URI of the file to move. Due to the restrictions of the underlying file system of lightweight wearable devices, the value must satisfy the following requirements:<br/>1. The URI must not contain the following special characters: \\"*+,:;<=>?[]\\|\x7F, etc.<br/>2. The maximum allowed character length is 128 characters. |
| dstUri | string | No | No | URI of the position to which the file is moved. Due to the restrictions of the underlying file system of lightweight wearable devices, the value must satisfy the following requirements:<br/>1. The URI must not contain the following special characters: \\"*+,:;<=>?[]\\|\x7F, etc.<br/>2. The maximum allowed character length is 128 characters. |
| success | (uri: string) => void | No | Yes | Success callback of the interface call. uri is the URI of the position to which the file is moved. |
| fail | (data: string, code: number) => void | No | Yes | Failure callback of the interface call.<br/>data is the error information.<br/>code is the possible returned error codes:<br/>202: parameter error.<br/>300: I/O error.<br/>301: file or directory does not exist. |
| complete | () => void | No | Yes | Called when the execution is complete. |

## FileCopyOption

Optional type that supports the copy interface.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

| Name | Type | Read-Only | Optional | Description |
| ------ | ------ | ---- | ---- | ----- |
| srcUri | string | No | No | URI of the file to copy. Due to the restrictions of the underlying file system of lightweight wearable devices, the value must satisfy the following requirements:<br/>1. The URI must not contain the following special characters: \\"*+,:;<=>?[]\\|\x7F, etc.<br/>2. The maximum allowed character length is 128 characters. |
| dstUri | string | No | No | URI of the location to which the file is copied.<br/>Application resource paths or tmp-type URIs are not supported. Due to the restrictions of the underlying file system of lightweight wearable devices, the value must satisfy the following requirements:<br/>1. The URI must not contain the following special characters: \\"*+,:;<=>?[]\\|\x7F, etc.<br/>2. The maximum allowed character length is 128 characters. |
| success | (uri: string) => void | No | Yes | Callback function for a successful interface call. uri is the URI of the location to which the file is copied. |
| fail | (data: string, code: number) => void | No | Yes | Callback function for a failed interface call.<br/>data is the error information.<br/>code is the possible returned error code:<br/>202: parameter error.<br/>300: I/O error.<br/>301: file or directory does not exist. |
| complete | () => void | No | Yes | Called when the execution is complete. |

## FileListOption

Defines the options used in **list()**.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

| Name | Type | Read-Only | Optional | Description |
| ------ | ------ | ---- | ---- | ----- |
| uri | string | No | No | URI of the directory. Due to the underlying file system restrictions of lightweight wearable devices, the value must satisfy the following requirements:<br/>1. The URI must not contain the following special characters: \\"*+,:;<=>?[]\\|\x7F, etc.<br/>2. The maximum allowed character length is 128 characters. |
| success | (data: FileListResponse) => void | No | Yes | Success callback of the interface call. data is [FileListResponse](#filelistresponse). |
| fail | (data: string, code: number) => void | No | Yes | Failure callback of the interface call.<br/>data is the error information.<br/>code is the possible return error codes:<br/>202: parameter error.<br/>300: I/O error.<br/>301: file or directory does not exist. |
| complete | () => void | No | Yes | Called when the execution is complete. |

## FileGetOption

Defines the options used in **get()**.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

| Name | Type | Read-Only | Optional | Description |
| ------ | ------ | ---- | ---- | ----- |
| uri | string | No | No | URI of the file. Due to the restriction of the underlying file system of lightweight wearable devices, the value must satisfy the following requirements:<br/>1. The URI must not contain the following special characters: \\"*+,:;<=>?[]\\|\x7F, etc.<br/>2. The maximum allowed character length is 128 characters. |
| recursive | boolean | No | Yes | Whether to recursively obtain the list of files in subdirectories. The value **true** indicates recursive operation, and **false** indicates non-recursive operation. When this parameter is omitted, the default is **false**. |
| success | (file: FileResponse) => void | No | Yes | Callback for a successful interface call. **file** is [FileResponse](#fileresponse). |
| fail | (data: string, code: number) => void | No | Yes | Callback for a failed interface call.<br/>**data** is the error information.<br/>**code** is the possible returned error code:<br/>202: parameter error.<br/>300: I/O error.<br/>301: the file or directory does not exist. |
| complete | () => void | No | Yes | Called when the execution is complete. |

## FileDeleteOption

Optional type that supports the delete interface.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

| Name | Type | Read-Only | Optional | Description |
| ------ | ------ | ---- | ---- | ----- |
| uri | string | No | No | URI of the file to delete. It cannot be an application resource path. Due to the restriction of the underlying file system of the lightweight wearable device, the value must satisfy the following requirements:<br/>1. The URI must not contain the following special characters: \\"*+,:;<=>?[]\\|\x7F, etc.<br/>2. The maximum allowed character length is 128 characters. |
| success | () => void | No | Yes | Called when the operation is successful. |
| fail | (data: string, code: number) => void | No | Yes | Failure callback of the interface call.<br/>data is the error information.<br/>code is the possible returned error code:<br/>202: parameter error.<br/>300: I/O error.<br/>301: file or directory does not exist. |
| complete | () => void | No | Yes | Called when the execution is complete. |

## FileWriteTextOption

Optional type that supports the writeText interface usage.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

| Name | Type | Read-Only | Optional | Description |
| ------ | ------ | ---- | ---- | ----- |
| uri | string | No | No | URI of the local file. If the file does not exist, a file is created. Due to the restriction of the underlying file system of the lightweight wearable device, the value must satisfy the following requirements:<br/>1. The URI must not contain the following special characters: \\"*+,:;<=>?[]\\|\x7F, etc.<br/>2. The maximum allowed character length is 128 characters. |
| text | string | No  | No | String to write. |
| encoding | string | No  | Yes | Encoding format. The default is UTF-8. |
| append | boolean | No  | Yes | Whether to use append mode. The default is false. true means append, and false means no append. |
| success | () => void | No  | Yes | Called when the operation is successful. |
| fail | (data: string, code: number) => void | No  | Yes | Callback invoked when the interface call fails.<br/>data is the error information.<br/>code is the possible returned error code:<br/>202: parameter error.<br/>300: I/O error. |
| complete | () => void | No  | Yes | Called when the execution is complete. |


## FileWriteArrayBufferOption

Optional type that supports the writeArrayBuffer interface usage.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

| Name | Type | Read-Only | Optional | Description |
| ------ | ------ | ---- | ---- | ----- |
| uri | string | No | No | Local file URI. If the file does not exist, it will be created. Due to the underlying file system restrictions of lightweight wearable devices, the value must satisfy the following requirements:<br/>1. The URI must not contain the following special characters: \\"*+,:;<=>?[]\\|\x7F etc.<br/>2. The maximum allowed character length is 128 characters. |
| buffer | Uint8Array | No | No | Buffer to write. |
| position | number | No | Yes | Starting offset position for file writing. The unit is Byte, and the default is 0. |
| append | boolean | No | Yes | Whether to use append mode. The default is false. When set to true, the position parameter is invalid. true means append, and false means no append. |
| success | () => void | No | Yes | Called when the operation is successful. |
| fail | (data: string, code: number) => void | No | Yes | Failure callback of the interface call.<br/>data is the error information.<br/>code is the possible returned error codes:<br/>202: parameter error.<br/>300: I/O error. |
| complete | () => void | No | Yes | Called when the execution is complete. |

## FileReadTextOption

Defines the options used in **readText()**.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

| Name | Type | Read-Only | Optional | Description |
| ------ | ------ | ---- | ---- | ----- |
| uri | string | No | No | URI of the local file. Due to the restrictions of the underlying file system of lightweight wearable devices, the value must satisfy the following requirements:<br/>1. The URI must not contain the following special characters: \\"*+,:;<=>?[]\\|\x7F, etc.<br/>2. The maximum allowed character length is 128 characters. |
| encoding | string | No | Yes | Encoding format, which defaults to UTF-8. |
| position | number | No | Yes | Start position for reading, in bytes. The default is the start position of the file. |
| length | number | No | Yes | Length to read, in bytes. The value range is [1, 4096]. When this parameter is empty, the default value is 4096. |
| success | (data: FileReadTextResponse) => void | No | Yes | Success callback of the interface call. **data** is [FileReadTextResponse](#filereadtextresponse). |
| fail | (data: string, code: number) => void | No | Yes | Failure callback of the interface call.<br/>**data** is the error information.<br/>**code** is the possible returned error codes:<br/>202: parameter error.<br/>300: I/O error.<br/>301: the file or directory does not exist.<br/>302: the file content to read exceeds 4KB. |
| complete | () => void | No | Yes | Called when the execution is complete. |

## FileReadArrayBufferOption

Optional type, which supports the readArrayBuffer interface usage.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

| Name | Type | Read-Only | Optional | Description |
| ------ | ------ | ---- | ---- | ----- |
| uri | string | No | No | Local file URI. Due to the underlying file system restrictions of lightweight wearable devices, the value must satisfy the following requirements:<br/>1. The URI must not contain the following special characters: \\"*+,:;<=>?[]\\|\x7F, etc.<br/>2. The maximum allowed character length is 128 characters. |
| position | number | No | Yes | Start position to read from, in bytes. It defaults to the start position of the file. |
| length | number | No | Yes | Length to read, in bytes. By default, it reads to the end of the file. |
| success | (data: FileReadArrayBufferResponse) => void | No | Yes | Success callback of the interface call. data is [FileReadArrayBufferResponse](#filereadarraybufferresponse). |
| fail | (data: string, code: number) => void | No | Yes | Failure callback of the interface call.<br/>data is the error information.<br/>code is the possible returned error code:<br/>202: parameter error.<br/>300: I/O error.<br/>301: file or directory does not exist. |
| complete | () => void | No | Yes | Called when the execution is complete. |

## FileAccessOption

Optional type, supports access interface usage.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

| Name | Type | Read-Only | Optional | Description |
| ------ | ------ | ---- | ---- | ----- |
| uri | string | No | No | Directory or file URI. Due to the restrictions of the underlying file system of lightweight wearable devices, the value must satisfy the following requirements:<br/>1. The URI must not contain the following special characters: \\"*+,:;<=>?[]\\|\x7F etc.<br/>2. The maximum allowed character length is 128 characters. |
| success | () => void | No | Yes | Called when the operation is successful. |
| fail | (data: string, code: number) => void | No | Yes | Failure callback of the interface call.<br/>data is the error information.<br/>code is the possible returned error codes:<br/>202: parameter error.<br/>300: I/O error.<br/>301: file or directory does not exist. |
| complete | () => void | No | Yes | Called when the execution is complete. |


## FileMkdirOption

Optional type that supports mkdir interface usage.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

| Name | Type | Read-Only | Optional | Description |
| ------ | ------ | ---- | ---- | ----- |
| uri | string | No | No | Directory URI. Due to the restriction of the underlying file system of the lightweight wearable device, the value must satisfy the following requirements:<br/>1. The URI must not contain the following special characters: \\"*+,:;<=>?[]\\|\x7F, etc.<br/>2. The maximum allowed character length is 128 characters. |
| recursive | boolean | No | Yes | Whether to recursively create the parent directory of this directory. The default is false. true means recursive creation, and false means non-recursive creation. |
| success | () => void | No | Yes | Called when the operation is successful. |
| fail | (data: string, code: number) => void | No | Yes | Callback function for a failed interface call.<br/>data is the error information.<br/>code is the possible returned error code:<br/>202: parameter error.<br/>300: I/O error. |
| complete | () => void | No | Yes | Called when the execution is complete. |


## FileRmdirOption

Optional type, supports rmdir interface usage.

**System capability**: SystemCapability.FileManagement.File.FileIO.Lite

| Name | Type | Read-Only | Optional | Description |
| ------ | ------ | ---- | ---- | ----- |
| uri | string | No | No | Directory URI. Due to the underlying file system restrictions of lightweight wearable devices, the value must satisfy the following requirements:<br/>1. The URI must not contain the following special characters: \\"*+,:;<=>?[]\\|\x7F, etc.<br/>2. The maximum allowed character length is 128 characters. |
| recursive | boolean | No | Yes | Whether to recursively delete subfiles and subdirectories. Defaults to false. true means recursive deletion, and false means non-recursive deletion. |
| success | () => void | No | Yes | Called when the operation is successful. |
| fail | (data: string, code: number) => void | No | Yes | Failure callback of the interface call.<br/>data is the error information.<br/>code is the possible return error codes:<br/>202: parameter error.<br/>300: I/O error.<br/>301: file or directory does not exist. |
| complete | () => void | No | Yes | Called when the execution is complete. |