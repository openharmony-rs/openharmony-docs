# @ohos.telephony.sim(SIM Management)

The **sim** module provides basic SIM card management functions. With the APIs provided by this module, you can obtain the ISO country code, home PLMN ID, service provider name, SIM card status, type, installation status, and activation status of the SIM card in the specified slot.

**Since:** 6

**System capability:** SystemCapability.Telephony.CoreService

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getActiveSimAccountInfoList](arkts-telephony-sim-getactivesimaccountinfolist-f.md) | Obtains the list of activated SIM card accounts. This API uses an asynchronous callback to return the result. |
| [getActiveSimAccountInfoList](arkts-telephony-sim-getactivesimaccountinfolist-f.md) | Obtains the list of activated SIM card accounts. This API uses a promise to return the result. |
| [getCardType](arkts-telephony-sim-getcardtype-f.md) | Obtains the type of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getCardType](arkts-telephony-sim-getcardtype-f.md) | Obtains the type of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getCardTypeSync](arkts-telephony-sim-getcardtypesync-f.md) | Obtains the type of the SIM card in the specified slot. |
| [getDefaultVoiceSimId](arkts-telephony-sim-getdefaultvoicesimid-f.md) | Obtains the default slot ID of the SIM card that provides voice services. This API uses an asynchronous callback to return the result. |
| [getDefaultVoiceSimId](arkts-telephony-sim-getdefaultvoicesimid-f.md) | Obtains the default slot ID of the SIM card that provides voice services. This API uses a promise to return the result. |
| [getDefaultVoiceSlotId](arkts-telephony-sim-getdefaultvoiceslotid-f.md) | Obtains the default slot ID of the SIM card that provides voice services. This API uses an asynchronous callback to return the result. |
| [getDefaultVoiceSlotId](arkts-telephony-sim-getdefaultvoiceslotid-f.md) | Obtains the default slot ID of the SIM card that provides voice services. This API uses a promise to return the result. |
| [getISOCountryCodeForSim](arkts-telephony-sim-getisocountrycodeforsim-f.md) | Obtains the ISO country code of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getISOCountryCodeForSim](arkts-telephony-sim-getisocountrycodeforsim-f.md) | Obtains the ISO country code of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getISOCountryCodeForSimSync](arkts-telephony-sim-getisocountrycodeforsimsync-f.md) | Obtains the ISO country code of the SIM card in the specified slot. |
| [getMaxSimCount](arkts-telephony-sim-getmaxsimcount-f.md) | Obtains the number of card slots. |
| [getOpKey](arkts-telephony-sim-getopkey-f.md) | Obtains the opkey of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getOpKey](arkts-telephony-sim-getopkey-f.md) | Obtains the opkey of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getOpKeySync](arkts-telephony-sim-getopkeysync-f.md) | Obtains the opkey of the SIM card in the specified slot. |
| [getOpName](arkts-telephony-sim-getopname-f.md) | Obtains the OpName of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getOpName](arkts-telephony-sim-getopname-f.md) | Obtains the OpName of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getOpNameSync](arkts-telephony-sim-getopnamesync-f.md) | Obtains the OpName of the SIM card in the specified slot. |
| [getSimAccountInfo](arkts-telephony-sim-getsimaccountinfo-f.md) | Obtains SIM card account information. This API uses an asynchronous callback to return the result. |
| [getSimAccountInfo](arkts-telephony-sim-getsimaccountinfo-f.md) | Obtains SIM card account information. This API uses a promise to return the result. |
| [getSimLabel](arkts-telephony-sim-getsimlabel-f.md) | Checks the mapping between card slot IDs and SIM cards. |
| [getSimLabel](arkts-telephony-sim-getsimlabel-f.md) | Obtains the SIM card label. This API uses a promise to return the result. |
| [getSimLabelSync](arkts-telephony-sim-getsimlabelsync-f.md) | Obtains the SIM card label based on the specified SIM card slot ID. |
| [getSimOperatorNumeric](arkts-telephony-sim-getsimoperatornumeric-f.md) | Obtains the home public land mobile network (PLMN) ID of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getSimOperatorNumeric](arkts-telephony-sim-getsimoperatornumeric-f.md) | Obtains the home PLMN ID of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getSimOperatorNumericSync](arkts-telephony-sim-getsimoperatornumericsync-f.md) | Obtains the home PLMN ID of the SIM card in the specified slot. This API returns the result synchronously. |
| [getSimSpn](arkts-telephony-sim-getsimspn-f.md) | Obtains the service provider name (SPN) of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getSimSpn](arkts-telephony-sim-getsimspn-f.md) | Obtains the SPN of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getSimSpnSync](arkts-telephony-sim-getsimspnsync-f.md) | Obtains the SPN of the SIM card in the specified slot. This API returns the result synchronously. |
| [getSimState](arkts-telephony-sim-getsimstate-f.md) | Obtains the state of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getSimState](arkts-telephony-sim-getsimstate-f.md) | Obtains the state of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getSimStateSync](arkts-telephony-sim-getsimstatesync-f.md) | Obtains the state of the SIM card in the specified slot. |
| [hasOperatorPrivileges](arkts-telephony-sim-hasoperatorprivileges-f.md) | Checks whether the application (caller) has been granted the operator permission. This API uses an asynchronous callback to return the result. |
| [hasOperatorPrivileges](arkts-telephony-sim-hasoperatorprivileges-f.md) | Checks whether the application (caller) has been granted the operator permission. This API uses a promise to return the result. |
| [hasSimCard](arkts-telephony-sim-hassimcard-f.md) | Checks whether the SIM card in the specified slot is installed. This API uses an asynchronous callback to return the result. |
| [hasSimCard](arkts-telephony-sim-hassimcard-f.md) | Checks whether the SIM card in the specified slot is installed. This API uses a promise to return the result. |
| [hasSimCardSync](arkts-telephony-sim-hassimcardsync-f.md) | Checks whether the SIM card in the specified slot is installed. |
| [isSimActive](arkts-telephony-sim-issimactive-f.md) | Checks whether the SIM card in the specified slot is activated. This API uses an asynchronous callback to return the result. |
| [isSimActive](arkts-telephony-sim-issimactive-f.md) | Checks whether the SIM card in the specified slot is activated. This API uses a promise to return the result. |
| [isSimActiveSync](arkts-telephony-sim-issimactivesync-f.md) | Checks whether the SIM card in the specified slot is activated. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [activateSim](arkts-telephony-sim-activatesim-f-sys.md) | Activate the SIM card in the specified slot. |
| [activateSim](arkts-telephony-sim-activatesim-f-sys.md) | Activate the SIM card in the specified slot. |
| [addIccDiallingNumbers](arkts-telephony-sim-addiccdiallingnumbers-f-sys.md) | Add dialing number information to SIM card. |
| [addIccDiallingNumbers](arkts-telephony-sim-addiccdiallingnumbers-f-sys.md) | Add dialing number information to SIM card. |
| [alterPin](arkts-telephony-sim-alterpin-f-sys.md) | Change Pin Password. |
| [alterPin](arkts-telephony-sim-alterpin-f-sys.md) | Change Pin Password. |
| [alterPin2](arkts-telephony-sim-alterpin2-f-sys.md) | Change Pin2 password. |
| [alterPin2](arkts-telephony-sim-alterpin2-f-sys.md) | Change Pin2 password. |
| [deactivateSim](arkts-telephony-sim-deactivatesim-f-sys.md) | Disable SIM card in specified slot. |
| [deactivateSim](arkts-telephony-sim-deactivatesim-f-sys.md) | Disable SIM card in specified slot. |
| [delIccDiallingNumbers](arkts-telephony-sim-deliccdiallingnumbers-f-sys.md) | Delete dialing number information on SIM card. |
| [delIccDiallingNumbers](arkts-telephony-sim-deliccdiallingnumbers-f-sys.md) | Delete dialing number information on SIM card. |
| [getAllSimAccountInfoList](arkts-telephony-sim-getallsimaccountinfolist-f-sys.md) | Get the list of all SIM card account information. |
| [getAllSimAccountInfoList](arkts-telephony-sim-getallsimaccountinfolist-f-sys.md) | Get the list of all SIM card account information. |
| [getDsdsMode](arkts-telephony-sim-getdsdsmode-f-sys.md) | Obtains the value of dsds mode. |
| [getDsdsMode](arkts-telephony-sim-getdsdsmode-f-sys.md) | Obtains the value of dsds mode. |
| [getIMSI](arkts-telephony-sim-getimsi-f-sys.md) | Get the international mobile subscriber ID. |
| [getIMSI](arkts-telephony-sim-getimsi-f-sys.md) | Get the international mobile subscriber ID. |
| [getLockState](arkts-telephony-sim-getlockstate-f-sys.md) | Get the lock status of the SIM card in the specified slot. |
| [getLockState](arkts-telephony-sim-getlockstate-f-sys.md) | Get the lock status of the SIM card in the specified slot. |
| [getOperatorConfigs](arkts-telephony-sim-getoperatorconfigs-f-sys.md) | Obtains the operatorconfigs of the SIM card in a specified slot. |
| [getOperatorConfigs](arkts-telephony-sim-getoperatorconfigs-f-sys.md) | Obtains the operatorconfigs of the SIM card in a specified slot. |
| [getShowName](arkts-telephony-sim-getshowname-f-sys.md) | Gets the name of the SIM card in the specified slot. |
| [getShowName](arkts-telephony-sim-getshowname-f-sys.md) | Gets the name of the SIM card in the specified slot. |
| [getShowNumber](arkts-telephony-sim-getshownumber-f-sys.md) | Get the SIM card number of the specified card slot. |
| [getShowNumber](arkts-telephony-sim-getshownumber-f-sys.md) | Get the SIM card number of the specified card slot. |
| [getSimAuthentication](arkts-telephony-sim-getsimauthentication-f-sys.md) | Performs SIM card authentication. |
| [getSimGid1](arkts-telephony-sim-getsimgid1-f-sys.md) | Obtains the Group Identifier Level 1 (GID1) of the SIM card in a specified slot. The GID1 is recorded in the EFGID1 file of the SIM card. |
| [getSimGid1](arkts-telephony-sim-getsimgid1-f-sys.md) | Obtains the Group Identifier Level 1 (GID1) of the SIM card in a specified slot. The GID1 is recorded in the EFGID1 file of the SIM card. |
| [getSimIccId](arkts-telephony-sim-getsimiccid-f-sys.md) | Obtains the ICCID of the SIM card in a specified slot. |
| [getSimIccId](arkts-telephony-sim-getsimiccid-f-sys.md) | Obtains the ICCID of the SIM card in a specified slot. |
| [getSimTelephoneNumber](arkts-telephony-sim-getsimtelephonenumber-f-sys.md) | Obtains the MSISDN of the SIM card in a specified slot. The MSISDN is recorded in the EFMSISDN file of the SIM card. |
| [getSimTelephoneNumber](arkts-telephony-sim-getsimtelephonenumber-f-sys.md) | Obtains the MSISDN of the SIM card in a specified slot. The MSISDN is recorded in the EFMSISDN file of the SIM card. |
| [getVoiceMailIdentifier](arkts-telephony-sim-getvoicemailidentifier-f-sys.md) | Obtains the alpha identifier of the voice mailbox of the SIM card in a specified slot. |
| [getVoiceMailIdentifier](arkts-telephony-sim-getvoicemailidentifier-f-sys.md) | Obtains the alpha identifier of the voice mailbox of the SIM card in a specified slot. |
| [getVoiceMailNumber](arkts-telephony-sim-getvoicemailnumber-f-sys.md) | Obtains the voice mailbox number of the SIM card in a specified slot. |
| [getVoiceMailNumber](arkts-telephony-sim-getvoicemailnumber-f-sys.md) | Obtains the voice mailbox number of the SIM card in a specified slot. |
| [isOperatorSimCard](arkts-telephony-sim-isoperatorsimcard-f-sys.md) | Indicates whether the SIM card in a specified slot is a specified operator. |
| [queryIccDiallingNumbers](arkts-telephony-sim-queryiccdiallingnumbers-f-sys.md) | Query dialing number information on SIM card. |
| [queryIccDiallingNumbers](arkts-telephony-sim-queryiccdiallingnumbers-f-sys.md) | Query dialing number information on SIM card. |
| [sendEnvelopeCmd](arkts-telephony-sim-sendenvelopecmd-f-sys.md) | Send envelope command to SIM card. |
| [sendEnvelopeCmd](arkts-telephony-sim-sendenvelopecmd-f-sys.md) | Send envelope command to SIM card. |
| [sendTerminalResponseCmd](arkts-telephony-sim-sendterminalresponsecmd-f-sys.md) | Send terminal response command to SIM card. |
| [sendTerminalResponseCmd](arkts-telephony-sim-sendterminalresponsecmd-f-sys.md) | Send terminal response command to SIM card. |
| [setDefaultVoiceSlotId](arkts-telephony-sim-setdefaultvoiceslotid-f-sys.md) | Set the card slot ID of the default voice service. |
| [setDefaultVoiceSlotId](arkts-telephony-sim-setdefaultvoiceslotid-f-sys.md) | Set the card slot ID of the default voice service. |
| [setLockState](arkts-telephony-sim-setlockstate-f-sys.md) | Set the lock status of the SIM card in the specified slot. |
| [setLockState](arkts-telephony-sim-setlockstate-f-sys.md) | Set the lock status of the SIM card in the specified slot. |
| [setShowName](arkts-telephony-sim-setshowname-f-sys.md) | Set the SIM card display name of the specified card slot. |
| [setShowName](arkts-telephony-sim-setshowname-f-sys.md) | Set the SIM card display name of the specified card slot. |
| [setShowNumber](arkts-telephony-sim-setshownumber-f-sys.md) | Set the SIM card number in the specified slot. |
| [setShowNumber](arkts-telephony-sim-setshownumber-f-sys.md) | Set the SIM card number in the specified slot. |
| [setSimLabelIndex](arkts-telephony-sim-setsimlabelindex-f-sys.md) | Set the SIM card labelIndex. |
| [setVoiceMailInfo](arkts-telephony-sim-setvoicemailinfo-f-sys.md) | Sets the voice mail information. |
| [setVoiceMailInfo](arkts-telephony-sim-setvoicemailinfo-f-sys.md) | Sets the voice mail information. |
| [unlockPin](arkts-telephony-sim-unlockpin-f-sys.md) | Unlock the SIM card password of the specified card slot. |
| [unlockPin](arkts-telephony-sim-unlockpin-f-sys.md) | Unlock the SIM card password of the specified card slot. |
| [unlockPin2](arkts-telephony-sim-unlockpin2-f-sys.md) | Unlock the SIM card password of the specified card slot. |
| [unlockPin2](arkts-telephony-sim-unlockpin2-f-sys.md) | Unlock the SIM card password of the specified card slot. |
| [unlockPuk](arkts-telephony-sim-unlockpuk-f-sys.md) | Unlock the SIM card password in the specified card slot. |
| [unlockPuk](arkts-telephony-sim-unlockpuk-f-sys.md) | Unlock the SIM card password in the specified card slot. |
| [unlockPuk2](arkts-telephony-sim-unlockpuk2-f-sys.md) | Unlock the SIM card password in the specified card slot. |
| [unlockPuk2](arkts-telephony-sim-unlockpuk2-f-sys.md) | Unlock the SIM card password in the specified card slot. |
| [unlockSimLock](arkts-telephony-sim-unlocksimlock-f-sys.md) | Unlock SIM card. |
| [unlockSimLock](arkts-telephony-sim-unlocksimlock-f-sys.md) | Unlock SIM card. |
| [updateIccDiallingNumbers](arkts-telephony-sim-updateiccdiallingnumbers-f-sys.md) | Update dialing number information on SIM card. |
| [updateIccDiallingNumbers](arkts-telephony-sim-updateiccdiallingnumbers-f-sys.md) | Update dialing number information on SIM card. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i.md) | Defines the ICC account information. |
| [SimLabel](arkts-telephony-sim-simlabel-i.md) | Defines the SIM card label. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DiallingNumbersInfo](arkts-telephony-sim-diallingnumbersinfo-i-sys.md) | Defines the contact number information. |
| [IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i-sys.md) | Defines the ICC account information. |
| [LockInfo](arkts-telephony-sim-lockinfo-i-sys.md) | Defines the personalized lock information. |
| [LockStatusResponse](arkts-telephony-sim-lockstatusresponse-i-sys.md) | Defines the personalized lock information. |
| [OperatorConfig](arkts-telephony-sim-operatorconfig-i-sys.md) | Defines the carrier configuration. |
| [PersoLockInfo](arkts-telephony-sim-persolockinfo-i-sys.md) | Defines the personalized lock information. |
| [SimAuthenticationResponse](arkts-telephony-sim-simauthenticationresponse-i-sys.md) | Defines the SIM card authentication response. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [CardType](arkts-telephony-sim-cardtype-e.md) | Enumerates SIM card types. |
| [SimState](arkts-telephony-sim-simstate-e.md) | Enumerates SIM card states. |
| [SimType](arkts-telephony-sim-simtype-e.md) | Enumerates the SIM card types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [AuthType](arkts-telephony-sim-authtype-e-sys.md) | Indicates the Authentication type |
| [ContactType](arkts-telephony-sim-contacttype-e-sys.md) | Indicates the contact types. |
| [DsdsMode](arkts-telephony-sim-dsdsmode-e-sys.md) | Indicates the Dsds Mode. |
| [LockState](arkts-telephony-sim-lockstate-e-sys.md) | Indicates the lock states. |
| [LockType](arkts-telephony-sim-locktype-e-sys.md) | Indicates the lock types. |
| [OperatorConfigKey](arkts-telephony-sim-operatorconfigkey-e-sys.md) | Indicates the carrier configuration keys. |
| [OperatorSimCard](arkts-telephony-sim-operatorsimcard-e-sys.md) | Indicates the operator of SIM. |
| [PersoLockType](arkts-telephony-sim-persolocktype-e-sys.md) | Indicates the personalized lock types. |
<!--DelEnd-->
