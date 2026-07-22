# listFile（系统接口）

## 导入模块

```TypeScript
import { trash } from '@kit.CoreFileKit';
```

## listFile

```TypeScript
function listFile(): Array<FileInfo>
```

Lists the files and directories in the **Recently deleted** list.

**起始版本：** 10

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-trash-function listFile(): Array<FileInfo>--><!--Device-trash-function listFile(): Array<FileInfo>-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;FileInfo&gt; | Returns the next level FileInfo Object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900020 | Invalid argument |
| 13900042 | Unknown error |

**示例：**

```TypeScript
let fileinfos = trash.listFile();
for(let i = 0; i < fileinfos.length; i++){
  console.info('uri: ' + fileinfos[i].uri);
  console.info('srcPath: ' + fileinfos[i].srcPath);
  console.info('fileName: ' + fileinfos[i].fileName);
  console.info('mode: ' + fileinfos[i].mode);
  console.info('size: ' + fileinfos[i].size);
  console.info('mtime: ' + fileinfos[i].mtime);
  console.info('ctime: ' + fileinfos[i].ctime);
}

```

