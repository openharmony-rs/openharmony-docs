# getCfgFilesSync (System API)

## Modules to Import

```TypeScript
import { configPolicy } from '@kit.BasicServicesKit';
```

## getCfgFilesSync

```TypeScript
function getCfgFilesSync(relPath: string, followMode?: FollowXMode, extra?: string): Array<string>
```

Obtains a list of all files of a specified file name based on the provided follow mode, in ascending order of priority.

**Since:** 11

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| relPath | string | Yes | Name of the configuration file. |
| followMode | [FollowXMode](arkts-basicservices-configpolicy-followxmode-e-sys.md) | No | Follow mode. The default value is [DEFAULT](arkts-basicservices-configpolicy-followxmode-e-sys.md#default) if this parameter is not set. |
| extra | string | No | Custom follow rule. This parameter is valid only when **followMode** is set to [USER_DEFINED](arkts-basicservices-configpolicy-followxmode-e-sys.md#user_defined). |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of configuration files obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified; <br>2.Incorrect parameter types; <br>3.Parameter verification failed. |
