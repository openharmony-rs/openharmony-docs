# setxattrSync

## 导入模块

```TypeScript
```

## setxattrSync

```TypeScript
function setxattrSync(path: string, key: string, value: string): void
```

设置文件或目录的扩展属性。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function setxattrSync(path: string, key: string, value: string): void--><!--Device-fileIo-function setxattrSync(path: string, key: string, value: string): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录的应用沙箱路径。 |
| key | string | 是 | 扩展属性的key。仅支持前缀为“user.”的字符串，且长度需小于256字节。 |
| value | string | 是 | 扩展属性的value。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameter types. |
| 13900038 | Value too large for defined data type |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900031 | Function not implemented |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 13900011 | Out of memory |

