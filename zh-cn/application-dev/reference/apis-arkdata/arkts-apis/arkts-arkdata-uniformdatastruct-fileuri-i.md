# FileUri

文件地址类型数据，用于描述文件的URI地址信息。创建FileUri对象后，可用于文件拖拽、文件共享等场景，支持通过uriAuthorizationPolicies控制文件访问权限，实现跨应用的文件数据传递和权限管理。

**起始版本：** 15

<!--Device-uniformDataStruct-interface FileUri--><!--Device-uniformDataStruct-interface FileUri-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## details

```TypeScript
details?: Record<string, number | number | number | string | Uint8Array>
```

字典类型对象，key为string类型，value可包含number（数值类型）、string（字符串类型）或Uint8Array（二进制字节数组）类型数据。非必填字段，默认值为空字典对象。

**类型：** Record&lt;string, number \| number \| number \| string \| Uint8Array&gt;

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileUri-details?: Record<string, int | long | double | string | Uint8Array>--><!--Device-FileUri-details?: Record<string, int | long | double | string | Uint8Array>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## fileType

```TypeScript
fileType: string
```

文件类型（必须是标准化数据类型（即[UTD预置列表](../../../database/uniform-data-type-list.md)中各类型对应的UTD-ID或自定义UTD-ID）。fileType最大长度限制为1024个字节，超出限制时抛出异常。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileUri-fileType: string--><!--Device-FileUri-fileType: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## oriUri

```TypeScript
oriUri: string
```

文件的原始URI路径。支持本地文件绝对路径、file://协议和http/https网络URL格式。长度限制为4096字节。例如：`/data/local/tmp/test.txt`、`file:///data/local/tmp/test.txt`或`http://example.com/file.txt`。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileUri-oriUri: string--><!--Device-FileUri-oriUri: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'general.file-uri'
```

统一数据类型标识为文件地址类型数据，固定为“general.file-uri”，数据类型描述信息见[UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)。

**类型：** 'general.file-uri'

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileUri-readonly uniformDataType: 'general.file-uri'--><!--Device-FileUri-readonly uniformDataType: 'general.file-uri'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uriAuthorizationPolicies

```TypeScript
uriAuthorizationPolicies?: Array<number>
```

用于拖拽场景的URI授权策略。默认值为READ+WRITE+PERSIST（读+写+持久化授权）。只针对单个record使用，优先级最高，具体策略见[UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md)。

**类型：** Array&lt;number&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileUri-uriAuthorizationPolicies?: Array<int>--><!--Device-FileUri-uriAuthorizationPolicies?: Array<int>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

