# File

文件类。

**起始版本：** 3

**废弃版本：** 10

<!--Device-unnamed-export default class File--><!--Device-unnamed-export default class File-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

## access

```TypeScript
static access(options: FileAccessOption): void
```

判断指定文件或目录是否存在。

**起始版本：** 3

**废弃版本：** 10

**替代接口：** [fs:access](arkts-corefile-file-fs-access-f.md#access-1)

<!--Device-File-static access(options: FileAccessOption): void--><!--Device-File-static access(options: FileAccessOption): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FileAccessOption](arkts-corefile-file-fileaccessoption-depr-i.md) | 是 | 接口选项。 |

**示例：**

ArkTS示例：

```TypeScript
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

JS示例：

```TypeScript
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="access" class="button" onclick="access"></input>
</div>

```

```TypeScript
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

```TypeScript
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

## copy

```TypeScript
static copy(options: FileCopyOption): void
```

将指定文件拷贝并存储到指定位置。

**起始版本：** 3

**废弃版本：** 10

**替代接口：** [fs:copyFile](arkts-corefile-file-fs-copyfile-f.md#copyfile-1)

<!--Device-File-static copy(options: FileCopyOption): void--><!--Device-File-static copy(options: FileCopyOption): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FileCopyOption](arkts-corefile-file-filecopyoption-depr-i.md) | 是 | 接口选项。 |

**示例：**

ArkTS示例：

```TypeScript
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

JS示例：

```TypeScript
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="copy" class="button" onclick="copy"></input>
</div>

```

```TypeScript
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

```TypeScript
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

## delete

```TypeScript
static delete(options: FileDeleteOption): void
```

删除本地文件。

**起始版本：** 3

**废弃版本：** 10

**替代接口：** [fs:unlink](arkts-corefile-file-fs-unlink-f.md#unlink-1)

<!--Device-File-static delete(options: FileDeleteOption): void--><!--Device-File-static delete(options: FileDeleteOption): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FileDeleteOption](arkts-corefile-file-filedeleteoption-depr-i.md) | 是 | 接口选项。 |

**示例：**

ArkTS示例：

```TypeScript
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

JS示例：

```TypeScript
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="delete" class="button" onclick="delete"></input>
</div>

```

```TypeScript
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

```TypeScript
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

## get

```TypeScript
static get(options: FileGetOption): void
```

获取指定本地文件的信息。

**起始版本：** 3

**废弃版本：** 10

**替代接口：** [fs:stat](arkts-corefile-file-fs-stat-f.md#stat-1)

<!--Device-File-static get(options: FileGetOption): void--><!--Device-File-static get(options: FileGetOption): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FileGetOption](arkts-corefile-file-filegetoption-depr-i.md) | 是 | 接口选项。 |

**示例：**

ArkTS示例：

```TypeScript
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

JS示例：

```TypeScript
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="get" class="button" onclick="get"></input>
</div>

```

```TypeScript
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

```TypeScript
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

## list

```TypeScript
static list(options: FileListOption): void
```

获取指定路径下全部文件的列表。

**起始版本：** 3

**废弃版本：** 10

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-File-static list(options: FileListOption): void--><!--Device-File-static list(options: FileListOption): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FileListOption](arkts-corefile-file-filelistoption-depr-i.md) | 是 | 接口选项。 |

**示例：**

ArkTS示例：

```TypeScript
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

JS示例：

```TypeScript
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="list" class="button" onclick="list"></input>
</div>

```

```TypeScript
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

```TypeScript
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

## mkdir

```TypeScript
static mkdir(options: FileMkdirOption): void
```

创建指定目录。

**起始版本：** 3

**废弃版本：** 10

**替代接口：** [fs:mkdir](arkts-corefile-file-fs-mkdir-f.md#mkdir-1)

<!--Device-File-static mkdir(options: FileMkdirOption): void--><!--Device-File-static mkdir(options: FileMkdirOption): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FileMkdirOption](arkts-corefile-file-filemkdiroption-depr-i.md) | 是 | 接口选项。 |

**示例：**

ArkTS示例：

```TypeScript
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

JS示例：

```TypeScript
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="mkdir" class="button" onclick="mkdir"></input>
</div>

```

```TypeScript
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

```TypeScript
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

## move

```TypeScript
static move(options: FileMoveOption): void
```

将指定文件移动到其他指定位置。

**起始版本：** 3

**废弃版本：** 10

**替代接口：** [fs:moveFile](arkts-corefile-file-fs-movefile-f.md#movefile-1)

<!--Device-File-static move(options: FileMoveOption): void--><!--Device-File-static move(options: FileMoveOption): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FileMoveOption](arkts-corefile-file-filemoveoption-depr-i.md) | 是 | 文件过滤选项。默认不进行过滤。 |

**示例：**

ArkTS示例：

```TypeScript
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

JS示例：

```TypeScript
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="move" class="button" onclick="move"></input>
</div>

```

```TypeScript
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

```TypeScript
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

## readArrayBuffer

```TypeScript
static readArrayBuffer(options: FileReadArrayBufferOption): void
```

从指定文件中读取Buffer内容。仅支持文本文档读写。

**起始版本：** 3

**废弃版本：** 10

**替代接口：** [fs:read](arkts-corefile-file-fs-read-f.md#read-1)

<!--Device-File-static readArrayBuffer(options: FileReadArrayBufferOption): void--><!--Device-File-static readArrayBuffer(options: FileReadArrayBufferOption): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FileReadArrayBufferOption](arkts-corefile-file-filereadarraybufferoption-depr-i.md) | 是 | 接口选项。 |

**示例：**

ArkTS示例：

```TypeScript
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

JS示例：

```TypeScript
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="readArrayBuffer" class="button" onclick="readArrayBuffer"></input>
</div>

```

```TypeScript
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

```TypeScript
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

## readText

```TypeScript
static readText(options: FileReadTextOption): void
```

从指定文件中读取文本内容。仅支持文本文档读写。

**起始版本：** 3

**废弃版本：** 10

**替代接口：** [fs:readText](arkts-corefile-file-fs-readtext-f.md#readtext-1)

<!--Device-File-static readText(options: FileReadTextOption): void--><!--Device-File-static readText(options: FileReadTextOption): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FileReadTextOption](arkts-corefile-file-filereadtextoption-depr-i.md) | 是 | 接口选项。 |

**示例：**

ArkTS示例：

```TypeScript
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

JS示例：

```TypeScript
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="readText" class="button" onclick="readText"></input>
</div>

```

```TypeScript
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

```TypeScript
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

## rmdir

```TypeScript
static rmdir(options: FileRmdirOption): void
```

删除指定目录。

**起始版本：** 3

**废弃版本：** 10

**替代接口：** [fs:rmdir](arkts-corefile-file-fs-rmdir-f.md#rmdir-1)

<!--Device-File-static rmdir(options: FileRmdirOption): void--><!--Device-File-static rmdir(options: FileRmdirOption): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FileRmdirOption](arkts-corefile-file-filermdiroption-depr-i.md) | 是 | 接口选项。 |

**示例：**

ArkTS示例：

```TypeScript
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

JS示例：

```TypeScript
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="rmdir" class="button" onclick="rmdir"></input>
</div>

```

```TypeScript
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

```TypeScript
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

## writeArrayBuffer

```TypeScript
static writeArrayBuffer(options: FileWriteArrayBufferOption): void
```

写Buffer内容到指定文件。仅支持文本文档读写。

**起始版本：** 3

**废弃版本：** 10

**替代接口：** [fs:write](arkts-corefile-file-fs-write-f.md#write-1)

<!--Device-File-static writeArrayBuffer(options: FileWriteArrayBufferOption): void--><!--Device-File-static writeArrayBuffer(options: FileWriteArrayBufferOption): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FileWriteArrayBufferOption](arkts-corefile-file-filewritearraybufferoption-depr-i.md) | 是 | 接口选项。 |

**示例：**

ArkTS示例：

```TypeScript
import file from '@system.file';

export default {    
  writeArrayBuffer() {       
    file.writeArrayBuffer({           
      uri: 'internal://app/test',           
      buffer: new Uint8Array(8),// buffer为Uint8Array类型
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

JS示例：

```TypeScript
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="writeArrayBuffer" class="button" onclick="writeArrayBuffer"></input>
</div>

```

```TypeScript
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

```TypeScript
// xxx.js
import file from '@system.file';

export default {    
  writeArrayBuffer() {       
    file.writeArrayBuffer({           
      uri: 'internal://app/test',           
      buffer: new Uint8Array(8),// buffer为Uint8Array类型
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

## writeText

```TypeScript
static writeText(options: FileWriteTextOption): void
```

写文本内容到指定文件。仅支持文本文档读写。

**起始版本：** 3

**废弃版本：** 10

**替代接口：** [fs:write](arkts-corefile-file-fs-write-f.md#write-1)

<!--Device-File-static writeText(options: FileWriteTextOption): void--><!--Device-File-static writeText(options: FileWriteTextOption): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FileWriteTextOption](arkts-corefile-file-filewritetextoption-depr-i.md) | 是 | 接口选项。 |

**示例：**

ArkTS示例：

```TypeScript
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

JS示例：

```TypeScript
<!-- xxx.hml -->
<div class="container">
  <text class="title" style="font-size: 30px;">test</text>
  <input type="button" value="writeText" class="button" onclick="writeText"></input>
</div>

```

```TypeScript
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

```TypeScript
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

