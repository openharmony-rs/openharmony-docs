# getCfgFilesSync（系统接口）

## 导入模块

```TypeScript
import { configPolicy } from '@kit.BasicServicesKit';
```

## getCfgFilesSync

```TypeScript
function getCfgFilesSync(relPath: string, followMode?: FollowXMode, extra?: string): Array<string>
```

根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。

**起始版本：** 11

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| relPath | string | 是 | 配置文件名。 |
| followMode | [FollowXMode](arkts-basicservices-configpolicy-followxmode-e-sys.md) | 否 | 跟随模式，不设置时，默认使用 [DEFAULT](arkts-basicservices-configpolicy-followxmode-e-sys.md#default)。 |
| extra | string | 否 | 用户自定义跟随规则，仅在followMode为 [USER_DEFINED](arkts-basicservices-configpolicy-followxmode-e-sys.md#user_defined)时有效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;string & gt; | 返回文件列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1.Mandatory parameters are left unspecified;  2.Incorrect parameter types;  3.Parameter verification failed. |

**示例**

```TypeScript
import { configPolicy, BusinessError } from '@kit.BasicServicesKit';

try {
  let relpath: string = 'etc/config.xml';
  let extra: string = 'etc/carrier/${telephony.sim.opkey0}';
  let result: Array<string> = configPolicy.getCfgFilesSync(relpath, configPolicy.FollowXMode.USER_DEFINED, extra);
  console.info('result is ' + result);
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error('error:' + code + ', ' + message);
}
```
