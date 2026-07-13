# @ohos.file.environment

该模块提供环境目录能力，获取内存存储根目录、公共文件根目录的ArkTS接口。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.File.Environment

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getUserDesktopDir](arkts-corefile-getuserdesktopdir-f.md#getuserdesktopdir-1) | 获取当前用户预授权桌面目录的沙箱路径。 |
| [getUserDocumentDir](arkts-corefile-getuserdocumentdir-f.md#getuserdocumentdir-1) | 获取当前用户预授权文档目录的沙箱路径。 |
| [getUserDownloadDir](arkts-corefile-getuserdownloaddir-f.md#getuserdownloaddir-1) | 获取当前用户预授权下载目录的沙箱路径。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getExternalStorageDir](arkts-corefile-getexternalstoragedir-f-sys.md#getexternalstoragedir-1) | 获取外卡根目录的沙箱路径，该接口仅对具有该系统能力的设备开放。 |
| [getStorageDataDir](arkts-corefile-getstoragedatadir-f-sys.md#getstoragedatadir-1) | 异步方法获取内存存储根目录，使用promise异步回调。 |
| [getStorageDataDir](arkts-corefile-getstoragedatadir-f-sys.md#getstoragedatadir-2) | 异步方法获取内存存储根目录，使用callback异步回调。 |
| [getUserDataDir](arkts-corefile-getuserdatadir-f-sys.md#getuserdatadir-1) | 异步方法获取公共文件根目录，使用promise异步回调。 |
| [getUserDataDir](arkts-corefile-getuserdatadir-f-sys.md#getuserdatadir-2) | 异步方法获取公共文件根目录，使用callback异步回调。 |
| [getUserHomeDir](arkts-corefile-getuserhomedir-f-sys.md#getuserhomedir-1) | 获取当前用户下应用沙箱路径的内卡目录，该接口仅对具有该系统能力的设备开放。 |
<!--DelEnd-->

