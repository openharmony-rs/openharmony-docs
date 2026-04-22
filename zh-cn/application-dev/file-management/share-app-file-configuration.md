# 应用共享目录配置
<!--Kit: Core File Kit-->
<!--Subsystem: Security-->
<!--Owner: @renzehua-->
<!--Designer: @renzehua; @huangjieliang; @zhanganxiang-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

从API version 23开始，系统新增支持共享目录配置功能。在[应用文件分享](share-app-file.md)场景中，开发者可配置共享目录范围，防止应用敏感数据泄露。  
从API version 26开始，系统新增支持应用分享沙箱目录给系统的能力，在手机和平板上实现捐献路径文管中可见的用户体验。

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
   | sharingOSPath<sup>26+</sup> | 应用分享给操作系统的沙箱目录。 | 字符串 | 否 |
   | sharingOSSubpath<sup>26+</sup> | 应用分享给操作系统的沙箱子目录。 | 字符串 | 否 |
   | sharingOSPermission<sup>26+</sup> | 应用分享给操作系统沙箱目录的路径授权类型。 | 字符串 | 否 |

   **scopes标签说明**

   | 属性名称 | 含义 | 数据类型 | 必填 |
   | -------- | -------- | -------- | -------- |
   | path | 共享路径配置，当前仅支持[el2目录](share-app-file.md#应用可分享目录)，scopes中的path不可重复。支持的取值如下：<br/>- `/base/files`<br/>- `/base/preferences`<br/>- `/base/haps` | string | scopes存在时必填 |
   | permission | 共享路径权限。支持的取值如下：<br/>- `r`：只读。<br/>- `r+w`：读写。 | string | scopes存在时必填 |

   **sharingOSPath等标签说明<sup>26+</sup>**

   | 属性名称 | 含义 | 数据类型 | 必填 |
   | -------- | -------- | -------- | -------- |
   | sharingOSPath | 非必选，不填代表不分享目录给操作系统，这样在系统应用如文管/filePicker中将不可见，填写要求是上面scopes列表中一个对象的path值 | string | 应用捐献沙箱目录时必填 |
   | sharingOSSubpath | 非必选，sharingOSPath有值时必填，长度不超过32，将"sharingOSPath"+"sharingOSSubpath"拼装后的路径，作为分享给操作系统的目录，""空串代表就是scopes中的path，有字符则以/开头，不允许有'.'、'..'、'\0'字符。 | string | sharingOSPath存在时必填 |
   | sharingOSPermission | 非必选，sharingOSPath有值时必填，单选["r"、"r+w"]；要求sharingOSPermission的权限是permission的子集。 | string | sharingOSPath存在时必填 |

> **说明：**
>
> 应用更新时如涉及配置变更，将依据新配置进行管控，已分享文件的临时权限不受影响。

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
