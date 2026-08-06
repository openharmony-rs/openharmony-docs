# FileUri

文件地址类型数据，用于描述文件的URI地址信息。创建FileUri对象后，可用于文件拖拽、文件共享等场景，支持通过uriAuthorizationPolicies控制文件访问权限，实现跨应用的文件数据传递和权限管理。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-uniformDataStruct-interface FileUri--><!--Device-uniformDataStruct-interface FileUri-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## details

```TypeScript
details?: Record<string, int | long | double | string | Uint8Array>
```

字典类型对象，key为string类型，value可包含number（数值类型）、string（字符串类型）或Uint8Array（二进制字节数组）类型数据。非必填字段，默认值为空字典对象。

**类型：** Record&lt;string, int \| long \| double \| string \| Uint8Array&gt;

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileUri-details?: Record<string, int | long | double | string | Uint8Array>--><!--Device-FileUri-details?: Record<string, int | long | double | string | Uint8Array>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## fileType

```TypeScript
fileType: string
```

文件类型（必须是标准化数据类型（即\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中各类型对应的UTD-ID或自定义UTD-ID）。fileType最大长度限制为1 024个字节，超出限制时抛出异常。

**类型：** string

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileUri-fileType: string--><!--Device-FileUri-fileType: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## oriUri

```TypeScript
oriUri: string
```

文件的原始URI路径。支持本地文件绝对路径、file://协议和http/https网络URL格式。长度限制为4096字节。例如：\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_、 \_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_或\_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_。

**类型：** string

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileUri-oriUri: string--><!--Device-FileUri-oriUri: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'general.file-uri'
```

统一数据类型标识为文件地址类型数据，固定为“general.file-uri”，数据类型描述信息见 [UniformDataType]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** 'general.file-uri'

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileUri-readonly uniformDataType: 'general.file-uri'--><!--Device-FileUri-readonly uniformDataType: 'general.file-uri'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uriAuthorizationPolicies

```TypeScript
uriAuthorizationPolicies?: Array<int>
```

用于拖拽场景的URI授权策略。默认值为READ+WRITE+PERSIST（读+写+持久化授权）。只针对单个record使用，优先级最高，具体策略见 [UriPermission]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** Array&lt;int&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileUri-uriAuthorizationPolicies?: Array<int>--><!--Device-FileUri-uriAuthorizationPolicies?: Array<int>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

