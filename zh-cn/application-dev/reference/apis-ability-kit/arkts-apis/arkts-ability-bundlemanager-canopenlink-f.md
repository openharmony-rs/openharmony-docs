# canOpenLink

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## canOpenLink

```TypeScript
function canOpenLink(link: string): boolean
```

根据给定的链接判断目标应用是否可访问，链接中的scheme需要在[module.json5文件](../../../../quick-start/module-configuration-file.md)的querySchemes字段下配置。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-bundleManager-function canOpenLink(link: string): boolean--><!--Device-bundleManager-function canOpenLink(link: string): boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| link | string | 是 | 表示需要查询的链接。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示给定的链接可以打开，返回false表示给定的链接不能打开。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700055](../errorcode-bundle.md#17700055-指定的link无效) | The specified link is invalid. |
| [17700056](../errorcode-bundle.md#17700056-指定link的scheme未在queryschemes字段下配置) | The scheme of the specified link is not in the querySchemes. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let link = 'welink://';
  let data = bundleManager.canOpenLink(link);
  hilog.info(0x0000, 'testTag', 'canOpenLink successfully: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'canOpenLink failed: %{public}s', message);
}

```

