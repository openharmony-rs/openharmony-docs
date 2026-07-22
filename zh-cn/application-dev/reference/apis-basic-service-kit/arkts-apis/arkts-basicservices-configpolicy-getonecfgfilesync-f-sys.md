# getOneCfgFileSync（系统接口）

## 导入模块

```TypeScript
import { configPolicy } from '@kit.BasicServicesKit';
```

## getOneCfgFileSync

```TypeScript
function getOneCfgFileSync(relPath: string, followMode?: FollowXMode, extra?: string): string
```

根据提供的跟随模式，获取指定文件名优先级最高的配置文件路径。

**起始版本：** 11

<!--Device-configPolicy-function getOneCfgFileSync(relPath: string, followMode?: FollowXMode, extra?: string): string--><!--Device-configPolicy-function getOneCfgFileSync(relPath: string, followMode?: FollowXMode, extra?: string): string-End-->

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| relPath | string | 是 | 配置文件名。 |
| followMode | [FollowXMode](arkts-basicservices-configpolicy-followxmode-e-sys.md) | 否 | 跟随模式，不设置时，默认使用[DEFAULT](arkts-basicservices-configpolicy-followxmode-e-sys.md#default)。 |
| extra | string | 否 | 用户自定义跟随规则，仅在followMode为[USER_DEFINED](arkts-basicservices-configpolicy-followxmode-e-sys.md#user_defined)时有效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回优先级最高的配置文件路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types;<br>3.Parameter verification failed. |

