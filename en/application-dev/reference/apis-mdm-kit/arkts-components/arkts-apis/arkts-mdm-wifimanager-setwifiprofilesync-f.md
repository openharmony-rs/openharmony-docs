# setWifiProfileSync

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.MDMKit';
```

## setWifiProfileSync

```TypeScript
function setWifiProfileSync(admin: Want, profile: WifiProfile): void
```

Configures Wi-Fi for the current device to connect to a specified network.

**Since:** 12

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_WIFI

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| profile | [WifiProfile](arkts-mdm-wifimanager-wifiprofile-i.md) | Yes | Wi-Fi configuration information, which is used to specify the configuration parameters of the Wi-Fi network to be connected, including the SSID, BSSID, key, and security type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

Scenario 1: public Wi-Fi development

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

let profile: wifiManager.WifiProfile = {
  // Replace with actual values.
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

Scenario 2: Multiple Wi-Fi networks with the same name but different BSSIDs

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

let profile: wifiManager.WifiProfile = {
  // Replace with actual values.
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

Scenario 3: old industrial devices with low security

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

let profile: wifiManager.WifiProfile = {
  // Replace with actual values.
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

Scenario 4: home networks, small offices, and consumer routers

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

let profile: wifiManager.WifiProfile = {
  // Replace with actual values.
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

Scenario 5: modern IoT device networks

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

let profile: wifiManager.WifiProfile = {
  // Replace with actual values.
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

Scenario 6: company networks and university campus networks

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

// EAP-PEAP configuration example
let profile: wifiManager.WifiProfile = {
  // Replace with actual values.
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
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

// EAP-TLS configuration example
let profile: wifiManager.WifiProfile = {
  // Replace with actual values.
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
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

// EAP-TTLS configuration example
let profile: wifiManager.WifiProfile = {
  // Replace with actual values.
  'ssid': 'ttls_Wi-Fi',
  'preSharedKey': '',
  'securityType': wifiManager.WifiSecurityType.WIFI_SEC_TYPE_EAP,
  'eapProfile': {
    eapMethod: wifiManager.EapMethod.EAP_TTLS,
    phase2Method: wifiManager.Phase2Method.PHASE2_GTC,
    identity: 'zhangsan@company.com',
    password: '123456', // Dynamic password generated based on the token.
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
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

// EAP-SIM configuration example
let profile: wifiManager.WifiProfile = {
  // Replace with actual values.
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

Scenario 7: fixed IP address for client access

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};

let profile: wifiManager.WifiProfile = {
  // Replace with actual values.
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
