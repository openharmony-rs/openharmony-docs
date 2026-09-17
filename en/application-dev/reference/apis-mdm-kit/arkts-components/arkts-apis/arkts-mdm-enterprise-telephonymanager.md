# @ohos.enterprise.telephonyManager(Telephony Management)

The **telephonyManager** module provides the telephony management capability.

> **NOTE:** 
> 
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see
> [MDM Kit Development](../../../mdm/mdm-kit-guide.md).
> 
> The global restriction policy is provided by **restrictions**. To disable telephony globally, see
> [@ohos.enterprise.restrictions (Restrictions)](arkts-mdm-enterprise-restrictions.md).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { telephonyManager } from '@kit.MDMKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [activeSim](arkts-mdm-telephonymanager-activesim-f.md) | Activates the SIM card in the specified slot. In scenarios where a SIM card is inserted but not yet activated, this API can be used to activate the SIM card without requiring manual user action. After the SIM card is activated, it can be used for communication. To successfully call this API, the SIM card must be inserted and airplane mode must be turned off. |
| [addIncomingCallPolicyNumbers](arkts-mdm-telephonymanager-addincomingcallpolicynumbers-f.md) | Adds the trustlist or blocklist for incoming calls. If no list is set, all numbers can make incoming calls. Once a list is added, only numbers on the list are allowed (or blocked) from making incoming calls. For example, an enterprise can restrict employees to answering only calls from customers, or prohibit them from answering harassment calls. |
| [addOutgoingCallPolicyNumbers](arkts-mdm-telephonymanager-addoutgoingcallpolicynumbers-f.md) | Adds the trustlist or blocklist for outgoing calls. If no list is set, all numbers can make outgoing calls. Once a list is added, only numbers on the list are allowed (or blocked) from making outgoing calls. For example, an enterprise can restrict employees to calling only customer service hotlines, or prohibit them from calling specific numbers. |
| [deactiveSim](arkts-mdm-telephonymanager-deactivesim-f.md) | Deactivates the SIM card in the specified slot. After deactivation, the SIM card in that slot cannot be used for making or receiving calls, sending or receiving SMSs, or accessing the internet. For example, an enterprise can temporarily deactivate a SIM card during employee leave or device maintenance. To successfully call this API, the SIM card must be inserted and airplane mode must be turned off. |
| [getDefaultData](arkts-mdm-telephonymanager-getdefaultdata-f.md) | Obtains the slot ID of the SIM card currently used as the default data SIM card on the device. For example, an enterprise device administrator can query the current default data SIM during device management for data usage control or data card configuration switching. If no SIM card is inserted or the device is in airplane mode, the API returns the slot ID of the last used data SIM card. If the device has never had a default data SIM set, the API returns **0**, indicating slot 1. |
| [getIncomingCallPolicyNumbers](arkts-mdm-telephonymanager-getincomingcallpolicynumbers-f.md) | Obtains the trustlist or blocklist for incoming calls. |
| [getIncomingCallPolicyNumbers](arkts-mdm-telephonymanager-getincomingcallpolicynumbers-f.md) | Obtains the trustlist or blocklist for incoming calls. |
| [getOutgoingCallPolicyNumbers](arkts-mdm-telephonymanager-getoutgoingcallpolicynumbers-f.md) | Obtains the trustlist or blocklist for outgoing calls. |
| [getOutgoingCallPolicyNumbers](arkts-mdm-telephonymanager-getoutgoingcallpolicynumbers-f.md) | Obtains the trustlist or blocklist for outgoing calls. |
| [hangupCalling](arkts-mdm-telephonymanager-hangupcalling-f.md) | Ends the current call. Only carrier calls are supported, excluding MeeTime calls. For example, an enterprise device administrator can forcibly hang up a non-compliant call that an employee is currently on in enterprise security management scenarios. |
| [isSimDisabled](arkts-mdm-telephonymanager-issimdisabled-f.md) | Checks whether the SIM card in a specified slot is disabled. This API is applicable in scenarios where enterprise administrators need to check whether the SIM card disablement policy has taken effect. It helps administrators confirm the policy enforcement status and ensure that call control policies are correctly implemented. |
| [removeIncomingCallPolicyNumbers](arkts-mdm-telephonymanager-removeincomingcallpolicynumbers-f.md) | Removes the trustlist or blocklist for incoming calls. If the list is not set, the removal fails. For example, an enterprise can use this API when lifting incoming call restrictions and restoring employees' normal answering permissions. |
| [removeOutgoingCallPolicyNumbers](arkts-mdm-telephonymanager-removeoutgoingcallpolicynumbers-f.md) | Removes the trustlist or blocklist for outgoing calls. If the list is not set, the removal fails. For example, an enterprise can use this API when removing call restrictions and restoring normal call permissions for employees. |
| [setDefaultData](arkts-mdm-telephonymanager-setdefaultdata-f.md) | Sets the SIM card in the specified slot as the default data SIM card. The device will use the data connection from the SIM card in that slot for internet access. For example, in dual-SIM device management scenarios, an enterprise can specify a default data SIM card for employee devices to centrally manage data usage. To successfully call this API, the SIM card must be inserted and airplane mode must be turned off. |
| [setSimDisabled](arkts-mdm-telephonymanager-setsimdisabled-f.md) | Disables the SIM card in the specified slot. After being disabled, the SIM card in the specified slot cannot be used for making or receiving calls, sending or receiving SMSs, or accessing the internet. For example, an enterprise device administrator can disable the SIM card when an employee leaves the company or a device is lost, preventing unauthorized use. This is applicable in scenarios where enterprises need to restrict employee devices'communication capabilities, such as preventing SIM card misuse after employee departure or device loss, thereby ensuring enterprise communication security and cost control. |
| [setSimEnabled](arkts-mdm-telephonymanager-setsimenabled-f.md) | Enables the SIM card in a specified slot. After it has been disabled with **setSimDisabled**, the card must be turned back on manually in **Settings**  > **Mobile network** > **SIM management**, as this **setSimEnabled** API cannot re-enable it directly. |
