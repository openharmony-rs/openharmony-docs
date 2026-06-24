# isAppKioskAllowed

## isAppKioskAllowed

```TypeScript
function isAppKioskAllowed(appIdentifier: string): boolean
```

��ѯĳӦ���Ƿ�������Kioskģʽ�����С�

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appIdentifier | string | 是 | Ӧ��[Ψһ��ʶ��](../../apis-ability-kit/arkts-apis/arkts-ability-signatureinfo-i.md#SignatureInfo)������ͨ���ӿ�<br/>[bundleManager.getBundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo-3)<br/>��ȡbundleInfo.signatureInfo.appIdentifier�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true��ʾ������Kioskģʽ�����С�false��ʾ��������Kioskģʽ�����С� |

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

