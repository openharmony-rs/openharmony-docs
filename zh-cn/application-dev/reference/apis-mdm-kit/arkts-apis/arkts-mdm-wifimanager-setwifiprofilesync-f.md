# setWifiProfileSync

## 导入模块

```TypeScript
import { wifiManager } from '@kit.MDMKit';
```

## setWifiProfileSync

```TypeScript
function setWifiProfileSync(admin: Want, profile: WifiProfile): void
```

为当前设备配置Wi-Fi，连接到指定网络。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_WIFI

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wifiManager-function setWifiProfileSync(admin: Want, profile: WifiProfile): void--><!--Device-wifiManager-function setWifiProfileSync(admin: Want, profile: WifiProfile): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| profile | [WifiProfile](arkts-mdm-wifimanager-wifiprofile-i.md) | 是 | Wi-Fi配置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

适用于公共开放Wi-Fi

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

let profile: wifiManager.WifiProfile = {
  // 需根据实际情况进行替换
  'ssid': 'guest-Wi-Fi',
  'preSharedKey': '',
  'securityType': wifiManager.WifiSecurityType.WIFI_SEC_TYPE_OPEN
};

try {
  wifiManager.setWifiProfileSync(wantTemp, profile);
  console.info(`Succeeded in setting Wi-Fi profile.`);
} catch (err) {
  console.error(`Failed to set Wi-Fi profile. Code: ${err.code}, message: ${err.message}`);
}

```

适用于多个同名Wi-Fi但不同BSSID的场景

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

let profile: wifiManager.WifiProfile = {
  // 需根据实际情况进行替换
  'ssid': 'guest-Wi-Fi',
  'bssid': 'AA:BB:CC:DD:EE:FF',
  'preSharedKey': '',
  'securityType': wifiManager.WifiSecurityType.WIFI_SEC_TYPE_OPEN
};

try {
  wifiManager.setWifiProfileSync(wantTemp, profile);
  console.info(`Succeeded in setting Wi-Fi profile.`);
} catch (err) {
  console.error(`Failed to set Wi-Fi profile. Code: ${err.code}, message: ${err.message}`);
}

```

适用于老旧的工业设备等场景、安全性低

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

let profile: wifiManager.WifiProfile = {
  // 需根据实际情况进行替换
  'ssid': 'Legacy-Office-Wi-Fi',
  'bssid': 'AA:BB:CC:DD:EE:FF',
  'preSharedKey': '',
  'securityType': wifiManager.WifiSecurityType.WIFI_SEC_TYPE_WEP
};

try {
  wifiManager.setWifiProfileSync(wantTemp, profile);
  console.info(`Succeeded in setting Wi-Fi profile.`);
} catch (err) {
  console.error(`Failed to set Wi-Fi profile. Code: ${err.code}, message: ${err.message}`);
}

```

适用于家庭网络、小型办公室、消费级路由器等场景

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

let profile: wifiManager.WifiProfile = {
  // 需根据实际情况进行替换
  'ssid': 'home_Wi-Fi',
  'preSharedKey': 'passwd',
  'securityType': wifiManager.WifiSecurityType.WIFI_SEC_TYPE_PSK
};

try {
  wifiManager.setWifiProfileSync(wantTemp, profile);
  console.info(`Succeeded in setting Wi-Fi profile.`);
} catch (err) {
  console.error(`Failed to set Wi-Fi profile. Code: ${err.code}, message: ${err.message}`);
}

```

适用于现代化IoT设备网络

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

let profile: wifiManager.WifiProfile = {
  // 需根据实际情况进行替换
  'ssid': 'iot_Wi-Fi',
  'preSharedKey': 'passwd',
  'securityType': wifiManager.WifiSecurityType.WIFI_SEC_TYPE_SAE
};

try {
  wifiManager.setWifiProfileSync(wantTemp, profile);
  console.info(`Succeeded in setting Wi-Fi profile.`);
} catch (err) {
  console.error(`Failed to set Wi-Fi profile. Code: ${err.code}, message: ${err.message}`);
}

```

适用于公司网络和大学校园网络

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

// EAP-PEAP 配置示例
let profile: wifiManager.WifiProfile = {
  // 需根据实际情况进行替换
  'ssid': 'company_Wi-Fi',
  'preSharedKey': '',
  'securityType': wifiManager.WifiSecurityType.WIFI_SEC_TYPE_EAP,
  'eapProfile': {
    eapMethod: wifiManager.EapMethod.EAP_PEAP,
    phase2Method: wifiManager.Phase2Method.PHASE2_MSCHAPV2,
    identity: 'zhangsan@company.com',
    password: 'passwd',
    anonymousIdentity: '',
    caPath: '/system/etc/security/caCerts/company-ca.pem',
    caCertAliases:  '',
    clientCertAliases: '',
    certEntry: new Uint8Array(),
    certPassword: '',
    altSubjectMatch: 'CN=radius.company.com,OU=IT Department,O=Company Inc.,C=US',
    domainSuffixMatch: 'company.com',
    realm: '',
    eapSubId: 0,
    plmn: ''
  }
};

try {
  wifiManager.setWifiProfileSync(wantTemp, profile);
  console.info(`Succeeded in setting Wi-Fi profile.`);
} catch (err) {
  console.error(`Failed to set Wi-Fi profile. Code: ${err.code}, message: ${err.message}`);
}

```

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

// EAP-TLS 配置示例
let profile: wifiManager.WifiProfile = {
  // 需根据实际情况进行替换
  'ssid': 'tls_Wi-Fi',
  'preSharedKey': '',
  'securityType': wifiManager.WifiSecurityType.WIFI_SEC_TYPE_EAP,
  'eapProfile': {
    eapMethod: wifiManager.EapMethod.EAP_TLS,
    phase2Method: wifiManager.Phase2Method.PHASE2_NONE,
    identity: 'zhangsan@company.com',
    password: '',
    anonymousIdentity: '',
    caPath: '/system/etc/security/caCerts/company-ca.pem',
    caCertAliases: '',
    clientCertAliases: 'zhangsan-auth-cert',
    certEntry: new Uint8Array(),
    certPassword: '',
    altSubjectMatch: 'CN=radius.company.com,OU=IT Department,O=Company Inc.,C=US',
    domainSuffixMatch: 'company.com',
    realm: '',
    eapSubId: 0,
    plmn: ''
  }
};

try {
  wifiManager.setWifiProfileSync(wantTemp, profile);
  console.info(`Succeeded in setting Wi-Fi profile.`);
} catch (err) {
  console.error(`Failed to set Wi-Fi profile. Code: ${err.code}, message: ${err.message}`);
}

```

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

// EAP-TTLS 配置示例
let profile: wifiManager.WifiProfile = {
  // 需根据实际情况进行替换
  'ssid': 'ttls_Wi-Fi',
  'preSharedKey': '',
  'securityType': wifiManager.WifiSecurityType.WIFI_SEC_TYPE_EAP,
  'eapProfile': {
    eapMethod: wifiManager.EapMethod.EAP_TTLS,
    phase2Method: wifiManager.Phase2Method.PHASE2_GTC,
    identity: 'zhangsan@company.com',
    password: '123456', // 根据令牌生成的动态密码
    anonymousIdentity: '',
    caPath: '',
    caCertAliases: 'company-ca',
    clientCertAliases: '',
    certEntry: new Uint8Array(),
    certPassword: '',
    altSubjectMatch: 'CN=radius.company.com,OU=IT Department,O=Company Inc.,C=US',
    domainSuffixMatch: 'company.com',
    realm: 'company.com',
    plmn: '',
    eapSubId: 0,
  }
};

try {
  wifiManager.setWifiProfileSync(wantTemp, profile);
  console.info(`Succeeded in setting Wi-Fi profile.`);
} catch (err) {
  console.error(`Failed to set Wi-Fi profile. Code: ${err.code}, message: ${err.message}`);
}

```

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

// EAP-SIM 配置示例
let profile: wifiManager.WifiProfile = {
  // 需根据实际情况进行替换
  'ssid': 'eap_sim_Wi-Fi',
  'preSharedKey': '',
  'securityType': wifiManager.WifiSecurityType.WIFI_SEC_TYPE_EAP,
  'eapProfile': {
    eapMethod: wifiManager.EapMethod.EAP_SIM,
    phase2Method: wifiManager.Phase2Method.PHASE2_NONE,
    identity: '',
    password:'',
    anonymousIdentity: '',
    caPath: '',
    caCertAliases:  'carrier-root-ca',
    clientCertAliases: '',
    certEntry: new Uint8Array(),
    certPassword: '',
    altSubjectMatch: 'CN=radius.company.com,OU=IT Department,O=Company Inc.,C=US',
    domainSuffixMatch: 'company.com',
    realm: 'waln.mnc000.mcc460.3gppnetwork.org',
    eapSubId: 0,
    plmn: '46000'
  }
};

try {
  wifiManager.setWifiProfileSync(wantTemp, profile);
  console.info(`Succeeded in setting Wi-Fi profile.`);
} catch (err) {
  console.error(`Failed to set Wi-Fi profile. Code: ${err.code}, message: ${err.message}`);
}

```

适用于需要固定IP地址供客户端访问等场景

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

let profile: wifiManager.WifiProfile = {
  // 需根据实际情况进行替换
  'ssid': 'static_ip_Wi-Fi',
  'preSharedKey': 'passwd',
  'securityType': wifiManager.WifiSecurityType.WIFI_SEC_TYPE_PSK,
  'ipType': wifiManager.IpType.STATIC,
  'staticIp': {
    ipAddress: 3232235778, // 192.168.1.2
    gateway: 3232235777, // 192.168.1.1
    prefixLength: 24,
    dnsServers: [3232235777, 3232235777],
    domains: []
  }
};

try {
  wifiManager.setWifiProfileSync(wantTemp, profile);
  console.info(`Succeeded in setting Wi-Fi profile.`);
} catch (err) {
  console.error(`Failed to set Wi-Fi profile. Code: ${err.code}, message: ${err.message}`);
}

```

