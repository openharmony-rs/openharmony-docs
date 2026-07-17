# isAppKioskAllowed

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## isAppKioskAllowed

```TypeScript
function isAppKioskAllowed(appIdentifier: string): boolean
```

查询某应用是否允许在Kiosk模式下运行。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function isAppKioskAllowed(appIdentifier: string): boolean--><!--Device-applicationManager-function isAppKioskAllowed(appIdentifier: string): boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appIdentifier | string | 是 | 应用[唯一标识符](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-signatureinfo-i.md)，可以通过接口[bundleManager.getBundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfo-f.md#getbundleinfo-3)获取bundleInfo.signatureInfo.appIdentifier。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示允许在Kiosk模式下运行。false表示不允许在Kiosk模式下运行。 |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';

try {
  // 需根据实际情况进行替换
  let isAllowed: boolean = applicationManager.isAppKioskAllowed('6917****3569');
  console.info(`Succeeded in querying if the app is allowed kiosk, isAllowed: ${isAllowed}`);
} catch (err) {
  console.error(`Failed to query if the app is allowed kiosk. Code is ${err.code}, message is ${err.message}`);
}

```

