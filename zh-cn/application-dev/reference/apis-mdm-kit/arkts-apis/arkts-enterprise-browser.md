# @ohos.enterprise.browser

本模块提供浏览器管理能力，包括设置/取消浏览器策略、获取浏览器策略等。

浏览器策略指通过配置或管理浏览器行为的一系列规则和设置，以确保安全性、合规性、性能优化和用户体验的一致性。

> **说明：**  
>  
> 本模块接口仅可在Stage模型下使用。  
>  
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../../mdm/mdm-kit-guide.md)。

**起始版本：** 10

<!--Device-unnamed-declare namespace browser--><!--Device-unnamed-declare namespace browser-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { browser } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getManagedBrowserPolicy](arkts-mdm-browser-getmanagedbrowserpolicy-f.md#getmanagedbrowserpolicy-1) | 通过应用包名获取指定浏览器的浏览器策略。 |
| [getPoliciesSync](arkts-mdm-browser-getpoliciessync-f.md#getpoliciessync-1) | 通过appid获取指定浏览器设置的策略。 |
| [getSelfManagedBrowserPolicy](arkts-mdm-browser-getselfmanagedbrowserpolicy-f.md#getselfmanagedbrowserpolicy-1) | 获取当前设备浏览器策略。 |
| [getSelfManagedBrowserPolicyVersion](arkts-mdm-browser-getselfmanagedbrowserpolicyversion-f.md#getselfmanagedbrowserpolicyversion-1) | 获取指定浏览器的浏览器策略版本。 |
| [setManagedBrowserPolicy](arkts-mdm-browser-setmanagedbrowserpolicy-f.md#setmanagedbrowserpolicy-1) | 为指定的浏览器设置浏览器策略，成功后会发布系统公共事件[COMMON_EVENT_MANAGED_BROWSER_POLICY_CHANGED](../../../../reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_managed_browser_policy_changed)。 |
| [setPolicySync](arkts-mdm-browser-setpolicysync-f.md#setpolicysync-1) | 为指定的浏览器设置浏览器子策略。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getPolicies](arkts-mdm-browser-getpolicies-f-sys.md#getpolicies-1) | 获取指定浏览器的策略，使用callback异步回调。 |
| [getPolicies](arkts-mdm-browser-getpolicies-f-sys.md#getpolicies-2) | 获取指定浏览器的策略，使用Promise异步回调。 |
| [setPolicies](arkts-mdm-browser-setpolicies-f-sys.md#setpolicies-1) | 为指定的浏览器设置浏览策略，使用callback异步回调。 |
| [setPolicies](arkts-mdm-browser-setpolicies-f-sys.md#setpolicies-2) | 为指定的浏览器设置浏览策略，使用Promise异步回调。 |
<!--DelEnd-->

