# getCfgFiles（系统接口）

## getCfgFiles

```TypeScript
function getCfgFiles(relPath: string, callback: AsyncCallback<Array<string>>): void
```

获取指定文件名的所有文件列表，按优先级从低到高。使用callback异步回调。 例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml。 最终返回的是：/system/etc/config.xml, /sys_pod/etc/config.xml。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-configPolicy-function getCfgFiles(relPath: string, callback: AsyncCallback<Array<string>>): void--><!--Device-configPolicy-function getCfgFiles(relPath: string, callback: AsyncCallback<Array<string>>): void-End-->

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| relPath | string | 是 | 配置文件名。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数。当获取文件列表成功，err为undefined， data为获取到的文件列表；否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt;1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |


## getCfgFiles

```TypeScript
function getCfgFiles(relPath: string, followMode: FollowXMode, callback: AsyncCallback<Array<string>>): void
```

根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。使用callback异步回调。 例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、 /sys_pod/etc/carrier/46060/etc/config.xml。设备默认卡opkey为46060，设置的followMode为 configPolicy.FollowXMode.SIM_DEFAULT。最终返回的是：/system/etc/config.xml, /sys_pod/etc/config.xml, /sys_pod/etc/carrier/46060/etc/config.xml。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-configPolicy-function getCfgFiles(relPath: string, followMode: FollowXMode, callback: AsyncCallback<Array<string>>): void--><!--Device-configPolicy-function getCfgFiles(relPath: string, followMode: FollowXMode, callback: AsyncCallback<Array<string>>): void-End-->

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| relPath | string | 是 | 配置文件名。 |
| followMode | [FollowXMode](arkts-basicservices-configpolicy-followxmode-e-sys.md) | 是 | 跟随模式。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数。当获取文件列表成功，err为undefined， data为获取到的文件列表；否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt;1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |


## getCfgFiles

```TypeScript
function getCfgFiles(relPath: string, followMode: FollowXMode, extra: string, callback: AsyncCallback<Array<string>>): void
```

根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。使用callback异步回调。 例如，config.xml在设备中的路径按优先级升序排列为：/system/etc/config.xml、/sys_pod/etc/config.xml、 /sys_pod/etc/carrier/46060/etc/config.xml。设备卡1的opkey为46060，设置的followMode为 configPolicy.FollowXMode.USER_DEFINED，自定义跟随规则为"etc/carrier/\${telephony.sim.opkey0}"。 最终返回的是：/system/etc/config.xml, /sys_pod/etc/config.xml, /sys_pod/etc/carrier/46060/etc/config.xml。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-configPolicy-function getCfgFiles(relPath: string, followMode: FollowXMode, extra: string, callback: AsyncCallback<Array<string>>): void--><!--Device-configPolicy-function getCfgFiles(relPath: string, followMode: FollowXMode, extra: string, callback: AsyncCallback<Array<string>>): void-End-->

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| relPath | string | 是 | 配置文件名。 |
| followMode | [FollowXMode](arkts-basicservices-configpolicy-followxmode-e-sys.md) | 是 | 跟随模式。 |
| extra | string | 是 | 用户自定义跟随规则，仅在followMode为 [USER_DEFINED](arkts-basicservices-configpolicy-followxmode-e-sys.md#USER_DEFINED)时有效。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数。当获取文件列表成功，err为undefined， data为获取到的文件列表；否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt;1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |


## getCfgFiles

```TypeScript
function getCfgFiles(relPath: string): Promise<Array<string>>
```

获取指定文件名的所有文件列表，按优先级从低到高。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-configPolicy-function getCfgFiles(relPath: string): Promise<Array<string>>--><!--Device-configPolicy-function getCfgFiles(relPath: string): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| relPath | string | 是 | 配置文件名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回文件列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt;1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types. |


## getCfgFiles

```TypeScript
function getCfgFiles(relPath: string, followMode: FollowXMode, extra?: string): Promise<Array<string>>
```

根据提供的跟随模式获取指定文件名所有的文件列表，按优先级从低到高。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-configPolicy-function getCfgFiles(relPath: string, followMode: FollowXMode, extra?: string): Promise<Array<string>>--><!--Device-configPolicy-function getCfgFiles(relPath: string, followMode: FollowXMode, extra?: string): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Customization.ConfigPolicy

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| relPath | string | 是 | 配置文件名。 |
| followMode | [FollowXMode](arkts-basicservices-configpolicy-followxmode-e-sys.md) | 是 | 跟随模式。 |
| extra | string | 否 | 用户自定义跟随规则，仅在followMode为 [USER_DEFINED](arkts-basicservices-configpolicy-followxmode-e-sys.md#USER_DEFINED)时有效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回文件列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt;1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types; &lt;br&gt;3.Parameter verification failed. |

