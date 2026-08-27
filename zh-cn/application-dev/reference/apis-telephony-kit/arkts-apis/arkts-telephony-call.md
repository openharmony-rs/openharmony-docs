# @ohos.telephony.call(拨打电话)

该模块提供呼叫管理功能，包括拨打电话、跳转到拨号界面、获取通话状态、格式化电话号码等。如需订阅通话状态请使用 `observer.on('callStateChange')` 。

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.CallManager

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [answerCall(拨打电话)](arkts-telephony-call-answercall-f.md) | 接听来电。使用callback异步回调。 |
| [dial(拨打电话)](arkts-telephony-call-dial-f.md) | 拨打电话，可设置通话参数。使用callback异步回调。 |
| [dial(拨打电话)](arkts-telephony-call-dial-f.md) | 拨打电话，可设置通话参数。使用Promise异步回调。 |
| [dial(拨打电话)](arkts-telephony-call-dial-f.md) | 拨打电话。使用callback异步回调。 |
| [formatPhoneNumber(拨打电话)](arkts-telephony-call-formatphonenumber-f.md) | 格式化电话号码，可设置格式化参数。使用callback异步回调。电话号码格式化后为标准数字字符串，例如：“138 xxxx xxxx”、“0755 xxxx xxxx”。 |
| [formatPhoneNumber(拨打电话)](arkts-telephony-call-formatphonenumber-f.md) | 格式化电话号码，可设置格式化参数。使用Promise异步回调。电话号码格式化后为标准数字字符串，例如：“138 xxxx xxxx”、“0755 xxxx xxxx”。 |
| [formatPhoneNumber(拨打电话)](arkts-telephony-call-formatphonenumber-f.md) | 格式化电话号码。使用callback异步回调。电话号码格式化后为标准数字字符串，例如：“138 xxxx xxxx”、“0755 xxxx xxxx”。 |
| [formatPhoneNumberToE164(拨打电话)](arkts-telephony-call-formatphonenumbertoe164-f.md) | 将电话号码格式化为E.164表示形式，使用callback异步回调。待格式化的电话号码需要与传入的国家码相匹配，如中国电话号码需要传入国家码CN，否则格式化后的电话号码为null。 |
| [formatPhoneNumberToE164(拨打电话)](arkts-telephony-call-formatphonenumbertoe164-f.md) | 将电话号码格式化为E.164表示形式，使用Promise异步回调。待格式化的电话号码需要与传入的国家码相匹配，如中国电话号码需要传入国家码CN，否则格式化后的电话号码为null。支持所有国家码。 |
| [getCallState(拨打电话)](arkts-telephony-call-getcallstate-f.md) | 获取当前通话状态。使用callback异步回调。 |
| [getCallState(拨打电话)](arkts-telephony-call-getcallstate-f.md) | 获取当前通话状态。使用Promise异步回调。 |
| [getCallStateSync(拨打电话)](arkts-telephony-call-getcallstatesync-f.md) | 获取当前通话状态。 |
| [getCallTransferInfo(拨打电话)](arkts-telephony-call-getcalltransferinfo-f.md) | 获取电话号码的呼叫转移状态。使用Promise异步回调。 |
| [hangUpCall(拨打电话)](arkts-telephony-call-hangupcall-f.md) | 挂断电话。使用callback异步回调。 |
| [hasCall(拨打电话)](arkts-telephony-call-hascall-f.md) | 判断是否存在通话。使用callback异步回调。 |
| [hasCall(拨打电话)](arkts-telephony-call-hascall-f.md) | 判断是否存在通话。使用Promise异步回调。 |
| [hasCallSync(拨打电话)](arkts-telephony-call-hascallsync-f.md) | 判断是否存在通话。 |
| [hasVoiceCapability(拨打电话)](arkts-telephony-call-hasvoicecapability-f.md) | 检查当前设备是否具备语音通话能力。 |
| [isEmergencyPhoneNumber(拨打电话)](arkts-telephony-call-isemergencyphonenumber-f.md) | 根据电话号码参数，判断是否是紧急电话号码。使用callback异步回调。 |
| [isEmergencyPhoneNumber(拨打电话)](arkts-telephony-call-isemergencyphonenumber-f.md) | 根据电话号码参数，判断是否是紧急电话号码。使用Promise异步回调。 |
| [isEmergencyPhoneNumber(拨打电话)](arkts-telephony-call-isemergencyphonenumber-f.md) | 判断是否是紧急电话号码。使用callback异步回调。 |
| [makeCall(拨打电话)](arkts-telephony-call-makecall-f.md) | 跳转到拨号界面，并显示待拨出的号码。使用callback异步回调。只支持在UIAbility中调用。 |
| [makeCall(拨打电话)](arkts-telephony-call-makecall-f.md) | 跳转到拨号界面，并显示待拨出的号码。使用Promise异步回调。只支持在UIAbility中调用。 |
| [makeCall(拨打电话)](arkts-telephony-call-makecall-f.md) | 跳转到拨号界面，并显示待拨出的号码。使用Promise异步回调。只支持在UIAbility中调用。 |
| [makeCall(拨打电话)](arkts-telephony-call-makecall-f.md) | 跳转到拨号界面，并显示待拨出的号码。使用Promise异步回调。后台调用需要申请ohos.permission.START_ABILITIES_FROM_BACKGROUND权限。 |
| [makeCallWithToken(拨打电话)](arkts-telephony-call-makecallwithtoken-f.md) | 跳转到拨号界面，并显示待拨出的号码。使用Promise异步回调。 |
| [rejectCall(拨打电话)](arkts-telephony-call-rejectcall-f.md) | 拒绝来电。使用callback异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [answerCall(拨打电话)](arkts-telephony-call-answercall-f-sys.md) | 接听来电。使用callback异步回调。 |
| [answerCall(拨打电话)](arkts-telephony-call-answercall-f-sys.md) | 接听来电。使用Promise异步回调。 |
| [answerCall(拨打电话)](arkts-telephony-call-answercall-f-sys.md) | 接听来电。使用Promise异步回调。 |
| [answerCall(拨打电话)](arkts-telephony-call-answercall-f-sys.md) | 接听rtt来电 |
| [cancelCallUpgrade(拨打电话)](arkts-telephony-call-cancelcallupgrade-f-sys.md) | 视频通话升级过程中取消升级。使用Promise异步回调。 |
| [cancelMuted(拨打电话)](arkts-telephony-call-cancelmuted-f-sys.md) | 取消通话中的静音。使用callback异步回调。 |
| [cancelMuted(拨打电话)](arkts-telephony-call-cancelmuted-f-sys.md) | 取消通话中的静音。使用Promise异步回调。 |
| [canSetCallTransferTime(拨打电话)](arkts-telephony-call-cansetcalltransfertime-f-sys.md) | 检查是否可以设置呼叫转移时间。使用callback异步回调。 |
| [canSetCallTransferTime(拨打电话)](arkts-telephony-call-cansetcalltransfertime-f-sys.md) | 检查是否可以设置呼叫转移时间。使用Promise异步回调。 |
| [closeUnfinishedUssd(拨打电话)](arkts-telephony-call-closeunfinishedussd-f-sys.md) | 取消未激活完成的非结构化补充数据业务。使用callback异步回调。 |
| [closeUnfinishedUssd(拨打电话)](arkts-telephony-call-closeunfinishedussd-f-sys.md) | 取消未激活完成的非结构化补充数据业务。使用Promise异步回调。 |
| [combineConference(拨打电话)](arkts-telephony-call-combineconference-f-sys.md) | 合并通话，将两通电话合并成会议电话。使用callback异步回调。 |
| [combineConference(拨打电话)](arkts-telephony-call-combineconference-f-sys.md) | 合并通话，将两通电话合并成会议电话。使用Promise异步回调。 |
| [controlCamera(拨打电话)](arkts-telephony-call-controlcamera-f-sys.md) | 设置使用指定的相机进行视频通话，cameraId为空表示关闭相机。使用Promise异步回调。 |
| [dialCall(拨打电话)](arkts-telephony-call-dialcall-f-sys.md) | 拨打电话，可设置通话参数。使用callback异步回调。 |
| [dialCall(拨打电话)](arkts-telephony-call-dialcall-f-sys.md) | 拨打电话，可设置通话参数。使用Promise异步回调。 |
| [dialCall(拨打电话)](arkts-telephony-call-dialcall-f-sys.md) | 拨打电话。使用callback异步回调。 |
| [disableImsSwitch(拨打电话)](arkts-telephony-call-disableimsswitch-f-sys.md) | 禁用Ims开关。使用callback异步回调。 |
| [disableImsSwitch(拨打电话)](arkts-telephony-call-disableimsswitch-f-sys.md) | 禁用Ims开关。使用Promise异步回调。 |
| [enableImsSwitch(拨打电话)](arkts-telephony-call-enableimsswitch-f-sys.md) | 启用Ims开关。使用callback异步回调。 |
| [enableImsSwitch(拨打电话)](arkts-telephony-call-enableimsswitch-f-sys.md) | 启用Ims开关。使用Promise异步回调。 |
| [getCallIdListForConference(拨打电话)](arkts-telephony-call-getcallidlistforconference-f-sys.md) | 获取会议的呼叫Id列表。使用callback异步回调。 |
| [getCallIdListForConference(拨打电话)](arkts-telephony-call-getcallidlistforconference-f-sys.md) | 获取会议的呼叫Id列表。使用Promise异步回调。 |
| [getCallRestrictionStatus(拨打电话)](arkts-telephony-call-getcallrestrictionstatus-f-sys.md) | 获取呼叫限制状态。使用callback异步回调。 |
| [getCallRestrictionStatus(拨打电话)](arkts-telephony-call-getcallrestrictionstatus-f-sys.md) | 获取呼叫限制状态。使用Promise异步回调。 |
| [getCallTransferInfo(拨打电话)](arkts-telephony-call-getcalltransferinfo-f-sys.md) | 获取呼叫转移信息。使用callback异步回调。 |
| [getCallTransferInfo(拨打电话)](arkts-telephony-call-getcalltransferinfo-f-sys.md) | 获取呼叫转移信息。使用Promise异步回调。 |
| [getCallWaitingStatus(拨打电话)](arkts-telephony-call-getcallwaitingstatus-f-sys.md) | 获取呼叫等待状态。使用callback异步回调。 |
| [getCallWaitingStatus(拨打电话)](arkts-telephony-call-getcallwaitingstatus-f-sys.md) | 获取呼叫等待状态。使用Promise异步回调。 |
| [getMainCallId(拨打电话)](arkts-telephony-call-getmaincallid-f-sys.md) | 获取主呼叫Id。使用callback异步回调。 |
| [getMainCallId(拨打电话)](arkts-telephony-call-getmaincallid-f-sys.md) | 获取主呼叫Id。使用Promise异步回调。 |
| [getSubCallIdList(拨打电话)](arkts-telephony-call-getsubcallidlist-f-sys.md) | 获取子呼叫Id列表。使用callback异步回调。 |
| [getSubCallIdList(拨打电话)](arkts-telephony-call-getsubcallidlist-f-sys.md) | 获取子呼叫Id列表。使用Promise异步回调。 |
| [getVoNRState(拨打电话)](arkts-telephony-call-getvonrstate-f-sys.md) | 查询NR语音的开关状态。使用callback异步回调。 |
| [getVoNRState(拨打电话)](arkts-telephony-call-getvonrstate-f-sys.md) | 查询NR语音的开关状态。使用Promise异步回调。 |
| [hangUpCall(拨打电话)](arkts-telephony-call-hangupcall-f-sys.md) | 挂断电话。使用callback异步回调。 |
| [hangUpCall(拨打电话)](arkts-telephony-call-hangupcall-f-sys.md) | 挂断电话。使用Promise异步回调。 |
| [holdCall(拨打电话)](arkts-telephony-call-holdcall-f-sys.md) | 保持通话。使用callback异步回调。 |
| [holdCall(拨打电话)](arkts-telephony-call-holdcall-f-sys.md) | 保持通话。使用Promise异步回调。 |
| [inputDialerSpecialCode(拨打电话)](arkts-telephony-call-inputdialerspecialcode-f-sys.md) | 暗码广播。使用callback异步回调。 |
| [inputDialerSpecialCode(拨打电话)](arkts-telephony-call-inputdialerspecialcode-f-sys.md) | 暗码广播。使用Promise异步回调。 |
| [isImsSwitchEnabled(拨打电话)](arkts-telephony-call-isimsswitchenabled-f-sys.md) | 判断Ims开关是否启用。使用callback异步回调。 |
| [isImsSwitchEnabled(拨打电话)](arkts-telephony-call-isimsswitchenabled-f-sys.md) | 判断Ims开关是否启用。使用Promise异步回调。 |
| [isImsSwitchEnabledSync(拨打电话)](arkts-telephony-call-isimsswitchenabledsync-f-sys.md) | 判断Ims开关是否启用。调用此API返回结果。 |
| [isInEmergencyCall(拨打电话)](arkts-telephony-call-isinemergencycall-f-sys.md) | 判断是否正在处于紧急呼叫。使用callback异步回调。 |
| [isInEmergencyCall(拨打电话)](arkts-telephony-call-isinemergencycall-f-sys.md) | 判断是否正在处于紧急呼叫。使用Promise异步回调。 |
| [isNewCallAllowed(拨打电话)](arkts-telephony-call-isnewcallallowed-f-sys.md) | 判断是否允许再拨打一通新电话。使用callback异步回调。 |
| [isNewCallAllowed(拨打电话)](arkts-telephony-call-isnewcallallowed-f-sys.md) | 判断是否允许再拨打一通新电话。使用Promise异步回调。 |
| [isRinging(拨打电话)](arkts-telephony-call-isringing-f-sys.md) | 判断是否正在响铃。使用callback异步回调。 |
| [isRinging(拨打电话)](arkts-telephony-call-isringing-f-sys.md) | 判断是否正在响铃。使用Promise异步回调。 |
| [joinConference(拨打电话)](arkts-telephony-call-joinconference-f-sys.md) | 加入会议。使用callback异步回调。 |
| [joinConference(拨打电话)](arkts-telephony-call-joinconference-f-sys.md) | 加入会议。使用Promise异步回调。 |
| [kickOutFromConference(拨打电话)](arkts-telephony-call-kickoutfromconference-f-sys.md) | 移出电话会议，将指定通话从会议电话中挂断。使用callback异步回调。 |
| [kickOutFromConference(拨打电话)](arkts-telephony-call-kickoutfromconference-f-sys.md) | 移出电话会议，将指定通话从会议电话中挂断。使用Promise异步回调。 |
| [muteRinger(拨打电话)](arkts-telephony-call-muteringer-f-sys.md) | 如果来电铃声响起，设备将停止铃声。否则，此方法不起作用。使用callback异步回调。 |
| [muteRinger(拨打电话)](arkts-telephony-call-muteringer-f-sys.md) | 如果来电铃声响起，设备将停止铃声。否则，此方法不起作用。使用Promise异步回调。 |
| off(拨打电话) | 取消订阅callDetailsChange事件。使用callback异步回调。 |
| off(拨打电话) | 取消订阅callEventChange事件。使用callback异步回调。 |
| off(拨打电话) | 取消订阅callDisconnectedCause事件。使用callback异步回调。 |
| [off(拨打电话)](arkts-telephony-call-mmicoderesult-e-sys.md) | 取消订阅mmiCodeResult事件。使用callback异步回调。 |
| off(拨打电话) | 取消订阅audioDeviceChange事件。使用callback异步回调。 |
| off(拨打电话) | 取消订阅拨号后延迟事件。使用callback异步回调。 |
| off(拨打电话) | 取消订阅imsCallModeChange事件。使用callback异步回调。 |
| [off(拨打电话)](arkts-telephony-call-callsessionevent-i-sys.md) | 取消订阅callSessionEvent事件。使用callback异步回调。 |
| off(拨打电话) | 取消订阅peerDimensionsChange事件。使用callback异步回调。 |
| off(拨打电话) | 取消订阅cameraCapabilitiesChange事件。使用callback异步回调。 |
| [offReceiveRttMessage(拨打电话)](arkts-telephony-call-offreceiverttmessage-f-sys.md) | 去订阅rtt消息事件 |
| [offRttErrCause(拨打电话)](arkts-telephony-call-offrtterrcause-f-sys.md) | 去订阅rtt通话错误事件 |
| [offRttModifyInd(拨打电话)](arkts-telephony-call-offrttmodifyind-f-sys.md) | 去订阅rtt通话变化事件 |
| on(拨打电话) | 订阅callDetailsChange事件。使用callback异步回调。 |
| on(拨打电话) | 订阅callEventChange事件。使用callback异步回调。 |
| on(拨打电话) | 订阅callDisconnectedCause事件。使用callback异步回调。 |
| [on(拨打电话)](arkts-telephony-call-mmicoderesult-e-sys.md) | 订阅mmiCodeResult事件。使用callback异步回调。 |
| on(拨打电话) | 订阅通话音频设备切换事件。使用callback异步回调。 |
| on(拨打电话) | 订阅拨号后延迟事件。使用callback异步回调。 |
| on(拨打电话) | 订阅imsCallModeChange事件。使用callback异步回调。 |
| [on(拨打电话)](arkts-telephony-call-callsessionevent-i-sys.md) | 订阅callSessionEvent事件。使用callback异步回调。 |
| on(拨打电话) | 订阅peerDimensionsChange事件。使用callback异步回调。 |
| on(拨打电话) | 订阅cameraCapabilitiesChange事件。使用callback异步回调。 |
| [onReceiveRttMessage(拨打电话)](arkts-telephony-call-onreceiverttmessage-f-sys.md) | 订阅RTT消息事件 |
| [onRttErrCause(拨打电话)](arkts-telephony-call-onrtterrcause-f-sys.md) | 订阅rtt通话错误事件 |
| [onRttModifyInd(拨打电话)](arkts-telephony-call-onrttmodifyind-f-sys.md) | 订阅rtt通话变化 |
| [postDialProceed(拨打电话)](arkts-telephony-call-postdialproceed-f-sys.md) | 继续进行通话。使用callback异步回调。当用户呼叫号码为：“普通电话号码”+“;”+"DTMF字符"(例如：“400xxxxxxx;123”)，并且已经订阅了通话后延迟事件，电话接通后，系统将上报通话后延迟事件，应用可以调用此接口选择是否发送DTMF音。 |
| [postDialProceed(拨打电话)](arkts-telephony-call-postdialproceed-f-sys.md) | 继续进行通话。使用Promise异步回调。当用户呼叫号码为：“普通电话号码”+“;”+"DTMF字符"(例如：“400xxxxxxx;123”)，并且已经订阅了通话后延迟事件，电话接通后，系统将上报通话后延迟事件，应用可以调用此接口选择是否发送DTMF音。 |
| [preloadCallUI(拨打电话)](arkts-telephony-call-preloadcallui-f-sys.md) | 预加载通话应用 |
| [rejectCall(拨打电话)](arkts-telephony-call-rejectcall-f-sys.md) | 拒绝来电。使用callback异步回调。 |
| [rejectCall(拨打电话)](arkts-telephony-call-rejectcall-f-sys.md) | 拒绝来电。使用Promise异步回调。 |
| [rejectCall(拨打电话)](arkts-telephony-call-rejectcall-f-sys.md) | 拒绝来电。使用callback异步回调。 |
| [rejectCall(拨打电话)](arkts-telephony-call-rejectcall-f-sys.md) | 拒绝来电。使用callback异步回调。 |
| [removeMissedIncomingCallNotification(拨打电话)](arkts-telephony-call-removemissedincomingcallnotification-f-sys.md) | 删除未接来电通知。使用callback异步回调。 |
| [removeMissedIncomingCallNotification(拨打电话)](arkts-telephony-call-removemissedincomingcallnotification-f-sys.md) | 删除未接来电通知。使用Promise异步回调。 |
| [sendCallUiEvent(拨打电话)](arkts-telephony-call-sendcalluievent-f-sys.md) | 发布通话界面事件。使用Promise异步回调。 |
| [sendRttMessage(拨打电话)](arkts-telephony-call-sendrttmessage-f-sys.md) | 发送rtt消息 |
| [sendUssdResponse(拨打电话)](arkts-telephony-call-sendussdresponse-f-sys.md) | 用于向运营商发送USSD业务（Unstructured Supplementary Service Data，非结构化补充数据业务）的响应消息。 |
| [separateConference(拨打电话)](arkts-telephony-call-separateconference-f-sys.md) | 分离会议电话。使用callback异步回调。 |
| [separateConference(拨打电话)](arkts-telephony-call-separateconference-f-sys.md) | 分离会议电话。使用Promise异步回调。 |
| [setAudioDevice(拨打电话)](arkts-telephony-call-setaudiodevice-f-sys.md) | 设置通话音频设备。使用callback异步回调。 |
| [setAudioDevice(拨打电话)](arkts-telephony-call-setaudiodevice-f-sys.md) | 设置通话音频设备。使用Promise异步回调。 |
| [setCallRestriction(拨打电话)](arkts-telephony-call-setcallrestriction-f-sys.md) | 设置呼叫限制状态。使用callback异步回调。 |
| [setCallRestriction(拨打电话)](arkts-telephony-call-setcallrestriction-f-sys.md) | 设置呼叫限制状态。使用Promise异步回调。 |
| [setCallRestrictionPassword(拨打电话)](arkts-telephony-call-setcallrestrictionpassword-f-sys.md) | 修改呼叫限制密码。使用callback异步回调。 |
| [setCallRestrictionPassword(拨打电话)](arkts-telephony-call-setcallrestrictionpassword-f-sys.md) | 修改呼叫限制密码。使用Promise异步回调。 |
| [setCallTransfer(拨打电话)](arkts-telephony-call-setcalltransfer-f-sys.md) | 设置呼叫转移信息。使用callback异步回调。 |
| [setCallTransfer(拨打电话)](arkts-telephony-call-setcalltransfer-f-sys.md) | 设置呼叫转移信息。使用Promise异步回调。 |
| [setCallWaiting(拨打电话)](arkts-telephony-call-setcallwaiting-f-sys.md) | 设置呼叫等待。使用callback异步回调。 |
| [setCallWaiting(拨打电话)](arkts-telephony-call-setcallwaiting-f-sys.md) | 设置呼叫等待。使用Promise异步回调。 |
| [setDeviceDirection(拨打电话)](arkts-telephony-call-setdevicedirection-f-sys.md) | 设置视频通话画面显示方向为设备方向。使用Promise异步回调。 |
| [setDisplaySurface(拨打电话)](arkts-telephony-call-setdisplaysurface-f-sys.md) | 设置远端画面窗口。使用Promise异步回调。 |
| [setMuted(拨打电话)](arkts-telephony-call-setmuted-f-sys.md) | 设置通话中的静音。使用callback异步回调。 |
| [setMuted(拨打电话)](arkts-telephony-call-setmuted-f-sys.md) | 设置通话中的静音。使用Promise异步回调。 |
| [setPreviewSurface(拨打电话)](arkts-telephony-call-setpreviewsurface-f-sys.md) | 设置本端预览画面窗口。使用Promise异步回调。 |
| [setRttCapability(拨打电话)](arkts-telephony-call-setrttcapability-f-sys.md) | 设置rtt功能 |
| [setVoNRState(拨打电话)](arkts-telephony-call-setvonrstate-f-sys.md) | 设置NR语音的开关状态。使用callback异步回调。 |
| [setVoNRState(拨打电话)](arkts-telephony-call-setvonrstate-f-sys.md) | 设置NR语音的开关状态。使用Promise异步回调。 |
| [startDTMF(拨打电话)](arkts-telephony-call-startdtmf-f-sys.md) | 启动双音多频。使用callback异步回调。 |
| [startDTMF(拨打电话)](arkts-telephony-call-startdtmf-f-sys.md) | 启动双音多频。使用Promise异步回调。 |
| [startRtt(拨打电话)](arkts-telephony-call-startrtt-f-sys.md) | 启动rtt |
| [stopDTMF(拨打电话)](arkts-telephony-call-stopdtmf-f-sys.md) | 停止双音多频。使用callback异步回调。 |
| [stopDTMF(拨打电话)](arkts-telephony-call-stopdtmf-f-sys.md) | 停止双音多频。使用Promise异步回调。 |
| [stopRtt(拨打电话)](arkts-telephony-call-stoprtt-f-sys.md) | 停止rtt |
| [switchCall(拨打电话)](arkts-telephony-call-switchcall-f-sys.md) | 切换呼叫。使用callback异步回调。 |
| [switchCall(拨打电话)](arkts-telephony-call-switchcall-f-sys.md) | 切换呼叫。使用Promise异步回调。 |
| [unHoldCall(拨打电话)](arkts-telephony-call-unholdcall-f-sys.md) | 取消保持通话。使用callback异步回调。 |
| [unHoldCall(拨打电话)](arkts-telephony-call-unholdcall-f-sys.md) | 取消保持通话。使用Promise异步回调。 |
| [unloadCallUI(拨打电话)](arkts-telephony-call-unloadcallui-f-sys.md) | 卸载通话应用 |
| [updateImsCallMode(拨打电话)](arkts-telephony-call-updateimscallmode-f-sys.md) | 更新Ims呼叫模式。使用callback异步回调。 |
| [updateImsCallMode(拨打电话)](arkts-telephony-call-updateimscallmode-f-sys.md) | 更新Ims呼叫模式。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CallTransferResult(拨打电话)](arkts-telephony-call-calltransferresult-i.md) | 呼叫转移结果。 |
| [DialOptions(拨打电话)](arkts-telephony-call-dialoptions-i.md) | 拨打电话的可选参数。 |
| [EmergencyNumberOptions(拨打电话)](arkts-telephony-call-emergencynumberoptions-i.md) | 判断是否是紧急电话号码的可选参数。 |
| [MakeCallOptions(拨打电话)](arkts-telephony-call-makecalloptions-i.md) | 拨打电话的可选参数。 |
| [NumberFormatOptions(拨打电话)](arkts-telephony-call-numberformatoptions-i.md) | 格式化号码的可选参数。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AudioDevice(拨打电话)](arkts-telephony-call-audiodevice-i-sys.md) | 音频设备。 |
| [AudioDeviceCallbackInfo(拨打电话)](arkts-telephony-call-audiodevicecallbackinfo-i-sys.md) | 音频设备信息。 |
| [CallAttributeOptions(拨打电话)](arkts-telephony-call-callattributeoptions-i-sys.md) | 调用属性选项。 |
| [CallEventOptions(拨打电话)](arkts-telephony-call-calleventoptions-i-sys.md) | 呼叫事件的可选参数。 |
| [CallRestrictionInfo(拨打电话)](arkts-telephony-call-callrestrictioninfo-i-sys.md) | 呼叫限制信息。 |
| [CallSessionEvent(拨打电话)](arkts-telephony-call-callsessionevent-i-sys.md) | 视频通话事件信息。 |
| [CallTransferInfo(拨打电话)](arkts-telephony-call-calltransferinfo-i-sys.md) | 呼叫转移信息。 |
| [CallTransferResult(拨打电话)](arkts-telephony-call-calltransferresult-i-sys.md) | 呼叫转移结果。 |
| [CameraCapabilities(拨打电话)](arkts-telephony-call-cameracapabilities-i-sys.md) | 视频通话本端相机画面分辨率信息。 |
| [DialCallOptions(拨打电话)](arkts-telephony-call-dialcalloptions-i-sys.md) | 拨打电话的可选参数。 |
| [DialOptions(拨打电话)](arkts-telephony-call-dialoptions-i-sys.md) | 拨打电话的可选参数。 |
| [DisconnectedDetails(拨打电话)](arkts-telephony-call-disconnecteddetails-i-sys.md) | 通话结束原因。 |
| [ImsCallModeInfo(拨打电话)](arkts-telephony-call-imscallmodeinfo-i-sys.md) | 视频通话模式信息。 |
| [MmiCodeResults(拨打电话)](arkts-telephony-call-mmicoderesults-i-sys.md) | MMI码结果。 |
| [NumberMarkInfo(拨打电话)](arkts-telephony-call-numbermarkinfo-i-sys.md) | 电话号码的标记信息。 |
| [PeerDimensionsDetail(拨打电话)](arkts-telephony-call-peerdimensionsdetail-i-sys.md) | 视频通话对端画面分辨率信息。 |
| [RejectMessageOptions(拨打电话)](arkts-telephony-call-rejectmessageoptions-i-sys.md) | 拒绝消息可选参数。 |
| [RttErrorInfo(拨打电话)](arkts-telephony-call-rtterrorinfo-i-sys.md) | rtt通话错误报告 |
| [RttEventInfo(拨打电话)](arkts-telephony-call-rtteventinfo-i-sys.md) | rtt通话事件 |
| [RttMessageInfo(拨打电话)](arkts-telephony-call-rttmessageinfo-i-sys.md) | rtt通话消息 |
| [VoipCallAttribute(拨打电话)](arkts-telephony-call-voipcallattribute-i-sys.md) | VoIP通话信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CallState(拨打电话)](arkts-telephony-call-callstate-e.md) | 通话状态码。 |
| [CallTransferType(拨打电话)](arkts-telephony-call-calltransfertype-e.md) | 呼叫转移类型。 |
| [CCallState(拨打电话)](arkts-telephony-call-ccallstate-e.md) | 运营商通话状态码。 |
| [TelCallState(拨打电话)](arkts-telephony-call-telcallstate-e.md) | 通话状态码。 |
| [TransferStatus(拨打电话)](arkts-telephony-call-transferstatus-e.md) | 转移状态。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AudioDeviceType(拨打电话)](arkts-telephony-call-audiodevicetype-e-sys.md) | 音频设备类型。 |
| [CallAbilityEventId(拨打电话)](arkts-telephony-call-callabilityeventid-e-sys.md) | 呼叫能力事件Id。 |
| [CallRestrictionMode(拨打电话)](arkts-telephony-call-callrestrictionmode-e-sys.md) | 呼叫限制模式。 |
| [CallRestrictionType(拨打电话)](arkts-telephony-call-callrestrictiontype-e-sys.md) | 呼叫限制类型。 |
| [CallSessionEventId(拨打电话)](arkts-telephony-call-callsessioneventid-e-sys.md) | 视频通话事件类型。 |
| [CallTransferSettingType(拨打电话)](arkts-telephony-call-calltransfersettingtype-e-sys.md) | 设置呼叫转移类型。 |
| [CallType(拨打电话)](arkts-telephony-call-calltype-e-sys.md) | 通话类型。 |
| [CallWaitingStatus(拨打电话)](arkts-telephony-call-callwaitingstatus-e-sys.md) | 呼叫等待状态。 |
| [ConferenceState(拨打电话)](arkts-telephony-call-conferencestate-e-sys.md) | 会议状态。 |
| [DetailedCallState(拨打电话)](arkts-telephony-call-detailedcallstate-e-sys.md) | 详细的呼叫状态。 |
| [DeviceDirection(拨打电话)](arkts-telephony-call-devicedirection-e-sys.md) | 视频通话画面方向类型。 |
| [DialScene(拨打电话)](arkts-telephony-call-dialscene-e-sys.md) | 拨号场景。 |
| [DialType(拨打电话)](arkts-telephony-call-dialtype-e-sys.md) | 拨号类型。 |
| [DisconnectedReason(拨打电话)](arkts-telephony-call-disconnectedreason-e-sys.md) | 断开连接的详细信息。 |
| [ImsCallMode(拨打电话)](arkts-telephony-call-imscallmode-e-sys.md) | IP多媒体系统调用模式。 |
| [ImsRttMode(拨打电话)](arkts-telephony-call-imsrttmode-e-sys.md) | rtt通话模式 |
| [MarkType(拨打电话)](arkts-telephony-call-marktype-e-sys.md) | 号码标记的类型。 |
| [MmiCodeResult(拨打电话)](arkts-telephony-call-mmicoderesult-e-sys.md) | MMI码结果。 |
| [RestrictionStatus(拨打电话)](arkts-telephony-call-restrictionstatus-e-sys.md) | 限制状态。 |
| [RttState(拨打电话)](arkts-telephony-call-rttstate-e-sys.md) | rtt通话状态 |
| [VideoRequestResultType(拨打电话)](arkts-telephony-call-videorequestresulttype-e-sys.md) | 视频通话升降级请求结果类型。 |
| [VideoStateType(拨打电话)](arkts-telephony-call-videostatetype-e-sys.md) | 视频状态类型。 |
| [VoNRState(拨打电话)](arkts-telephony-call-vonrstate-e-sys.md) | 5G语音开关状态。 |
| [XCallType(拨打电话)](arkts-telephony-call-xcalltype-e-sys.md) | 表示XCall的类型。 |
<!--DelEnd-->
