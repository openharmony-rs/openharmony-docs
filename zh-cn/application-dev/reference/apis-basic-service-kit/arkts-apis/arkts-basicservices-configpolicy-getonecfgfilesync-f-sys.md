# getOneCfgFileSync（系统接口）

## getOneCfgFileSync

```TypeScript
function getOneCfgFileSync(relPath: string, followMode?: FollowXMode, extra?: string): string
```

根据提供的跟随模式，获取指定文件名优先级最高的配置文件路径。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-configPolicy-function getOneCfgFileSync(relPath: string, followMode?: FollowXMode, extra?: string): string--><!--Device-configPolicy-function getOneCfgFileSync(relPath: string, followMode?: FollowXMode, extra?: string): string-End-->

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| relPath | string | 是 | 配置文件名。 |
| followMode | [FollowXMode](arkts-basicservices-configpolicy-followxmode-e-sys.md) | 否 | 跟随模式，不设置时，默认使用 [DEFAULT](arkts-basicservices-configpolicy-followxmode-e-sys.md#DEFAULT)。 |
| extra | string | 否 | 用户自定义跟随规则，仅在followMode为 [USER_DEFINED](arkts-basicservices-configpolicy-followxmode-e-sys.md#USER_DEFINED)时有效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回优先级最高的配置文件路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt;1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types; &lt;br&gt;3.Parameter verification failed. |

