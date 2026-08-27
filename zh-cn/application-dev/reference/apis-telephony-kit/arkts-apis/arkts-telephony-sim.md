# @ohos.telephony.sim(SIM卡管理)

SIM卡管理模块提供了SIM卡管理的基础能力，包括获取指定卡槽SIM卡的ISO国家码、归属PLMN号、服务提供商名称、SIM卡状态、卡类型、是否插卡、是否激活等。

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.CoreService

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getActiveSimAccountInfoList(SIM卡管理)](arkts-telephony-sim-getactivesimaccountinfolist-f.md) | 获取激活SIM卡账户信息列表。使用callback异步回调。 |
| [getActiveSimAccountInfoList(SIM卡管理)](arkts-telephony-sim-getactivesimaccountinfolist-f.md) | 获取激活SIM卡账户信息列表。使用Promise异步回调。 |
| [getCardType(SIM卡管理)](arkts-telephony-sim-getcardtype-f.md) | 获取指定卡槽SIM卡的卡类型。使用callback异步回调。 |
| [getCardType(SIM卡管理)](arkts-telephony-sim-getcardtype-f.md) | 获取指定卡槽SIM卡的卡类型。使用Promise异步回调。 |
| [getCardTypeSync(SIM卡管理)](arkts-telephony-sim-getcardtypesync-f.md) | 获取指定卡槽SIM卡的卡类型。 |
| [getDefaultVoiceSimId(SIM卡管理)](arkts-telephony-sim-getdefaultvoicesimid-f.md) | 获取默认语音业务的SIM卡ID。使用callback异步回调。 |
| [getDefaultVoiceSimId(SIM卡管理)](arkts-telephony-sim-getdefaultvoicesimid-f.md) | 获取默认语音业务的SIM卡ID。使用Promise异步回调。 |
| [getDefaultVoiceSlotId(SIM卡管理)](arkts-telephony-sim-getdefaultvoiceslotid-f.md) | 获取默认语音业务的卡槽ID。使用callback异步回调。 |
| [getDefaultVoiceSlotId(SIM卡管理)](arkts-telephony-sim-getdefaultvoiceslotid-f.md) | 获取默认语音业务的卡槽ID。使用Promise异步回调。 |
| [getISOCountryCodeForSim(SIM卡管理)](arkts-telephony-sim-getisocountrycodeforsim-f.md) | 获取指定卡槽SIM卡的ISO国家码。使用callback异步回调。 |
| [getISOCountryCodeForSim(SIM卡管理)](arkts-telephony-sim-getisocountrycodeforsim-f.md) | 获取指定卡槽SIM卡的ISO国家码。使用Promise异步回调。 |
| [getISOCountryCodeForSimSync(SIM卡管理)](arkts-telephony-sim-getisocountrycodeforsimsync-f.md) | 获取指定卡槽SIM卡的ISO国家码。 |
| [getMaxSimCount(SIM卡管理)](arkts-telephony-sim-getmaxsimcount-f.md) | 获取卡槽数量。 |
| [getOpKey(SIM卡管理)](arkts-telephony-sim-getopkey-f.md) | 获取指定卡槽中SIM卡的opkey。使用callback异步回调。 |
| [getOpKey(SIM卡管理)](arkts-telephony-sim-getopkey-f.md) | 获取指定卡槽中SIM卡的opkey。使用Promise异步回调。 |
| [getOpKeySync(SIM卡管理)](arkts-telephony-sim-getopkeysync-f.md) | 获取指定卡槽中SIM卡的opkey。 |
| [getOpName(SIM卡管理)](arkts-telephony-sim-getopname-f.md) | 获取指定卡槽中SIM卡的OpName。使用callback异步回调。 |
| [getOpName(SIM卡管理)](arkts-telephony-sim-getopname-f.md) | 获取指定卡槽中SIM卡的OpName。使用Promise异步回调。 |
| [getOpNameSync(SIM卡管理)](arkts-telephony-sim-getopnamesync-f.md) | 获取指定卡槽中SIM卡的OpName。 |
| [getSimAccountInfo(SIM卡管理)](arkts-telephony-sim-getsimaccountinfo-f.md) | 获取SIM卡账户信息。使用callback异步回调。 |
| [getSimAccountInfo(SIM卡管理)](arkts-telephony-sim-getsimaccountinfo-f.md) | 获取SIM卡账户信息。使用Promise异步回调。 |
| [getSimLabel(SIM卡管理)](arkts-telephony-sim-getsimlabel-f.md) | 查看卡槽ID和SIM卡的对应关系：  - 卡槽1对应SIM卡1或SIM卡2  - 卡槽2对应SIM卡2或ESIMX |
| [getSimLabel(SIM卡管理)](arkts-telephony-sim-getsimlabel-f.md) | 获取SIM卡的标签信息。使用Promise异步回调。 |
| [getSimLabelSync(SIM卡管理)](arkts-telephony-sim-getsimlabelsync-f.md) | 通过传入SIM卡槽的ID，获取对应的SIM卡标签。 |
| [getSimOperatorNumeric(SIM卡管理)](arkts-telephony-sim-getsimoperatornumeric-f.md) | 获取指定卡槽SIM卡的归属PLMN(Public Land Mobile Network)号。使用callback异步回调。 |
| [getSimOperatorNumeric(SIM卡管理)](arkts-telephony-sim-getsimoperatornumeric-f.md) | 获取指定卡槽SIM卡的归属PLMN(Public Land Mobile Network)号。使用Promise异步回调。 |
| [getSimOperatorNumericSync(SIM卡管理)](arkts-telephony-sim-getsimoperatornumericsync-f.md) | 获取指定卡槽SIM卡的归属PLMN(Public Land Mobile Network)号。 |
| [getSimSpn(SIM卡管理)](arkts-telephony-sim-getsimspn-f.md) | 获取指定卡槽SIM卡的服务提供商名称(Service Provider Name，SPN)。使用callback异步回调。 |
| [getSimSpn(SIM卡管理)](arkts-telephony-sim-getsimspn-f.md) | 获取指定卡槽SIM卡的服务提供商名称(Service Provider Name，SPN)。使用Promise异步回调。 |
| [getSimSpnSync(SIM卡管理)](arkts-telephony-sim-getsimspnsync-f.md) | 获取指定卡槽SIM卡的服务提供商名称(Service Provider Name，SPN)。 |
| [getSimState(SIM卡管理)](arkts-telephony-sim-getsimstate-f.md) | 获取指定卡槽的SIM卡状态。使用callback异步回调。 |
| [getSimState(SIM卡管理)](arkts-telephony-sim-getsimstate-f.md) | 获取指定卡槽的SIM卡状态。使用Promise异步回调。 |
| [getSimStateSync(SIM卡管理)](arkts-telephony-sim-getsimstatesync-f.md) | 获取指定卡槽的SIM卡状态。 |
| [hasOperatorPrivileges(SIM卡管理)](arkts-telephony-sim-hasoperatorprivileges-f.md) | 检查应用(调用者)是否已被授予运营商权限。使用callback异步回调。 |
| [hasOperatorPrivileges(SIM卡管理)](arkts-telephony-sim-hasoperatorprivileges-f.md) | 检查应用(调用者)是否已被授予运营商权限。使用Promise异步回调。 |
| [hasSimCard(SIM卡管理)](arkts-telephony-sim-hassimcard-f.md) | 获取指定卡槽SIM卡是否插卡。使用callback异步回调。 |
| [hasSimCard(SIM卡管理)](arkts-telephony-sim-hassimcard-f.md) | 获取指定卡槽SIM卡是否插卡。使用Promise异步回调。 |
| [hasSimCardSync(SIM卡管理)](arkts-telephony-sim-hassimcardsync-f.md) | 获取指定卡槽SIM卡是否插卡。 |
| [isSimActive(SIM卡管理)](arkts-telephony-sim-issimactive-f.md) | 获取指定卡槽SIM卡是否激活。使用callback异步回调。 |
| [isSimActive(SIM卡管理)](arkts-telephony-sim-issimactive-f.md) | 获取指定卡槽SIM卡是否激活。使用Promise异步回调。 |
| [isSimActiveSync(SIM卡管理)](arkts-telephony-sim-issimactivesync-f.md) | 获取指定卡槽SIM卡是否激活。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [activateSim(SIM卡管理)](arkts-telephony-sim-activatesim-f-sys.md) | Activate the SIM card in the specified slot. |
| [activateSim(SIM卡管理)](arkts-telephony-sim-activatesim-f-sys.md) | Activate the SIM card in the specified slot. |
| [addIccDiallingNumbers(SIM卡管理)](arkts-telephony-sim-addiccdiallingnumbers-f-sys.md) | Add dialing number information to SIM card. |
| [addIccDiallingNumbers(SIM卡管理)](arkts-telephony-sim-addiccdiallingnumbers-f-sys.md) | Add dialing number information to SIM card. |
| [alterPin(SIM卡管理)](arkts-telephony-sim-alterpin-f-sys.md) | Change Pin Password. |
| [alterPin(SIM卡管理)](arkts-telephony-sim-alterpin-f-sys.md) | Change Pin Password. |
| [alterPin2(SIM卡管理)](arkts-telephony-sim-alterpin2-f-sys.md) | Change Pin2 password. |
| [alterPin2(SIM卡管理)](arkts-telephony-sim-alterpin2-f-sys.md) | Change Pin2 password. |
| [deactivateSim(SIM卡管理)](arkts-telephony-sim-deactivatesim-f-sys.md) | Disable SIM card in specified slot. |
| [deactivateSim(SIM卡管理)](arkts-telephony-sim-deactivatesim-f-sys.md) | Disable SIM card in specified slot. |
| [delIccDiallingNumbers(SIM卡管理)](arkts-telephony-sim-deliccdiallingnumbers-f-sys.md) | Delete dialing number information on SIM card. |
| [delIccDiallingNumbers(SIM卡管理)](arkts-telephony-sim-deliccdiallingnumbers-f-sys.md) | Delete dialing number information on SIM card. |
| [getAllSimAccountInfoList(SIM卡管理)](arkts-telephony-sim-getallsimaccountinfolist-f-sys.md) | Get the list of all SIM card account information. |
| [getAllSimAccountInfoList(SIM卡管理)](arkts-telephony-sim-getallsimaccountinfolist-f-sys.md) | Get the list of all SIM card account information. |
| [getDsdsMode(SIM卡管理)](arkts-telephony-sim-getdsdsmode-f-sys.md) |  |
| [getDsdsMode(SIM卡管理)](arkts-telephony-sim-getdsdsmode-f-sys.md) |  |
| [getIMSI(SIM卡管理)](arkts-telephony-sim-getimsi-f-sys.md) | Get the international mobile subscriber ID. |
| [getIMSI(SIM卡管理)](arkts-telephony-sim-getimsi-f-sys.md) | Get the international mobile subscriber ID. |
| [getLockState(SIM卡管理)](arkts-telephony-sim-getlockstate-f-sys.md) | Get the lock status of the SIM card in the specified slot. |
| [getLockState(SIM卡管理)](arkts-telephony-sim-getlockstate-f-sys.md) | Get the lock status of the SIM card in the specified slot. |
| [getOperatorConfigs(SIM卡管理)](arkts-telephony-sim-getoperatorconfigs-f-sys.md) | Obtains the operatorconfigs of the SIM card in a specified slot. |
| [getOperatorConfigs(SIM卡管理)](arkts-telephony-sim-getoperatorconfigs-f-sys.md) | Obtains the operatorconfigs of the SIM card in a specified slot. |
| [getShowName(SIM卡管理)](arkts-telephony-sim-getshowname-f-sys.md) | Gets the name of the SIM card in the specified slot. |
| [getShowName(SIM卡管理)](arkts-telephony-sim-getshowname-f-sys.md) | Gets the name of the SIM card in the specified slot. |
| [getShowNumber(SIM卡管理)](arkts-telephony-sim-getshownumber-f-sys.md) | Get the SIM card number of the specified card slot. |
| [getShowNumber(SIM卡管理)](arkts-telephony-sim-getshownumber-f-sys.md) | Get the SIM card number of the specified card slot. |
| [getSimAuthentication(SIM卡管理)](arkts-telephony-sim-getsimauthentication-f-sys.md) | Performs SIM card authentication. |
| [getSimGid1(SIM卡管理)](arkts-telephony-sim-getsimgid1-f-sys.md) | Obtains the Group Identifier Level 1 (GID1) of the SIM card in a specified slot. The GID1 is recorded in the EFGID1 file of the SIM card. |
| [getSimGid1(SIM卡管理)](arkts-telephony-sim-getsimgid1-f-sys.md) | Obtains the Group Identifier Level 1 (GID1) of the SIM card in a specified slot. The GID1 is recorded in the EFGID1 file of the SIM card. |
| [getSimIccId(SIM卡管理)](arkts-telephony-sim-getsimiccid-f-sys.md) | Obtains the ICCID of the SIM card in a specified slot. & lt;p & gt;The ICCID is a unique identifier of a SIM card. It consists of 20 digits and is recorded in the EFICCID file of the SIM card. |
| [getSimIccId(SIM卡管理)](arkts-telephony-sim-getsimiccid-f-sys.md) | Obtains the ICCID of the SIM card in a specified slot. & lt;p & gt;The ICCID is a unique identifier of a SIM card. It consists of 20 digits and is recorded in the EFICCID file of the SIM card. |
| [getSimTelephoneNumber(SIM卡管理)](arkts-telephony-sim-getsimtelephonenumber-f-sys.md) | Obtains the MSISDN of the SIM card in a specified slot. The MSISDN is recorded in the EFMSISDN file of the SIM card. |
| [getSimTelephoneNumber(SIM卡管理)](arkts-telephony-sim-getsimtelephonenumber-f-sys.md) | Obtains the MSISDN of the SIM card in a specified slot. The MSISDN is recorded in the EFMSISDN file of the SIM card. |
| [getVoiceMailIdentifier(SIM卡管理)](arkts-telephony-sim-getvoicemailidentifier-f-sys.md) | Obtains the alpha identifier of the voice mailbox of the SIM card in a specified slot. |
| [getVoiceMailIdentifier(SIM卡管理)](arkts-telephony-sim-getvoicemailidentifier-f-sys.md) | Obtains the alpha identifier of the voice mailbox of the SIM card in a specified slot. |
| [getVoiceMailNumber(SIM卡管理)](arkts-telephony-sim-getvoicemailnumber-f-sys.md) | Obtains the voice mailbox number of the SIM card in a specified slot. |
| [getVoiceMailNumber(SIM卡管理)](arkts-telephony-sim-getvoicemailnumber-f-sys.md) | Obtains the voice mailbox number of the SIM card in a specified slot. |
| [isOperatorSimCard(SIM卡管理)](arkts-telephony-sim-isoperatorsimcard-f-sys.md) | Indicates whether the SIM card in a specified slot is a specified operator. |
| [queryIccDiallingNumbers(SIM卡管理)](arkts-telephony-sim-queryiccdiallingnumbers-f-sys.md) | Query dialing number information on SIM card. |
| [queryIccDiallingNumbers(SIM卡管理)](arkts-telephony-sim-queryiccdiallingnumbers-f-sys.md) | Query dialing number information on SIM card. |
| [sendEnvelopeCmd(SIM卡管理)](arkts-telephony-sim-sendenvelopecmd-f-sys.md) | Send envelope command to SIM card. |
| [sendEnvelopeCmd(SIM卡管理)](arkts-telephony-sim-sendenvelopecmd-f-sys.md) | Send envelope command to SIM card. |
| [sendTerminalResponseCmd(SIM卡管理)](arkts-telephony-sim-sendterminalresponsecmd-f-sys.md) | Send terminal response command to SIM card. |
| [sendTerminalResponseCmd(SIM卡管理)](arkts-telephony-sim-sendterminalresponsecmd-f-sys.md) | Send terminal response command to SIM card. |
| [setDefaultVoiceSlotId(SIM卡管理)](arkts-telephony-sim-setdefaultvoiceslotid-f-sys.md) | Set the card slot ID of the default voice service. |
| [setDefaultVoiceSlotId(SIM卡管理)](arkts-telephony-sim-setdefaultvoiceslotid-f-sys.md) | Set the card slot ID of the default voice service. |
| [setLockState(SIM卡管理)](arkts-telephony-sim-setlockstate-f-sys.md) | Set the lock status of the SIM card in the specified slot. |
| [setLockState(SIM卡管理)](arkts-telephony-sim-setlockstate-f-sys.md) | Set the lock status of the SIM card in the specified slot. |
| [setShowName(SIM卡管理)](arkts-telephony-sim-setshowname-f-sys.md) | Set the SIM card display name of the specified card slot. |
| [setShowName(SIM卡管理)](arkts-telephony-sim-setshowname-f-sys.md) | Set the SIM card display name of the specified card slot. |
| [setShowNumber(SIM卡管理)](arkts-telephony-sim-setshownumber-f-sys.md) | Set the SIM card number in the specified slot. |
| [setShowNumber(SIM卡管理)](arkts-telephony-sim-setshownumber-f-sys.md) | Set the SIM card number in the specified slot. |
| [setSimLabelIndex(SIM卡管理)](arkts-telephony-sim-setsimlabelindex-f-sys.md) | 设置SIM卡标签索引。 |
| [setVoiceMailInfo(SIM卡管理)](arkts-telephony-sim-setvoicemailinfo-f-sys.md) | Sets the voice mail information. |
| [setVoiceMailInfo(SIM卡管理)](arkts-telephony-sim-setvoicemailinfo-f-sys.md) | Sets the voice mail information. |
| [unlockPin(SIM卡管理)](arkts-telephony-sim-unlockpin-f-sys.md) | Unlock the SIM card password of the specified card slot. |
| [unlockPin(SIM卡管理)](arkts-telephony-sim-unlockpin-f-sys.md) | Unlock the SIM card password of the specified card slot. |
| [unlockPin2(SIM卡管理)](arkts-telephony-sim-unlockpin2-f-sys.md) | Unlock the SIM card password of the specified card slot. |
| [unlockPin2(SIM卡管理)](arkts-telephony-sim-unlockpin2-f-sys.md) | Unlock the SIM card password of the specified card slot. |
| [unlockPuk(SIM卡管理)](arkts-telephony-sim-unlockpuk-f-sys.md) | Unlock the SIM card password in the specified card slot. |
| [unlockPuk(SIM卡管理)](arkts-telephony-sim-unlockpuk-f-sys.md) | Unlock the SIM card password in the specified card slot. |
| [unlockPuk2(SIM卡管理)](arkts-telephony-sim-unlockpuk2-f-sys.md) | Unlock the SIM card password in the specified card slot. |
| [unlockPuk2(SIM卡管理)](arkts-telephony-sim-unlockpuk2-f-sys.md) | Unlock the SIM card password in the specified card slot. |
| [unlockSimLock(SIM卡管理)](arkts-telephony-sim-unlocksimlock-f-sys.md) | Unlock SIM card. |
| [unlockSimLock(SIM卡管理)](arkts-telephony-sim-unlocksimlock-f-sys.md) | Unlock SIM card. |
| [updateIccDiallingNumbers(SIM卡管理)](arkts-telephony-sim-updateiccdiallingnumbers-f-sys.md) | Update dialing number information on SIM card. |
| [updateIccDiallingNumbers(SIM卡管理)](arkts-telephony-sim-updateiccdiallingnumbers-f-sys.md) | Update dialing number information on SIM card. |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [IccAccountInfo(SIM卡管理)](arkts-telephony-sim-iccaccountinfo-i.md) | Icc账户信息。 |
| [SimLabel(SIM卡管理)](arkts-telephony-sim-simlabel-i.md) | SIM卡标签。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DiallingNumbersInfo(SIM卡管理)](arkts-telephony-sim-diallingnumbersinfo-i-sys.md) |  |
| [IccAccountInfo(SIM卡管理)](arkts-telephony-sim-iccaccountinfo-i-sys.md) | Icc账户信息。 |
| [LockInfo(SIM卡管理)](arkts-telephony-sim-lockinfo-i-sys.md) |  |
| [LockStatusResponse(SIM卡管理)](arkts-telephony-sim-lockstatusresponse-i-sys.md) |  |
| [OperatorConfig(SIM卡管理)](arkts-telephony-sim-operatorconfig-i-sys.md) |  |
| [PersoLockInfo(SIM卡管理)](arkts-telephony-sim-persolockinfo-i-sys.md) |  |
| [SimAuthenticationResponse(SIM卡管理)](arkts-telephony-sim-simauthenticationresponse-i-sys.md) |  |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CardType(SIM卡管理)](arkts-telephony-sim-cardtype-e.md) | 卡类型。 |
| [SimState(SIM卡管理)](arkts-telephony-sim-simstate-e.md) | SIM卡状态。 |
| [SimType(SIM卡管理)](arkts-telephony-sim-simtype-e.md) | SIM卡类型的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthType(SIM卡管理)](arkts-telephony-sim-authtype-e-sys.md) | Indicates the Authentication type |
| [ContactType(SIM卡管理)](arkts-telephony-sim-contacttype-e-sys.md) | Indicates the contact types. |
| [DsdsMode(SIM卡管理)](arkts-telephony-sim-dsdsmode-e-sys.md) | Indicates the Dsds Mode. |
| [LockState(SIM卡管理)](arkts-telephony-sim-lockstate-e-sys.md) | Indicates the lock states. |
| [LockType(SIM卡管理)](arkts-telephony-sim-locktype-e-sys.md) | Indicates the lock types. |
| [OperatorConfigKey(SIM卡管理)](arkts-telephony-sim-operatorconfigkey-e-sys.md) |  |
| [OperatorSimCard(SIM卡管理)](arkts-telephony-sim-operatorsimcard-e-sys.md) |  |
| [PersoLockType(SIM卡管理)](arkts-telephony-sim-persolocktype-e-sys.md) | Indicates the personalized lock types. |
<!--DelEnd-->
