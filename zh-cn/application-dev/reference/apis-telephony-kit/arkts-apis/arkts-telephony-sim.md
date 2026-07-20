# @ohos.telephony.sim

Provides applications with APIs for obtaining SIM card status, card file information, and card specifications.SIM cards include SIM, USIM, and CSIM cards.

**起始版本：** 6

<!--Device-unnamed-declare namespace sim--><!--Device-unnamed-declare namespace sim-End-->

**系统能力：** SystemCapability.Telephony.CoreService

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getActiveSimAccountInfoList](arkts-telephony-sim-getactivesimaccountinfolist-f.md#getactivesimaccountinfolist) | Get the list of active SIM card account information. |
| [getActiveSimAccountInfoList](arkts-telephony-sim-getactivesimaccountinfolist-f.md#getactivesimaccountinfolist-1) | Get the list of active SIM card account information. |
| [getCardType](arkts-telephony-sim-getcardtype-f.md#getcardtype) | Obtains the type of the SIM card installed in a specified slot. |
| [getCardType](arkts-telephony-sim-getcardtype-f.md#getcardtype-1) | Obtains the type of the SIM card installed in a specified slot. |
| [getCardTypeSync](arkts-telephony-sim-getcardtypesync-f.md#getcardtypesync) | Obtains the type of the SIM card inserted in a specified slot. |
| [getDefaultVoiceSimId](arkts-telephony-sim-getdefaultvoicesimid-f.md#getdefaultvoicesimid) | Obtains the default SIM ID for the voice service. |
| [getDefaultVoiceSimId](arkts-telephony-sim-getdefaultvoicesimid-f.md#getdefaultvoicesimid-1) | Obtains the default SIM ID for the voice service. |
| [getDefaultVoiceSlotId](arkts-telephony-sim-getdefaultvoiceslotid-f.md#getdefaultvoiceslotid) | Obtains the default card slot for the voice service. |
| [getDefaultVoiceSlotId](arkts-telephony-sim-getdefaultvoiceslotid-f.md#getdefaultvoiceslotid-1) | Obtains the default card slot for the voice service. |
| [getISOCountryCodeForSim](arkts-telephony-sim-getisocountrycodeforsim-f.md#getisocountrycodeforsim) | Obtains the ISO country code of the SIM card in a specified slot. |
| [getISOCountryCodeForSim](arkts-telephony-sim-getisocountrycodeforsim-f.md#getisocountrycodeforsim-1) | Obtains the ISO country code of the SIM card in a specified slot. |
| [getISOCountryCodeForSimSync](arkts-telephony-sim-getisocountrycodeforsimsync-f.md#getisocountrycodeforsimsync) | Obtains the ISO country code of the SIM card in a specified slot. |
| [getMaxSimCount](arkts-telephony-sim-getmaxsimcount-f.md#getmaxsimcount) | Obtains the maximum number of SIM cards that can be used simultaneously on the device,that is, the maximum number of SIM card slots. |
| [getOpKey](arkts-telephony-sim-getopkey-f.md#getopkey) | Obtains the operator key of the SIM card in a specified slot. |
| [getOpKey](arkts-telephony-sim-getopkey-f.md#getopkey-1) | Obtains the operator key of the SIM card in a specified slot. |
| [getOpKeySync](arkts-telephony-sim-getopkeysync-f.md#getopkeysync) | Obtains the operator key of the SIM card in a specified slot. |
| [getOpName](arkts-telephony-sim-getopname-f.md#getopname) | Obtains the operator name of the SIM card in a specified slot. |
| [getOpName](arkts-telephony-sim-getopname-f.md#getopname-1) | Obtains the operator name of the SIM card in a specified slot. |
| [getOpNameSync](arkts-telephony-sim-getopnamesync-f.md#getopnamesync) | Obtains the operator name of the SIM card in a specified slot. |
| [getSimAccountInfo](arkts-telephony-sim-getsimaccountinfo-f.md#getsimaccountinfo) | Get account information of SIM card. |
| [getSimAccountInfo](arkts-telephony-sim-getsimaccountinfo-f.md#getsimaccountinfo-1) | Get account information of SIM card. |
| [getSimLabel](arkts-telephony-sim-getsimlabel-f.md#getsimlabel) | Obtains the SIM card label. |
| [getSimLabel](arkts-telephony-sim-getsimlabel-f.md#getsimlabel-1) | 获取SIM卡标签名称 |
| [getSimLabelSync](arkts-telephony-sim-getsimlabelsync-f.md#getsimlabelsync) | Obtains the SIM card label synchronously. |
| [getSimOperatorNumeric](arkts-telephony-sim-getsimoperatornumeric-f.md#getsimoperatornumeric) | Obtains the home PLMN number of the SIM card in a specified slot.  <p>The value is recorded in the SIM card and is irrelevant to the network with which the SIM card is currently registered. |
| [getSimOperatorNumeric](arkts-telephony-sim-getsimoperatornumeric-f.md#getsimoperatornumeric-1) | Obtains the home PLMN number of the SIM card in a specified slot.  <p>The value is recorded in the SIM card and is irrelevant to the network with which the SIM card is currently registered. |
| [getSimOperatorNumericSync](arkts-telephony-sim-getsimoperatornumericsync-f.md#getsimoperatornumericsync) | Obtains the home PLMN number of the SIM card in a specified slot.  <p>The value is recorded in the SIM card and is irrelevant to the network with which the SIM card is currently registered. |
| [getSimSpn](arkts-telephony-sim-getsimspn-f.md#getsimspn) | Obtains the service provider name (SPN) of the SIM card in a specified slot.  <p>The value is recorded in the EFSPN file of the SIM card and is irrelevant to the network with which the SIM card is currently registered. |
| [getSimSpn](arkts-telephony-sim-getsimspn-f.md#getsimspn-1) | Obtains the service provider name (SPN) of the SIM card in a specified slot.  <p>The value is recorded in the EFSPN file of the SIM card and is irrelevant to the network with which the SIM card is currently registered. |
| [getSimSpnSync](arkts-telephony-sim-getsimspnsync-f.md#getsimspnsync) | Obtains the service provider name (SPN) of the SIM card in a specified slot.  <p>The value is recorded in the EFSPN file of the SIM card and is irrelevant to the network with which the SIM card is currently registered. |
| [getSimState](arkts-telephony-sim-getsimstate-f.md#getsimstate) | Obtains the state of the SIM card in a specified slot. |
| [getSimState](arkts-telephony-sim-getsimstate-f.md#getsimstate-1) | Obtains the state of the SIM card in a specified slot. |
| [getSimStateSync](arkts-telephony-sim-getsimstatesync-f.md#getsimstatesync) | Obtains the state of the SIM card in a specified slot. |
| [hasOperatorPrivileges](arkts-telephony-sim-hasoperatorprivileges-f.md#hasoperatorprivileges) | Checks whether your application (the caller) has been granted the operator permissions. |
| [hasOperatorPrivileges](arkts-telephony-sim-hasoperatorprivileges-f.md#hasoperatorprivileges-1) | Checks whether your application (the caller) has been granted the operator permissions. |
| [hasSimCard](arkts-telephony-sim-hassimcard-f.md#hassimcard) | Checks whether a SIM card is inserted in a specified slot. |
| [hasSimCard](arkts-telephony-sim-hassimcard-f.md#hassimcard-1) | Checks whether a SIM card is inserted in a specified slot. |
| [hasSimCardSync](arkts-telephony-sim-hassimcardsync-f.md#hassimcardsync) | Checks whether a SIM card is inserted in a specified slot. |
| [isSimActive](arkts-telephony-sim-issimactive-f.md#issimactive) | Checks whether the SIM card in a specified slot is activated. |
| [isSimActive](arkts-telephony-sim-issimactive-f.md#issimactive-1) | Checks whether the SIM card in a specified slot is activated. |
| [isSimActiveSync](arkts-telephony-sim-issimactivesync-f.md#issimactivesync) | Checks whether the SIM card in a specified slot is activated. |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [activateSim](arkts-telephony-sim-activatesim-f-sys.md#activatesim) | Activate the SIM card in the specified slot. |
| [activateSim](arkts-telephony-sim-activatesim-f-sys.md#activatesim-1) | Activate the SIM card in the specified slot. |
| [addIccDiallingNumbers](arkts-telephony-sim-addiccdiallingnumbers-f-sys.md#addiccdiallingnumbers) | Add dialing number information to SIM card. |
| [addIccDiallingNumbers](arkts-telephony-sim-addiccdiallingnumbers-f-sys.md#addiccdiallingnumbers-1) | Add dialing number information to SIM card. |
| [alterPin](arkts-telephony-sim-alterpin-f-sys.md#alterpin) | Change Pin Password. |
| [alterPin](arkts-telephony-sim-alterpin-f-sys.md#alterpin-1) | Change Pin Password. |
| [alterPin2](arkts-telephony-sim-alterpin2-f-sys.md#alterpin2) | Change Pin2 password. |
| [alterPin2](arkts-telephony-sim-alterpin2-f-sys.md#alterpin2-1) | Change Pin2 password. |
| [deactivateSim](arkts-telephony-sim-deactivatesim-f-sys.md#deactivatesim) | Disable SIM card in specified slot. |
| [deactivateSim](arkts-telephony-sim-deactivatesim-f-sys.md#deactivatesim-1) | Disable SIM card in specified slot. |
| [delIccDiallingNumbers](arkts-telephony-sim-deliccdiallingnumbers-f-sys.md#deliccdiallingnumbers) | Delete dialing number information on SIM card. |
| [delIccDiallingNumbers](arkts-telephony-sim-deliccdiallingnumbers-f-sys.md#deliccdiallingnumbers-1) | Delete dialing number information on SIM card. |
| [getAllSimAccountInfoList](arkts-telephony-sim-getallsimaccountinfolist-f-sys.md#getallsimaccountinfolist) | Get the list of all SIM card account information. |
| [getAllSimAccountInfoList](arkts-telephony-sim-getallsimaccountinfolist-f-sys.md#getallsimaccountinfolist-1) | Get the list of all SIM card account information. |
| [getDsdsMode](arkts-telephony-sim-getdsdsmode-f-sys.md#getdsdsmode) | Obtains the value of dsds mode. |
| [getDsdsMode](arkts-telephony-sim-getdsdsmode-f-sys.md#getdsdsmode-1) | Obtains the value of dsds mode. |
| [getIMSI](arkts-telephony-sim-getimsi-f-sys.md#getimsi) | Get the international mobile subscriber ID. |
| [getIMSI](arkts-telephony-sim-getimsi-f-sys.md#getimsi-1) | Get the international mobile subscriber ID. |
| [getLockState](arkts-telephony-sim-getlockstate-f-sys.md#getlockstate) | Get the lock status of the SIM card in the specified slot. |
| [getLockState](arkts-telephony-sim-getlockstate-f-sys.md#getlockstate-1) | Get the lock status of the SIM card in the specified slot. |
| [getOperatorConfigs](arkts-telephony-sim-getoperatorconfigs-f-sys.md#getoperatorconfigs) | Obtains the operatorconfigs of the SIM card in a specified slot. |
| [getOperatorConfigs](arkts-telephony-sim-getoperatorconfigs-f-sys.md#getoperatorconfigs-1) | Obtains the operatorconfigs of the SIM card in a specified slot. |
| [getShowName](arkts-telephony-sim-getshowname-f-sys.md#getshowname) | Gets the name of the SIM card in the specified slot. |
| [getShowName](arkts-telephony-sim-getshowname-f-sys.md#getshowname-1) | Gets the name of the SIM card in the specified slot. |
| [getShowNumber](arkts-telephony-sim-getshownumber-f-sys.md#getshownumber) | Get the SIM card number of the specified card slot. |
| [getShowNumber](arkts-telephony-sim-getshownumber-f-sys.md#getshownumber-1) | Get the SIM card number of the specified card slot. |
| [getSimAuthentication](arkts-telephony-sim-getsimauthentication-f-sys.md#getsimauthentication) | Performs SIM card authentication. |
| [getSimGid1](arkts-telephony-sim-getsimgid1-f-sys.md#getsimgid1) | Obtains the Group Identifier Level 1 (GID1) of the SIM card in a specified slot.The GID1 is recorded in the EFGID1 file of the SIM card. |
| [getSimGid1](arkts-telephony-sim-getsimgid1-f-sys.md#getsimgid1-1) | Obtains the Group Identifier Level 1 (GID1) of the SIM card in a specified slot.The GID1 is recorded in the EFGID1 file of the SIM card. |
| [getSimIccId](arkts-telephony-sim-getsimiccid-f-sys.md#getsimiccid) | Obtains the ICCID of the SIM card in a specified slot.  <p>The ICCID is a unique identifier of a SIM card. It consists of 20 digits and is recorded in the EFICCID file of the SIM card. |
| [getSimIccId](arkts-telephony-sim-getsimiccid-f-sys.md#getsimiccid-1) | Obtains the ICCID of the SIM card in a specified slot.  <p>The ICCID is a unique identifier of a SIM card. It consists of 20 digits and is recorded in the EFICCID file of the SIM card. |
| [getSimTelephoneNumber](arkts-telephony-sim-getsimtelephonenumber-f-sys.md#getsimtelephonenumber) | Obtains the MSISDN of the SIM card in a specified slot.The MSISDN is recorded in the EFMSISDN file of the SIM card. |
| [getSimTelephoneNumber](arkts-telephony-sim-getsimtelephonenumber-f-sys.md#getsimtelephonenumber-1) | Obtains the MSISDN of the SIM card in a specified slot.The MSISDN is recorded in the EFMSISDN file of the SIM card. |
| [getVoiceMailIdentifier](arkts-telephony-sim-getvoicemailidentifier-f-sys.md#getvoicemailidentifier) | Obtains the alpha identifier of the voice mailbox of the SIM card in a specified slot. |
| [getVoiceMailIdentifier](arkts-telephony-sim-getvoicemailidentifier-f-sys.md#getvoicemailidentifier-1) | Obtains the alpha identifier of the voice mailbox of the SIM card in a specified slot. |
| [getVoiceMailNumber](arkts-telephony-sim-getvoicemailnumber-f-sys.md#getvoicemailnumber) | Obtains the voice mailbox number of the SIM card in a specified slot. |
| [getVoiceMailNumber](arkts-telephony-sim-getvoicemailnumber-f-sys.md#getvoicemailnumber-1) | Obtains the voice mailbox number of the SIM card in a specified slot. |
| [isOperatorSimCard](arkts-telephony-sim-isoperatorsimcard-f-sys.md#isoperatorsimcard) | Indicates whether the SIM card in a specified slot is a specified operator. |
| [queryIccDiallingNumbers](arkts-telephony-sim-queryiccdiallingnumbers-f-sys.md#queryiccdiallingnumbers) | Query dialing number information on SIM card. |
| [queryIccDiallingNumbers](arkts-telephony-sim-queryiccdiallingnumbers-f-sys.md#queryiccdiallingnumbers-1) | Query dialing number information on SIM card. |
| [sendEnvelopeCmd](arkts-telephony-sim-sendenvelopecmd-f-sys.md#sendenvelopecmd) | Send envelope command to SIM card. |
| [sendEnvelopeCmd](arkts-telephony-sim-sendenvelopecmd-f-sys.md#sendenvelopecmd-1) | Send envelope command to SIM card. |
| [sendTerminalResponseCmd](arkts-telephony-sim-sendterminalresponsecmd-f-sys.md#sendterminalresponsecmd) | Send terminal response command to SIM card. |
| [sendTerminalResponseCmd](arkts-telephony-sim-sendterminalresponsecmd-f-sys.md#sendterminalresponsecmd-1) | Send terminal response command to SIM card. |
| [setDefaultVoiceSlotId](arkts-telephony-sim-setdefaultvoiceslotid-f-sys.md#setdefaultvoiceslotid) | Set the card slot ID of the default voice service. |
| [setDefaultVoiceSlotId](arkts-telephony-sim-setdefaultvoiceslotid-f-sys.md#setdefaultvoiceslotid-1) | Set the card slot ID of the default voice service. |
| [setLockState](arkts-telephony-sim-setlockstate-f-sys.md#setlockstate) | Set the lock status of the SIM card in the specified slot. |
| [setLockState](arkts-telephony-sim-setlockstate-f-sys.md#setlockstate-1) | Set the lock status of the SIM card in the specified slot. |
| [setShowName](arkts-telephony-sim-setshowname-f-sys.md#setshowname) | Set the SIM card display name of the specified card slot. |
| [setShowName](arkts-telephony-sim-setshowname-f-sys.md#setshowname-1) | Set the SIM card display name of the specified card slot. |
| [setShowNumber](arkts-telephony-sim-setshownumber-f-sys.md#setshownumber) | Set the SIM card number in the specified slot. |
| [setShowNumber](arkts-telephony-sim-setshownumber-f-sys.md#setshownumber-1) | Set the SIM card number in the specified slot. |
| [setSimLabelIndex](arkts-telephony-sim-setsimlabelindex-f-sys.md#setsimlabelindex) | 设置SIM卡标签索引。 |
| [setVoiceMailInfo](arkts-telephony-sim-setvoicemailinfo-f-sys.md#setvoicemailinfo) | Sets the voice mail information. |
| [setVoiceMailInfo](arkts-telephony-sim-setvoicemailinfo-f-sys.md#setvoicemailinfo-1) | Sets the voice mail information. |
| [unlockPin](arkts-telephony-sim-unlockpin-f-sys.md#unlockpin) | Unlock the SIM card password of the specified card slot. |
| [unlockPin](arkts-telephony-sim-unlockpin-f-sys.md#unlockpin-1) | Unlock the SIM card password of the specified card slot. |
| [unlockPin2](arkts-telephony-sim-unlockpin2-f-sys.md#unlockpin2) | Unlock the SIM card password of the specified card slot. |
| [unlockPin2](arkts-telephony-sim-unlockpin2-f-sys.md#unlockpin2-1) | Unlock the SIM card password of the specified card slot. |
| [unlockPuk](arkts-telephony-sim-unlockpuk-f-sys.md#unlockpuk) | Unlock the SIM card password in the specified card slot. |
| [unlockPuk](arkts-telephony-sim-unlockpuk-f-sys.md#unlockpuk-1) | Unlock the SIM card password in the specified card slot. |
| [unlockPuk2](arkts-telephony-sim-unlockpuk2-f-sys.md#unlockpuk2) | Unlock the SIM card password in the specified card slot. |
| [unlockPuk2](arkts-telephony-sim-unlockpuk2-f-sys.md#unlockpuk2-1) | Unlock the SIM card password in the specified card slot. |
| [unlockSimLock](arkts-telephony-sim-unlocksimlock-f-sys.md#unlocksimlock) | Unlock SIM card. |
| [unlockSimLock](arkts-telephony-sim-unlocksimlock-f-sys.md#unlocksimlock-1) | Unlock SIM card. |
| [updateIccDiallingNumbers](arkts-telephony-sim-updateiccdiallingnumbers-f-sys.md#updateiccdiallingnumbers) | Update dialing number information on SIM card. |
| [updateIccDiallingNumbers](arkts-telephony-sim-updateiccdiallingnumbers-f-sys.md#updateiccdiallingnumbers-1) | Update dialing number information on SIM card. |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i.md) | Defines the ICC account information. |
| [SimLabel](arkts-telephony-sim-simlabel-i.md) | 定义SIM卡标签信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DiallingNumbersInfo](arkts-telephony-sim-diallingnumbersinfo-i-sys.md) | Defines the contact number information. |
| [IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i-sys.md) | Defines the ICC account information. |
| [LockInfo](arkts-telephony-sim-lockinfo-i-sys.md) | Defines the personalized lock information. |
| [LockStatusResponse](arkts-telephony-sim-lockstatusresponse-i-sys.md) | Defines the personalized lock information. |
| [OperatorConfig](arkts-telephony-sim-operatorconfig-i-sys.md) | Defines the carrier configuration. |
| [PersoLockInfo](arkts-telephony-sim-persolockinfo-i-sys.md) | Defines the personalized lock information. |
| [SimAuthenticationResponse](arkts-telephony-sim-simauthenticationresponse-i-sys.md) | Defines the SIM card authentication response. |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CardType](arkts-telephony-sim-cardtype-e.md) | Indicates the SIM card types. |
| [SimState](arkts-telephony-sim-simstate-e.md) | Indicates the SIM card states. |
| [SimType](arkts-telephony-sim-simtype-e.md) | Indicates the SIM card type. |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
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

