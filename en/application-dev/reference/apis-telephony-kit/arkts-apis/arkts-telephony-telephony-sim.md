# @ohos.telephony.sim(SIM Management)

The **sim** module provides basic SIM card management functions. With the APIs provided by this module, you can obtain the ISO country code, home PLMN ID, service provider name, SIM card status, type, installation status, and activation status of the SIM card in the specified slot.

**Since:** 6

<!--Device-unnamed-declare namespace sim--><!--Device-unnamed-declare namespace sim-End-->

**System capability:** SystemCapability.Telephony.CoreService

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getActiveSimAccountInfoList](arkts-telephony-sim-getactivesimaccountinfolist-f.md#getactivesimaccountinfolist1) | Obtains the list of activated SIM card accounts. This API uses an asynchronous callback to return the result. |
| [getActiveSimAccountInfoList](arkts-telephony-sim-getactivesimaccountinfolist-f.md#getactivesimaccountinfolist2) | Obtains the list of activated SIM card accounts. This API uses a promise to return the result. |
| [getCardType](arkts-telephony-sim-getcardtype-f.md#getcardtype1) | Obtains the type of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getCardType](arkts-telephony-sim-getcardtype-f.md#getcardtype2) | Obtains the type of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getCardTypeSync](arkts-telephony-sim-getcardtypesync-f.md#getcardtypesync) | Obtains the type of the SIM card in the specified slot. |
| [getDefaultVoiceSimId](arkts-telephony-sim-getdefaultvoicesimid-f.md#getdefaultvoicesimid1) | Obtains the default slot ID of the SIM card that provides voice services. This API uses an asynchronous callback to return the result. |
| [getDefaultVoiceSimId](arkts-telephony-sim-getdefaultvoicesimid-f.md#getdefaultvoicesimid2) | Obtains the default slot ID of the SIM card that provides voice services. This API uses a promise to return the result. |
| [getDefaultVoiceSlotId](arkts-telephony-sim-getdefaultvoiceslotid-f.md#getdefaultvoiceslotid1) | Obtains the default slot ID of the SIM card that provides voice services. This API uses an asynchronous callback to return the result. |
| [getDefaultVoiceSlotId](arkts-telephony-sim-getdefaultvoiceslotid-f.md#getdefaultvoiceslotid2) | Obtains the default slot ID of the SIM card that provides voice services. This API uses a promise to return the result. |
| [getISOCountryCodeForSim](arkts-telephony-sim-getisocountrycodeforsim-f.md#getisocountrycodeforsim1) | Obtains the ISO country code of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getISOCountryCodeForSim](arkts-telephony-sim-getisocountrycodeforsim-f.md#getisocountrycodeforsim2) | Obtains the ISO country code of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getISOCountryCodeForSimSync](arkts-telephony-sim-getisocountrycodeforsimsync-f.md#getisocountrycodeforsimsync) | Obtains the ISO country code of the SIM card in the specified slot. |
| [getMaxSimCount](arkts-telephony-sim-getmaxsimcount-f.md#getmaxsimcount) | Obtains the number of card slots. |
| [getOpKey](arkts-telephony-sim-getopkey-f.md#getopkey1) | Obtains the opkey of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getOpKey](arkts-telephony-sim-getopkey-f.md#getopkey2) | Obtains the opkey of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getOpKeySync](arkts-telephony-sim-getopkeysync-f.md#getopkeysync) | Obtains the opkey of the SIM card in the specified slot. |
| [getOpName](arkts-telephony-sim-getopname-f.md#getopname1) | Obtains the OpName of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getOpName](arkts-telephony-sim-getopname-f.md#getopname2) | Obtains the OpName of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getOpNameSync](arkts-telephony-sim-getopnamesync-f.md#getopnamesync) | Obtains the OpName of the SIM card in the specified slot. |
| [getSimAccountInfo](arkts-telephony-sim-getsimaccountinfo-f.md#getsimaccountinfo1) | Obtains SIM card account information. This API uses an asynchronous callback to return the result. |
| [getSimAccountInfo](arkts-telephony-sim-getsimaccountinfo-f.md#getsimaccountinfo2) | Obtains SIM card account information. This API uses a promise to return the result. |
| [getSimLabel](arkts-telephony-sim-getsimlabel-f.md#getsimlabel1) | Checks the mapping between card slot IDs and SIM cards. |
| [getSimLabel](arkts-telephony-sim-getsimlabel-f.md#getsimlabel2) | Obtains the SIM card label. This API uses a promise to return the result. |
| [getSimLabelSync](arkts-telephony-sim-getsimlabelsync-f.md#getsimlabelsync) | Obtains the SIM card label based on the specified SIM card slot ID. |
| [getSimOperatorNumeric](arkts-telephony-sim-getsimoperatornumeric-f.md#getsimoperatornumeric1) | Obtains the home public land mobile network (PLMN) ID of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getSimOperatorNumeric](arkts-telephony-sim-getsimoperatornumeric-f.md#getsimoperatornumeric2) | Obtains the home PLMN ID of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getSimOperatorNumericSync](arkts-telephony-sim-getsimoperatornumericsync-f.md#getsimoperatornumericsync) | Obtains the home PLMN ID of the SIM card in the specified slot. This API returns the result synchronously. |
| [getSimSpn](arkts-telephony-sim-getsimspn-f.md#getsimspn1) | Obtains the service provider name (SPN) of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getSimSpn](arkts-telephony-sim-getsimspn-f.md#getsimspn2) | Obtains the SPN of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getSimSpnSync](arkts-telephony-sim-getsimspnsync-f.md#getsimspnsync) | Obtains the SPN of the SIM card in the specified slot. This API returns the result synchronously. |
| [getSimState](arkts-telephony-sim-getsimstate-f.md#getsimstate1) | Obtains the state of the SIM card in the specified slot. This API uses an asynchronous callback to return the result. |
| [getSimState](arkts-telephony-sim-getsimstate-f.md#getsimstate2) | Obtains the state of the SIM card in the specified slot. This API uses a promise to return the result. |
| [getSimStateSync](arkts-telephony-sim-getsimstatesync-f.md#getsimstatesync) | Obtains the state of the SIM card in the specified slot. |
| [hasOperatorPrivileges](arkts-telephony-sim-hasoperatorprivileges-f.md#hasoperatorprivileges1) | Checks whether the application (caller) has been granted the operator permission. This API uses an asynchronous callback to return the result. |
| [hasOperatorPrivileges](arkts-telephony-sim-hasoperatorprivileges-f.md#hasoperatorprivileges2) | Checks whether the application (caller) has been granted the operator permission. This API uses a promise to return the result. |
| [hasSimCard](arkts-telephony-sim-hassimcard-f.md#hassimcard1) | Checks whether the SIM card in the specified slot is installed. This API uses an asynchronous callback to return the result. |
| [hasSimCard](arkts-telephony-sim-hassimcard-f.md#hassimcard2) | Checks whether the SIM card in the specified slot is installed. This API uses a promise to return the result. |
| [hasSimCardSync](arkts-telephony-sim-hassimcardsync-f.md#hassimcardsync) | Checks whether the SIM card in the specified slot is installed. |
| [isSimActive](arkts-telephony-sim-issimactive-f.md#issimactive1) | Checks whether the SIM card in the specified slot is activated. This API uses an asynchronous callback to return the result. |
| [isSimActive](arkts-telephony-sim-issimactive-f.md#issimactive2) | Checks whether the SIM card in the specified slot is activated. This API uses a promise to return the result. |
| [isSimActiveSync](arkts-telephony-sim-issimactivesync-f.md#issimactivesync) | Checks whether the SIM card in the specified slot is activated. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [activateSim](arkts-telephony-sim-activatesim-f-sys.md#activatesim1) | Activate the SIM card in the specified slot. |
| [activateSim](arkts-telephony-sim-activatesim-f-sys.md#activatesim2) | Activate the SIM card in the specified slot. |
| [addIccDiallingNumbers](arkts-telephony-sim-addiccdiallingnumbers-f-sys.md#addiccdiallingnumbers1) | Add dialing number information to SIM card. |
| [addIccDiallingNumbers](arkts-telephony-sim-addiccdiallingnumbers-f-sys.md#addiccdiallingnumbers2) | Add dialing number information to SIM card. |
| [alterPin](arkts-telephony-sim-alterpin-f-sys.md#alterpin1) | Change Pin Password. |
| [alterPin](arkts-telephony-sim-alterpin-f-sys.md#alterpin2) | Change Pin Password. |
| [alterPin2](arkts-telephony-sim-alterpin2-f-sys.md#alterpin21) | Change Pin2 password. |
| [alterPin2](arkts-telephony-sim-alterpin2-f-sys.md#alterpin22) | Change Pin2 password. |
| [deactivateSim](arkts-telephony-sim-deactivatesim-f-sys.md#deactivatesim1) | Disable SIM card in specified slot. |
| [deactivateSim](arkts-telephony-sim-deactivatesim-f-sys.md#deactivatesim2) | Disable SIM card in specified slot. |
| [delIccDiallingNumbers](arkts-telephony-sim-deliccdiallingnumbers-f-sys.md#deliccdiallingnumbers1) | Delete dialing number information on SIM card. |
| [delIccDiallingNumbers](arkts-telephony-sim-deliccdiallingnumbers-f-sys.md#deliccdiallingnumbers2) | Delete dialing number information on SIM card. |
| [getAllSimAccountInfoList](arkts-telephony-sim-getallsimaccountinfolist-f-sys.md#getallsimaccountinfolist1) | Get the list of all SIM card account information. |
| [getAllSimAccountInfoList](arkts-telephony-sim-getallsimaccountinfolist-f-sys.md#getallsimaccountinfolist2) | Get the list of all SIM card account information. |
| [getDsdsMode](arkts-telephony-sim-getdsdsmode-f-sys.md#getdsdsmode1) | Obtains the value of dsds mode. |
| [getDsdsMode](arkts-telephony-sim-getdsdsmode-f-sys.md#getdsdsmode2) | Obtains the value of dsds mode. |
| [getIMSI](arkts-telephony-sim-getimsi-f-sys.md#getimsi1) | Get the international mobile subscriber ID. |
| [getIMSI](arkts-telephony-sim-getimsi-f-sys.md#getimsi2) | Get the international mobile subscriber ID. |
| [getLockState](arkts-telephony-sim-getlockstate-f-sys.md#getlockstate1) | Get the lock status of the SIM card in the specified slot. |
| [getLockState](arkts-telephony-sim-getlockstate-f-sys.md#getlockstate2) | Get the lock status of the SIM card in the specified slot. |
| [getOperatorConfigs](arkts-telephony-sim-getoperatorconfigs-f-sys.md#getoperatorconfigs1) | Obtains the operatorconfigs of the SIM card in a specified slot. |
| [getOperatorConfigs](arkts-telephony-sim-getoperatorconfigs-f-sys.md#getoperatorconfigs2) | Obtains the operatorconfigs of the SIM card in a specified slot. |
| [getShowName](arkts-telephony-sim-getshowname-f-sys.md#getshowname1) | Gets the name of the SIM card in the specified slot. |
| [getShowName](arkts-telephony-sim-getshowname-f-sys.md#getshowname2) | Gets the name of the SIM card in the specified slot. |
| [getShowNumber](arkts-telephony-sim-getshownumber-f-sys.md#getshownumber1) | Get the SIM card number of the specified card slot. |
| [getShowNumber](arkts-telephony-sim-getshownumber-f-sys.md#getshownumber2) | Get the SIM card number of the specified card slot. |
| [getSimAuthentication](arkts-telephony-sim-getsimauthentication-f-sys.md#getsimauthentication) | Performs SIM card authentication. |
| [getSimGid1](arkts-telephony-sim-getsimgid1-f-sys.md#getsimgid11) | Obtains the Group Identifier Level 1 (GID1) of the SIM card in a specified slot. The GID1 is recorded in the EFGID1 file of the SIM card. |
| [getSimGid1](arkts-telephony-sim-getsimgid1-f-sys.md#getsimgid12) | Obtains the Group Identifier Level 1 (GID1) of the SIM card in a specified slot. The GID1 is recorded in the EFGID1 file of the SIM card. |
| [getSimIccId](arkts-telephony-sim-getsimiccid-f-sys.md#getsimiccid1) | Obtains the ICCID of the SIM card in a specified slot. |
| [getSimIccId](arkts-telephony-sim-getsimiccid-f-sys.md#getsimiccid2) | Obtains the ICCID of the SIM card in a specified slot. |
| [getSimTelephoneNumber](arkts-telephony-sim-getsimtelephonenumber-f-sys.md#getsimtelephonenumber1) | Obtains the MSISDN of the SIM card in a specified slot. The MSISDN is recorded in the EFMSISDN file of the SIM card. |
| [getSimTelephoneNumber](arkts-telephony-sim-getsimtelephonenumber-f-sys.md#getsimtelephonenumber2) | Obtains the MSISDN of the SIM card in a specified slot. The MSISDN is recorded in the EFMSISDN file of the SIM card. |
| [getVoiceMailIdentifier](arkts-telephony-sim-getvoicemailidentifier-f-sys.md#getvoicemailidentifier1) | Obtains the alpha identifier of the voice mailbox of the SIM card in a specified slot. |
| [getVoiceMailIdentifier](arkts-telephony-sim-getvoicemailidentifier-f-sys.md#getvoicemailidentifier2) | Obtains the alpha identifier of the voice mailbox of the SIM card in a specified slot. |
| [getVoiceMailNumber](arkts-telephony-sim-getvoicemailnumber-f-sys.md#getvoicemailnumber1) | Obtains the voice mailbox number of the SIM card in a specified slot. |
| [getVoiceMailNumber](arkts-telephony-sim-getvoicemailnumber-f-sys.md#getvoicemailnumber2) | Obtains the voice mailbox number of the SIM card in a specified slot. |
| [isOperatorSimCard](arkts-telephony-sim-isoperatorsimcard-f-sys.md#isoperatorsimcard) | Indicates whether the SIM card in a specified slot is a specified operator. |
| [queryIccDiallingNumbers](arkts-telephony-sim-queryiccdiallingnumbers-f-sys.md#queryiccdiallingnumbers1) | Query dialing number information on SIM card. |
| [queryIccDiallingNumbers](arkts-telephony-sim-queryiccdiallingnumbers-f-sys.md#queryiccdiallingnumbers2) | Query dialing number information on SIM card. |
| [sendEnvelopeCmd](arkts-telephony-sim-sendenvelopecmd-f-sys.md#sendenvelopecmd1) | Send envelope command to SIM card. |
| [sendEnvelopeCmd](arkts-telephony-sim-sendenvelopecmd-f-sys.md#sendenvelopecmd2) | Send envelope command to SIM card. |
| [sendTerminalResponseCmd](arkts-telephony-sim-sendterminalresponsecmd-f-sys.md#sendterminalresponsecmd1) | Send terminal response command to SIM card. |
| [sendTerminalResponseCmd](arkts-telephony-sim-sendterminalresponsecmd-f-sys.md#sendterminalresponsecmd2) | Send terminal response command to SIM card. |
| [setDefaultVoiceSlotId](arkts-telephony-sim-setdefaultvoiceslotid-f-sys.md#setdefaultvoiceslotid1) | Set the card slot ID of the default voice service. |
| [setDefaultVoiceSlotId](arkts-telephony-sim-setdefaultvoiceslotid-f-sys.md#setdefaultvoiceslotid2) | Set the card slot ID of the default voice service. |
| [setLockState](arkts-telephony-sim-setlockstate-f-sys.md#setlockstate1) | Set the lock status of the SIM card in the specified slot. |
| [setLockState](arkts-telephony-sim-setlockstate-f-sys.md#setlockstate2) | Set the lock status of the SIM card in the specified slot. |
| [setShowName](arkts-telephony-sim-setshowname-f-sys.md#setshowname1) | Set the SIM card display name of the specified card slot. |
| [setShowName](arkts-telephony-sim-setshowname-f-sys.md#setshowname2) | Set the SIM card display name of the specified card slot. |
| [setShowNumber](arkts-telephony-sim-setshownumber-f-sys.md#setshownumber1) | Set the SIM card number in the specified slot. |
| [setShowNumber](arkts-telephony-sim-setshownumber-f-sys.md#setshownumber2) | Set the SIM card number in the specified slot. |
| [setSimLabelIndex](arkts-telephony-sim-setsimlabelindex-f-sys.md#setsimlabelindex) | Set the SIM card labelIndex. |
| [setVoiceMailInfo](arkts-telephony-sim-setvoicemailinfo-f-sys.md#setvoicemailinfo1) | Sets the voice mail information. |
| [setVoiceMailInfo](arkts-telephony-sim-setvoicemailinfo-f-sys.md#setvoicemailinfo2) | Sets the voice mail information. |
| [unlockPin](arkts-telephony-sim-unlockpin-f-sys.md#unlockpin1) | Unlock the SIM card password of the specified card slot. |
| [unlockPin](arkts-telephony-sim-unlockpin-f-sys.md#unlockpin2) | Unlock the SIM card password of the specified card slot. |
| [unlockPin2](arkts-telephony-sim-unlockpin2-f-sys.md#unlockpin21) | Unlock the SIM card password of the specified card slot. |
| [unlockPin2](arkts-telephony-sim-unlockpin2-f-sys.md#unlockpin22) | Unlock the SIM card password of the specified card slot. |
| [unlockPuk](arkts-telephony-sim-unlockpuk-f-sys.md#unlockpuk1) | Unlock the SIM card password in the specified card slot. |
| [unlockPuk](arkts-telephony-sim-unlockpuk-f-sys.md#unlockpuk2) | Unlock the SIM card password in the specified card slot. |
| [unlockPuk2](arkts-telephony-sim-unlockpuk2-f-sys.md#unlockpuk21) | Unlock the SIM card password in the specified card slot. |
| [unlockPuk2](arkts-telephony-sim-unlockpuk2-f-sys.md#unlockpuk22) | Unlock the SIM card password in the specified card slot. |
| [unlockSimLock](arkts-telephony-sim-unlocksimlock-f-sys.md#unlocksimlock1) | Unlock SIM card. |
| [unlockSimLock](arkts-telephony-sim-unlocksimlock-f-sys.md#unlocksimlock2) | Unlock SIM card. |
| [updateIccDiallingNumbers](arkts-telephony-sim-updateiccdiallingnumbers-f-sys.md#updateiccdiallingnumbers1) | Update dialing number information on SIM card. |
| [updateIccDiallingNumbers](arkts-telephony-sim-updateiccdiallingnumbers-f-sys.md#updateiccdiallingnumbers2) | Update dialing number information on SIM card. |
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
