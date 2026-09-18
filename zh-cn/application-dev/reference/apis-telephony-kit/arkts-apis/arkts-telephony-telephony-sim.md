# @ohos.telephony.sim(SIM卡管理)

SIM卡管理模块提供了SIM卡管理的基础能力，包括获取指定卡槽SIM卡的ISO国家码、归属PLMN号、服务提供商名称、SIM卡状态、卡类型、是否插卡、是否激活等。

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.CoreService

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getActiveSimAccountInfoList](arkts-telephony-sim-getactivesimaccountinfolist-f.md) | 获取激活SIM卡账户信息列表。使用callback异步回调。 |
| [getActiveSimAccountInfoList](arkts-telephony-sim-getactivesimaccountinfolist-f.md) | 获取激活SIM卡账户信息列表。使用Promise异步回调。 |
| [getCardType](arkts-telephony-sim-getcardtype-f.md) | 获取指定卡槽SIM卡的卡类型。使用callback异步回调。 |
| [getCardType](arkts-telephony-sim-getcardtype-f.md) | 获取指定卡槽SIM卡的卡类型。使用Promise异步回调。 |
| [getCardTypeSync](arkts-telephony-sim-getcardtypesync-f.md) | 获取指定卡槽SIM卡的卡类型。 |
| [getDefaultVoiceSimId](arkts-telephony-sim-getdefaultvoicesimid-f.md) | 获取默认语音业务的SIM卡ID。使用callback异步回调。 |
| [getDefaultVoiceSimId](arkts-telephony-sim-getdefaultvoicesimid-f.md) | 获取默认语音业务的SIM卡ID。使用Promise异步回调。 |
| [getDefaultVoiceSlotId](arkts-telephony-sim-getdefaultvoiceslotid-f.md) | 获取默认语音业务的卡槽ID。使用callback异步回调。 |
| [getDefaultVoiceSlotId](arkts-telephony-sim-getdefaultvoiceslotid-f.md) | 获取默认语音业务的卡槽ID。使用Promise异步回调。 |
| [getISOCountryCodeForSim](arkts-telephony-sim-getisocountrycodeforsim-f.md) | 获取指定卡槽SIM卡的ISO国家码。使用callback异步回调。 |
| [getISOCountryCodeForSim](arkts-telephony-sim-getisocountrycodeforsim-f.md) | 获取指定卡槽SIM卡的ISO国家码。使用Promise异步回调。 |
| [getISOCountryCodeForSimSync](arkts-telephony-sim-getisocountrycodeforsimsync-f.md) | 获取指定卡槽SIM卡的ISO国家码。 |
| [getMaxSimCount](arkts-telephony-sim-getmaxsimcount-f.md) | 获取卡槽数量。 |
| [getOpKey](arkts-telephony-sim-getopkey-f.md) | 获取指定卡槽中SIM卡的opkey。使用callback异步回调。 |
| [getOpKey](arkts-telephony-sim-getopkey-f.md) | 获取指定卡槽中SIM卡的opkey。使用Promise异步回调。 |
| [getOpKeySync](arkts-telephony-sim-getopkeysync-f.md) | 获取指定卡槽中SIM卡的opkey。 |
| [getOpName](arkts-telephony-sim-getopname-f.md) | 获取指定卡槽中SIM卡的OpName。使用callback异步回调。 |
| [getOpName](arkts-telephony-sim-getopname-f.md) | 获取指定卡槽中SIM卡的OpName。使用Promise异步回调。 |
| [getOpNameSync](arkts-telephony-sim-getopnamesync-f.md) | 获取指定卡槽中SIM卡的OpName。 |
| [getSimAccountInfo](arkts-telephony-sim-getsimaccountinfo-f.md) | 获取SIM卡账户信息。使用callback异步回调。 |
| [getSimAccountInfo](arkts-telephony-sim-getsimaccountinfo-f.md) | 获取SIM卡账户信息。使用Promise异步回调。 |
| [getSimLabel](arkts-telephony-sim-getsimlabel-f.md) | 查看卡槽ID和SIM卡的对应关系： |
| [getSimLabel](arkts-telephony-sim-getsimlabel-f.md) | 获取SIM卡的标签信息。使用Promise异步回调。 |
| [getSimLabelSync](arkts-telephony-sim-getsimlabelsync-f.md) | 通过传入SIM卡槽的ID，获取对应的SIM卡标签。 |
| [getSimOperatorNumeric](arkts-telephony-sim-getsimoperatornumeric-f.md) | 获取指定卡槽SIM卡的归属PLMN(Public Land Mobile Network)号。使用callback异步回调。 |
| [getSimOperatorNumeric](arkts-telephony-sim-getsimoperatornumeric-f.md) | 获取指定卡槽SIM卡的归属PLMN(Public Land Mobile Network)号。使用Promise异步回调。 |
| [getSimOperatorNumericSync](arkts-telephony-sim-getsimoperatornumericsync-f.md) | 获取指定卡槽SIM卡的归属PLMN(Public Land Mobile Network)号。 |
| [getSimSpn](arkts-telephony-sim-getsimspn-f.md) | 获取指定卡槽SIM卡的服务提供商名称(Service Provider Name，SPN)。使用callback异步回调。 |
| [getSimSpn](arkts-telephony-sim-getsimspn-f.md) | 获取指定卡槽SIM卡的服务提供商名称(Service Provider Name，SPN)。使用Promise异步回调。 |
| [getSimSpnSync](arkts-telephony-sim-getsimspnsync-f.md) | 获取指定卡槽SIM卡的服务提供商名称(Service Provider Name，SPN)。 |
| [getSimState](arkts-telephony-sim-getsimstate-f.md) | 获取指定卡槽的SIM卡状态。使用callback异步回调。 |
| [getSimState](arkts-telephony-sim-getsimstate-f.md) | 获取指定卡槽的SIM卡状态。使用Promise异步回调。 |
| [getSimStateSync](arkts-telephony-sim-getsimstatesync-f.md) | 获取指定卡槽的SIM卡状态。 |
| [hasOperatorPrivileges](arkts-telephony-sim-hasoperatorprivileges-f.md) | 检查应用(调用者)是否已被授予运营商权限。使用callback异步回调。 |
| [hasOperatorPrivileges](arkts-telephony-sim-hasoperatorprivileges-f.md) | 检查应用(调用者)是否已被授予运营商权限。使用Promise异步回调。 |
| [hasSimCard](arkts-telephony-sim-hassimcard-f.md) | 获取指定卡槽SIM卡是否插卡。使用callback异步回调。 |
| [hasSimCard](arkts-telephony-sim-hassimcard-f.md) | 获取指定卡槽SIM卡是否插卡。使用Promise异步回调。 |
| [hasSimCardSync](arkts-telephony-sim-hassimcardsync-f.md) | 获取指定卡槽SIM卡是否插卡。 |
| [isSimActive](arkts-telephony-sim-issimactive-f.md) | 获取指定卡槽SIM卡是否激活。使用callback异步回调。 |
| [isSimActive](arkts-telephony-sim-issimactive-f.md) | 获取指定卡槽SIM卡是否激活。使用Promise异步回调。 |
| [isSimActiveSync](arkts-telephony-sim-issimactivesync-f.md) | 获取指定卡槽SIM卡是否激活。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
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
| [getDsdsMode](arkts-telephony-sim-getdsdsmode-f-sys.md) |  |
| [getDsdsMode](arkts-telephony-sim-getdsdsmode-f-sys.md) |  |
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
| [setSimLabelIndex](arkts-telephony-sim-setsimlabelindex-f-sys.md) | 设置SIM卡标签索引。 |
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

### 接口

| 名称 | 说明 |
| --- | --- |
| [IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i.md) | Icc账户信息。 |
| [SimLabel](arkts-telephony-sim-simlabel-i.md) | SIM卡标签。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DiallingNumbersInfo](arkts-telephony-sim-diallingnumbersinfo-i-sys.md) |  |
| [IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i-sys.md) | Icc账户信息。 |
| [LockInfo](arkts-telephony-sim-lockinfo-i-sys.md) |  |
| [LockStatusResponse](arkts-telephony-sim-lockstatusresponse-i-sys.md) |  |
| [OperatorConfig](arkts-telephony-sim-operatorconfig-i-sys.md) |  |
| [PersoLockInfo](arkts-telephony-sim-persolockinfo-i-sys.md) |  |
| [SimAuthenticationResponse](arkts-telephony-sim-simauthenticationresponse-i-sys.md) |  |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CardType](arkts-telephony-sim-cardtype-e.md) | 卡类型。 |
| [SimState](arkts-telephony-sim-simstate-e.md) | SIM卡状态。 |
| [SimType](arkts-telephony-sim-simtype-e.md) | SIM卡类型的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthType](arkts-telephony-sim-authtype-e-sys.md) | Indicates the Authentication type |
| [ContactType](arkts-telephony-sim-contacttype-e-sys.md) | Indicates the contact types. |
| [DsdsMode](arkts-telephony-sim-dsdsmode-e-sys.md) | Indicates the Dsds Mode. |
| [LockState](arkts-telephony-sim-lockstate-e-sys.md) | Indicates the lock states. |
| [LockType](arkts-telephony-sim-locktype-e-sys.md) | Indicates the lock types. |
| [OperatorConfigKey](arkts-telephony-sim-operatorconfigkey-e-sys.md) |  |
| [OperatorSimCard](arkts-telephony-sim-operatorsimcard-e-sys.md) |  |
| [PersoLockType](arkts-telephony-sim-persolocktype-e-sys.md) | Indicates the personalized lock types. |
<!--DelEnd-->
