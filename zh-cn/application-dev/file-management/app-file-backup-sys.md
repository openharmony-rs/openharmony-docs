# 应用触发数据备份/恢复（仅对系统应用开放）
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @lvzhenjie-->
<!--Designer: @wang_zhangjun; @chenxi0605-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @foryourself-->

备份恢复框架是为设备上的应用、服务提供自身数据备份和恢复的解决方案。系统应用开发者可以根据需求，按下述指导开发应用，以触发备份/恢复数据。

- [获取能力文件](#获取能力文件)：获取当前系统用户内所有应用与备份恢复相关基础信息的能力文件。能力文件在应用备份/恢复数据时不可缺少。

- [应用备份数据](#应用备份数据)：根据能力文件提供的应用信息，选择需要备份的应用数据并进行备份。

- [应用恢复数据](#应用恢复数据)：根据能力文件提供的应用信息，选择需要恢复的应用数据并进行恢复。

## 开发说明

备份恢复API的使用指导请参见[API参考](../reference/apis-core-file-kit/js-apis-file-backup-sys.md)。

在使用备份恢复接口之前，需要：

1. [申请应用权限](../security/AccessToken/determine-application-mode.md#system_basic等级应用申请权限的方式)：`ohos.permission.BACKUP`

2. 导入依赖模块：`@ohos.file.backup`

   ```js
   import { backup } from '@kit.CoreFileKit';
   ```

## 获取能力文件

获取当前系统用户内所有应用与备份恢复相关基础信息的能力文件。能力文件在应用备份恢复数据时是不可缺少的，开发者可以根据需要获取能力文件。

该文件包含设备类型、设备版本、应用的基础性信息。如应用名称、应用数据大小、应用版本信息、是否支持备份恢复、是否在恢复时安装应用。

调用[backup.getLocalCapabilities()](../reference/apis-core-file-kit/js-apis-file-backup-sys.md#backupgetlocalcapabilities)获取能力文件。

<!-- @[get_local_cap_ability](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/AppFileBackup/entry/src/main/ets/backuprestore/BackupRestore.ets) -->

**返回的能力文件内容示例：**

| 属性名称       | 数据类型 | 必填 | 含义                   |
| -------------- | -------- | ---- | ---------------------- |
| bundleInfos    | 数组     | 是   | 应用信息列表。           |
| allToBackup    | 布尔值   | 是   | 是否允许备份恢复。true表示允许，false表示不允许。       |
| extensionName  | 字符串   | 是   | 应用的扩展名。           |
| name           | 字符串   | 是   | 应用的包名。             |
| spaceOccupied  | 数值     | 是   | 应用数据占用的空间大小（单位为Byte）。 |
| versionCode    | 数值     | 是   | 应用的版本号。           |
| versionName    | 字符串   | 是   | 应用的版本名称。         |
| deviceType     | 字符串   | 是   | 设备类型。               |
| systemFullName | 字符串   | 是   | 设备版本。               |

```json
{
"bundleInfos" :[{
 "allToBackup" : true,
 "extensionName" : "BackupExtensionAbility",
 "name" : "com.example.hiworld",
 "needToInstall" : false,
 "spaceOccupied" : 0,
 "versionCode" : 1000000,
 "versionName" : "1.0.0"
 }],
"deviceType" : "default",
"systemFullName" : "OpenHarmony-4.0.0.0"
}
```

## 应用备份数据

开发者可以根据能力文件提供的应用信息，选择需要备份的应用数据。

备份过程中，备份恢复服务会将应用的数据打包成文件，打包后的文件会以打开的文件句柄形式，通过创建实例时所注册的回调[onFileReady](../reference/apis-core-file-kit/js-apis-file-backup-sys.md#onfileready)接口返回。

开发者可以根据需要将文件内容保存到本地。

**示例**

  <!-- @[session_backup](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/AppFileBackup/entry/src/main/ets/backuprestore/BackupRestore.ets) -->

## 应用恢复数据

开发者可以根据能力文件提供的应用信息，选择需要恢复的应用数据。

恢复过程中，备份恢复服务会根据开发者调用[getFileHandle](../reference/apis-core-file-kit/js-apis-file-backup-sys.md#getfilehandle)的请求内容，将应用待恢复数据的文件句柄，通过创建实例时注册的回调[onFileReady](../reference/apis-core-file-kit/js-apis-file-backup-sys.md#onfileready)接口返回。可以根据返回的[uri](../reference/apis-core-file-kit/js-apis-file-backup-sys.md#filemeta)将应用对应的待恢复数据写入到文件句柄中。写入完成后开发者调用[publishFile](../reference/apis-core-file-kit/js-apis-file-backup-sys.md#publishfile)通知服务写入完成。

待应用所有恢复数据准备就绪后，服务开始恢复应用数据。

**示例**

  <!-- @[session_restore](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/AppFileBackup/entry/src/main/ets/backuprestore/BackupRestore.ets) -->
