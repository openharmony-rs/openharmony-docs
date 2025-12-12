# 应用共享目录配置


应用文件分享场景下，提供应用共享目录配置的能力，支持开发者按需配置共享目录范围或关闭共享，防止应用敏感数据泄露。

## 开发说明

在模块级配置文件/src/main/module.json5的配置文件标签"module"中添加"shareFiles"标签。

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
| share_files | 标识当前Module中所有共享路径的权限信息。 | 对象 | 该标签不可缺省。 |


**表2** share_files标签说明

| 属性名称 | 含义 | 数据类型 | 是否可缺省 |
| -------- | -------- | -------- | -------- |
| scopes | 允许授权的范围。 | 对象数组 | 该标签可缺省。 |
| path_to_system | 允许授权范围。 | 字符串 | 该标签可缺省。 |
| subpath_to_system | 字符长度不能超过32，可以为空值""，有字符则以/开头，不允许"."、".."、"/0"字符。 | 字符串 | path_to_system有值时该标签不可缺省。 |
| permission_to_system | 支持的取值如下：<br/>-&nbsp;r：公有类型。<br/>-&nbsp;r+w：私有类型。 | 字符串 | path_to_system有值时该标签不可缺省。 |


**表3** scopes标签说明

| 属性名称 | 含义 | 数据类型 | 是否可缺省 |
| -------- | -------- | -------- | -------- |
| path | 允许授权的范围。支持的取值如下：<br/>-&nbsp;/base/temp：。<br/>-&nbsp;/base/files：。<br/>-&nbsp;/base/preferences：。<br/>-&nbsp;/base/haps：。 | 字符串 | 该标签不可缺省。 |
| permission | 支持的取值如下：<br/>-&nbsp;r：公有类型。<br/>-&nbsp;r+w：私有类型。 | 字符串 | 该标签不可缺省。 |




share_files.json示例：


``` json
{
  "share_files": {
    "scopes": [
      {
        "path": "hnpsample.hnp",
        "permission": "public"
      }
    ],
    "path_to_system": "",
    "subpath_to_system": "",
    "permission_to_system": "r"
  }
}
```
