# @ohos.file.environment

该模块提供环境目录能力，获取内存存储根目录、公共文件根目录的ArkTS接口。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.File.Environment

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[getExternalStorageDir](arkts-corefile-environment-getexternalstoragedir-f-sys.md#getExternalStorageDir-1) | 获取外卡根目录的沙箱路径，该接口仅对具有该系统能力的设备开放。<br/> |
| <!--DelRow-->[getStorageDataDir](arkts-corefile-environment-getstoragedatadir-f-sys.md#getStorageDataDir-1) | 异步方法获取内存存储根目录，使用promise异步回调。<br/> |
| <!--DelRow-->[getStorageDataDir](arkts-corefile-environment-getstoragedatadir-f-sys.md#getStorageDataDir-2) | 异步方法获取内存存储根目录，使用callback异步回调。<br/> |
| <!--DelRow-->[getUserDataDir](arkts-corefile-environment-getuserdatadir-f-sys.md#getUserDataDir-1) | 异步方法获取公共文件根目录，使用promise异步回调。<br/> |
| <!--DelRow-->[getUserDataDir](arkts-corefile-environment-getuserdatadir-f-sys.md#getUserDataDir-2) | 异步方法获取公共文件根目录，使用callback异步回调。<br/> |
| [getUserDesktopDir](arkts-corefile-environment-getuserdesktopdir-f.md#getUserDesktopDir-1) | 获取当前用户预授权桌面目录的沙箱路径。<br/> |
| [getUserDocumentDir](arkts-corefile-environment-getuserdocumentdir-f.md#getUserDocumentDir-1) | 获取当前用户预授权文档目录的沙箱路径。<br/> |
| [getUserDownloadDir](arkts-corefile-environment-getuserdownloaddir-f.md#getUserDownloadDir-1) | 获取当前用户预授权下载目录的沙箱路径。<br/> |
| <!--DelRow-->[getUserHomeDir](arkts-corefile-environment-getuserhomedir-f-sys.md#getUserHomeDir-1) | 获取当前用户下应用沙箱路径的内卡目录，该接口仅对具有该系统能力的设备开放。<br/> |

