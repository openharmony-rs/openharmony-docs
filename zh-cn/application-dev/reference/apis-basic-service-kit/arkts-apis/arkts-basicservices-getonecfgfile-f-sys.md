# getOneCfgFile（系统接口）

## getOneCfgFile

```TypeScript
function getOneCfgFile(relPath: string, callback: AsyncCallback<string>): void
```

获取指定文件名优先级最高的配置文件路径。使用callback异步回调。
例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml，
最终返回优先级最高的是：/sys_pod/etc/config.xml。

**起始版本：** 8

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| relPath | string | 是 | 配置文件名。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。当获取配置文件路径成功，err为undefined，data为获取到的优先级最高的配置文件路径；否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |


## getOneCfgFile

```TypeScript
function getOneCfgFile(relPath: string, followMode: FollowXMode, callback: AsyncCallback<string>): void
```

根据提供的跟随模式获取指定文件名优先级最高的配置文件路径。使用callback异步回调。
例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、
/sys_pod/etc/carrier/46060/etc/
config.xml。设备默认卡opkey为46060，设置的followMode为configPolicy.FollowXMode.SIM_DEFAULT。最终返回的是：
/sys_pod/etc/carrier/46060/etc/config.xml。

**起始版本：** 11

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| relPath | string | 是 | 配置文件名。 |
| followMode | FollowXMode | 是 | 跟随模式。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。当获取配置文件路径成功，err为undefined，data为获取到的优先级最高的配置文件路径；否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |


## getOneCfgFile

```TypeScript
function getOneCfgFile(relPath: string, followMode: FollowXMode, extra: string, callback: AsyncCallback<string>): void
```

根据跟随模式获取指定文件优先级最高的配置文件路径。使用callback异步回调。
例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、
/sys_pod/etc/carrier/46060/etc/config.xml。设备卡1的opkey为46060，设置的followMode为
configPolicy.FollowXMode.USER_DEFINED，自定义跟随规则为"etc/carrier/${telephony.sim.opkey0}"。
最终返回的是：/sys_pod/etc/carrier/46060/etc/config.xml。

**起始版本：** 11

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| relPath | string | 是 | 配置文件名。 |
| followMode | FollowXMode | 是 | 跟随模式。 |
| extra | string | 是 | 用户自定义跟随规则，仅在followMode为[USER_DEFINED](arkts-basicservices-followxmode-e-sys.md#user_defined)时有效。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。当获取配置文件路径成功，err为undefined，data为获取到的优先级最高的配置文件路径；否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |


## getOneCfgFile

```TypeScript
function getOneCfgFile(relPath: string): Promise<string>
```

获取指定文件名优先级最高的配置文件路径。使用Promise异步回调。

**起始版本：** 8

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| relPath | string | 是 | 配置文件名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回优先级最高的配置文件路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |


## getOneCfgFile

```TypeScript
function getOneCfgFile(relPath: string, followMode: FollowXMode, extra?: string): Promise<string>
```

根据提供的跟随模式，获取指定文件名优先级最高的配置文件路径。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| relPath | string | 是 | 配置文件名。 |
| followMode | FollowXMode | 是 | 跟随模式。 |
| extra | string | 否 | 用户自定义跟随规则，仅在followMode为[USER_DEFINED](arkts-basicservices-followxmode-e-sys.md#user_defined)时有效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回优先级最高的配置文件路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types;<br>3.Parameter verification failed. |

