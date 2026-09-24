# getOneCfgFile (System API)

## Modules to Import

```TypeScript
import { configPolicy } from '@kit.BasicServicesKit';
```

## getOneCfgFile

```TypeScript
function getOneCfgFile(relPath: string, callback: AsyncCallback<string>): void
```

Obtains the path of the configuration file with the highest priority. This API uses an asynchronous callback to return the result. For example, if the paths of **config.xml** on the device are **\/system/etc/config.xml** and **\/sys_pod/etc/config.xml** in ascending order of priority, **\/sys_pod/etc/config.xml** is returned.

**Since:** 8

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| relPath | string | Yes | Name of the configuration file. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the configuration file path is successfully obtained, **err** is **undefined**, and **data** is the path of the configuration file with the highest priority. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified; <br>2.Incorrect parameter types. |


<a id="getonecfgfile-1"></a>

## getOneCfgFile

```TypeScript
function getOneCfgFile(relPath: string): Promise<string>
```

Obtains the path of the configuration file with the highest priority. This API uses a promise to return the result.

**Since:** 8

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| relPath | string | Yes | Name of the configuration file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the path of the configuration file with the highest priority. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified; <br>2.Incorrect parameter types. |


<a id="getonecfgfile-2"></a>

## getOneCfgFile

```TypeScript
function getOneCfgFile(relPath: string, followMode: FollowXMode, callback: AsyncCallback<string>): void
```

Obtains the path of the configuration file with the highest priority based on the provided follow mode. This API uses an asynchronous callback to return the result. For example, if the paths of **config.xml** on the device are **\/system/etc/config.xml**, **\/sys_pod/etc/config.xml**, and **\/sys_pod/etc/carrier/46060/etc/config.xml** in ascending order of priority, the default opkey of the device is **46060**, and **followMode** is set to **configPolicy.FollowXMode.SIM_DEFAULT**, the final return value is **\/sys_pod/etc/carrier/46060/etc/config.xml**.

**Since:** 11

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| relPath | string | Yes | Name of the configuration file. |
| followMode | [FollowXMode](arkts-basicservices-configpolicy-followxmode-e-sys.md) | Yes | Follow mode. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the configuration file path is successfully obtained, **err** is **undefined**, and **data** is the path of the configuration file with the highest priority. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified; <br>2.Incorrect parameter types. |


<a id="getonecfgfile-3"></a>

## getOneCfgFile

```TypeScript
function getOneCfgFile(relPath: string, followMode: FollowXMode, extra: string, callback: AsyncCallback<string>): void
```

Obtains the path of the configuration file with the highest priority based on the provided follow mode. This API uses an asynchronous callback to return the result. For example, if the paths of **config.xml** on the device are **\/system/etc/config.xml**, **\/sys_pod/etc/config.xml**, and **\/sys_pod/etc/carrier/46060/etc/config.xml** in ascending order of priority, the opkey of the device card 1 is **46060**, **followMode** is set to **configPolicy.FollowXMode.USER_DEFINED**, and the custom follow rule is **"etc/carrier/${telephony.sim.opkey0}"**, the final return value is **\/sys_pod/etc/carrier/46060/etc/config.xml**.

**Since:** 11

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| relPath | string | Yes | Name of the configuration file. |
| followMode | [FollowXMode](arkts-basicservices-configpolicy-followxmode-e-sys.md) | Yes | Follow mode. |
| extra | string | Yes | Custom follow rule. This parameter is valid only when **followMode** is set to [USER_DEFINED](arkts-basicservices-configpolicy-followxmode-e-sys.md#user_defined). |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the configuration file path is successfully obtained, **err** is **undefined**, and **data** is the path of the configuration file with the highest priority. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified; <br>2.Incorrect parameter types. |


<a id="getonecfgfile-4"></a>

## getOneCfgFile

```TypeScript
function getOneCfgFile(relPath: string, followMode: FollowXMode, extra?: string): Promise<string>
```

Obtains the path of the configuration file with the highest priority based on the provided follow mode. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| relPath | string | Yes | Name of the configuration file. |
| followMode | [FollowXMode](arkts-basicservices-configpolicy-followxmode-e-sys.md) | Yes | Follow mode. |
| extra | string | No | Custom follow rule. This parameter is valid only when **followMode** is set to [USER_DEFINED](arkts-basicservices-configpolicy-followxmode-e-sys.md#user_defined). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the path of the configuration file with the highest priority. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified; <br>2.Incorrect parameter types; <br>3.Parameter verification failed. |
