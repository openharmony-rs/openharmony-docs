# 应用共享目录配置
<!--Kit: Core File Kit-->
<!--Subsystem: Security-->
<!--Owner: @renzehua-->
<!--Designer: @renzehua; @huangjieliang; @zhanganxiang-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

从API版本23开始，系统支持配置共享目录。在[应用文件分享](share-app-file.md)场景中，开发者可配置共享目录范围，以防止应用敏感数据泄露。仅共享目录中的文件可供用户分享给其他应用查阅。

从API版本26.0.0开始，系统支持配置应用捐献沙箱目录。捐献目录为共享目录的子目录。应用配置捐献目录后，系统应用可访问并操作其中的文件数据。仅支持在手机（Phone）、平板（Tablet）上配置捐献目录。

以文件管理器上的交互体验为例，应用配置了捐献目录后，用户在手机、平板设备上可通过文件管理器查阅、修改捐献目录中的文件。

## 开发步骤

1. 开发者可在应用模块级配置文件[src/main/module.json5](../quick-start/module-configuration-file.md)的module标签中添加shareFiles标签，以实现对沙箱共享目录权限的限制。若未配置共享目录，则默认允许应用共享其自身沙箱内的文件。

   **shareFiles标签**

   ``` JSON5
   {
     "module": {
       // ...
       "shareFiles": "$profile:share_files", // 资源配置，指向profile下面定义的配置文件share_files.json
       // ...
     }
   }
   ```

2. 在开发视图的resources/base/profile下面定义配置文件share_files.json，以标识当前模块所有共享路径的权限信息。

   文件名share_files可修改为任意合法文件名，但需要和shareFiles标签配置的文件名一致。

   **share_files标签说明**

   | 属性名称 | 含义 | 数据类型 | 必填 |
   | -------- | -------- | -------- | -------- |
   | scopes | 允许共享的范围，详见scopes标签说明。 | 对象数组 | 否 |
   | sharingOSPath | 应用捐献给操作系统的沙箱目录，取值必须为scopes列表中已配置的path值。未配置该字段则表示不向操作系统捐献目录，系统应用如文件管理器、FilePicker等将无法查看应用捐献的沙箱目录。<br/>**起始版本：** 26.0.0 | 字符串 | 否 |
   | sharingOSSubpath | 应用捐献给操作系统的沙箱目录的子目录。仅当sharingOSPath配置时必填，长度不超过32，将"sharingOSPath"+"sharingOSSubpath"拼接后的路径，作为捐献给操作系统的目录，""空串代表直接捐献sharingOSPath，有字符则以/开头，不允许有'.'、'..'、'\0'字符。<br/>**起始版本：** 26.0.0 | 字符串 | 否 |
   | sharingOSPermission | 应用捐献给操作系统的沙箱目录的访问权限。仅当sharingOSPath配置时必填，权限必须是scopes中对应路径permission的一个子集，不可超出原配置权限。<br/>**起始版本：** 26.0.0 | 字符串 | 否 |

   > **说明：**
   >
   > 应用更新时如涉及配置变更，将依据新配置进行管控，已分享文件的临时权限不受影响。
   > 
   > 应用向操作系统捐献沙箱目录时，sharingOSPath、sharingOSSubpath、sharingOSPermission三项为必填配置。

   **scopes标签说明**

   | 属性名称 | 含义 | 数据类型 | 必填 |
   | -------- | -------- | -------- | -------- |
   | path | 共享路径配置，当前仅支持[el2目录](share-app-file.md#应用可分享目录)，scopes中的path不可重复。支持的取值如下：<br/>- `/base/files`<br/>- `/base/preferences`<br/>- `/base/haps` | string | scopes存在时必填 |
   | permission | 共享路径权限。支持的取值如下：<br/>- `r`：只读。<br/>- `r+w`：读写。 | string | scopes存在时必填 |


   share_files.json示例：

   ``` json
   {
     "share_files": {
       "scopes": [
         {
           "path": "/base/files",
           "permission": "r+w"
         }
       ],
       "sharingOSPath" : "/base/files",
       "sharingOSSubpath" : "/subdir",
       "sharingOSPermission": "r"
     }
   }
   ```
