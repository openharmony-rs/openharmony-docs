# isStorageTypeSupported

## 导入模块

```TypeScript
import { preferences } from '@kit.ArkData';
```

## isStorageTypeSupported

```TypeScript
function isStorageTypeSupported(type: StorageType): boolean
```

判断当前平台是否支持传入的存储模式，此为同步接口。如果当前平台支持传入的存储模式时，该接口返回true；反之，返回false。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-preferences-function isStorageTypeSupported(type: StorageType): boolean--><!--Device-preferences-function isStorageTypeSupported(type: StorageType): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [StorageType](arkts-arkdata-preferences-storagetype-e.md) | 是 | 需要判断是否支持的存储模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示当前平台支持当前校验的存储模式，false表示当前平台不支持当前校验的存储模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Incorrect parameter types |

**示例：**

```TypeScript
let xmlType = preferences.StorageType.XML;
let gskvType = preferences.StorageType.GSKV;
let isXmlSupported = preferences.isStorageTypeSupported(xmlType);
let isGskvSupported = preferences.isStorageTypeSupported(gskvType);
console.info("Is xml supported in current platform: " + isXmlSupported);
console.info("Is gskv supported in current platform: " + isGskvSupported);

```

