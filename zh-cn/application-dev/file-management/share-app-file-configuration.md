# 应用共享目录配置
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @renzehua-->
<!--Designer: @renzehua; @huangjieliang; @zhanganxiang-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

应用文件分享场景下，提供应用共享目录配置的能力，支持开发者按需配置共享目录范围或关闭共享，防止应用敏感数据泄露。

## 开发说明

在模块级配置文件[src/main/module.json5](../quick-start/module-configuration-file.md)的配置文件标签"module"中添加"shareFiles"标签。

``` JSON5
{
  "module": {
    // ...
    "shareFiles": "$profile:share_files", // 资源配置，指向profile下面定义的配置文件share_files.json
    // ...
  }
}
```

在开发视图的resources/base/profile下面定义配置文件share_files.json，其中文件名"share_files"可自定义，需要和标签指定的信息对应。配置文件中包含了共享目录范围以及文件权限。

**表1** shareFiles标签说明

| 属性名称 | 含义 | 数据类型 | 是否可缺省 |
| -------- | -------- | -------- | -------- |
| share_files | 标识当前Module所有共享路径的权限信息。 | 对象 | 该标签不可缺省。 |


**表2** share_files标签说明

| 属性名称 | 含义 | 数据类型 | 是否可缺省 |
| -------- | -------- | -------- | -------- |
| scopes | 允许授权的范围。 | 对象数组 | 该标签可缺省。 |
| path_to_system | 捐献给操作系统的路径，必须是scopes中配置的path值。 | 字符串 | 该标签可缺省。 |
| subpath_to_system | path_to_system与subpath_to_system拼接后的路径作为捐献给操作系统的路径。字符长度不能超过32，可以为空值""，有字符则以/开头，不允许"."、".."、"/0"字符。 | 字符串 | path_to_system有值时该标签不可缺省。 |
| permission_to_system | 捐献给操作系统的路径权限，值需为permission的子集。支持的取值如下：<br/>-&nbsp;r：只读。<br/>-&nbsp;r+w：读写。 | 字符串 | path_to_system有值时该标签不可缺省。 |


**表3** scopes标签说明

| 属性名称 | 含义 | 数据类型 | 是否可缺省 |
| -------- | -------- | -------- | -------- |
| path | 路径配置，scopes中的path不可重复。支持的取值如下：<br/>-&nbsp;/base/temp。<br/>-&nbsp;/base/files。<br/>-&nbsp;/base/preferences。<br/>-&nbsp;/base/haps。 | 字符串 | 该标签不可缺省。 |
| permission | 路径权限。支持的取值如下：<br/>-&nbsp;r：只读。<br/>-&nbsp;r+w：读写。 | 字符串 | 该标签不可缺省。 |


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
    "path_to_system": "/base/files",
    "subpath_to_system": "/subdir",
    "permission_to_system": "r"
  }
}
```
