# @ohos.telephony.call(拨打电话)

该模块提供呼叫管理功能，包括拨打电话、跳转到拨号界面、获取通话状态、格式化电话号码等。

如需订阅通话状态请使用[`observer.on('callStateChange')`](arkts-telephony-observer-on-f.md#oncallstatechange)。

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.CallManager

## 导入模块

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [answerCall](arkts-telephony-call-answercall-f.md) | 接听来电。使用callback异步回调。 |
| [dial](arkts-telephony-call-dial-f.md) | 拨打电话，可设置通话参数。使用callback异步回调。 |
| [dial](arkts-telephony-call-dial-f.md) | 拨打电话，可设置通话参数。使用Promise异步回调。 |
| [dial](arkts-telephony-call-dial-f.md) | 拨打电话。使用callback异步回调。 |
| [formatPhoneNumber](arkts-telephony-call-formatphonenumber-f.md) | 格式化电话号码，可设置格式化参数。使用callback异步回调。 |
| [formatPhoneNumber](arkts-telephony-call-formatphonenumber-f.md) | 格式化电话号码，可设置格式化参数。使用Promise异步回调。 |
| [formatPhoneNumber](arkts-telephony-call-formatphonenumber-f.md) | 格式化电话号码。使用callback异步回调。 |
| [formatPhoneNumberToE164](arkts-telephony-call-formatphonenumbertoe164-f.md) | 将电话号码格式化为E.164表示形式，使用callback异步回调。 |
| [formatPhoneNumberToE164](arkts-telephony-call-formatphonenumbertoe164-f.md) | 将电话号码格式化为E.164表示形式，使用Promise异步回调。 |
| [getCallState](arkts-telephony-call-getcallstate-f.md) | 获取当前通话状态。使用callback异步回调。 |
| [getCallState](arkts-telephony-call-getcallstate-f.md) | 获取当前通话状态。使用Promise异步回调。 |
| [getCallStateSync](arkts-telephony-call-getcallstatesync-f.md) | 获取当前通话状态。 |
| [getCallTransferInfo](arkts-telephony-call-getcalltransferinfo-f.md) | 获取电话号码的呼叫转移状态。使用Promise异步回调。 |
| [hangUpCall](arkts-telephony-call-hangupcall-f.md) | 挂断电话。使用callback异步回调。 |
| [hasCall](arkts-telephony-call-hascall-f.md) | 判断是否存在通话。使用callback异步回调。 |
| [hasCall](arkts-telephony-call-hascall-f.md) | 判断是否存在通话。使用Promise异步回调。 |
| [hasCallSync](arkts-telephony-call-hascallsync-f.md) | 判断是否存在通话。 |
| [hasVoiceCapability](arkts-telephony-call-hasvoicecapability-f.md) | 检查当前设备是否具备语音通话能力。 |
| [isEmergencyPhoneNumber](arkts-telephony-call-isemergencyphonenumber-f.md) | 根据电话号码参数，判断是否是紧急电话号码。使用callback异步回调。 |
| [isEmergencyPhoneNumber](arkts-telephony-call-isemergencyphonenumber-f.md) | 根据电话号码参数，判断是否是紧急电话号码。使用Promise异步回调。 |
| [isEmergencyPhoneNumber](arkts-telephony-call-isemergencyphonenumber-f.md) | 判断是否是紧急电话号码。使用callback异步回调。 |
| [makeCall](arkts-telephony-call-makecall-f.md) | 跳转到拨号界面，并显示待拨出的号码。使用callback异步回调。只支持在UIAbility中调用。 |
| [makeCall](arkts-telephony-call-makecall-f.md) | 跳转到拨号界面，并显示待拨出的号码。使用Promise异步回调。只支持在UIAbility中调用。 |
| [makeCall](arkts-telephony-call-makecall-f.md) | 跳转到拨号界面，并显示待拨出的号码。使用Promise异步回调。只支持在UIAbility中调用。 |
| [makeCall](arkts-telephony-call-makecall-f.md) | 跳转到拨号界面，并显示待拨出的号码。使用Promise异步回调。后台调用需要申请ohos.permission.START_ABILITIES_FROM_BACKGROUND权限。 |
| [makeCallWithToken](arkts-telephony-call-makecallwithtoken-f.md) | 跳转到拨号界面，并显示待拨出的号码。使用Promise异步回调。 |
| [rejectCall](arkts-telephony-call-rejectcall-f.md) | 拒绝来电。使用callback异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [answerCall](arkts-telephony-call-answercall-f-sys.md) | 接听来电。使用callback异步回调。 |
| [answerCall](arkts-telephony-call-answercall-f-sys.md) | 接听来电。使用Promise异步回调。 |
| [answerCall](arkts-telephony-call-answercall-f-sys.md) | 接听来电。使用Promise异步回调。 |
| [answerCall](arkts-telephony-call-answercall-f-sys.md) | 接听rtt来电 |
| [cancelCallUpgrade](arkts-telephony-call-cancelcallupgrade-f-sys.md) | 视频通话升级过程中取消升级。使用Promise异步回调。 |
| [cancelMuted](arkts-telephony-call-cancelmuted-f-sys.md) | 取消通话中的静音。使用callback异步回调。 |
| [cancelMuted](arkts-telephony-call-cancelmuted-f-sys.md) | 取消通话中的静音。使用Promise异步回调。 |
| [canSetCallTransferTime](arkts-telephony-call-cansetcalltransfertime-f-sys.md) | 检查是否可以设置呼叫转移时间。使用callback异步回调。 |
| [canSetCallTransferTime](arkts-telephony-call-cansetcalltransfertime-f-sys.md) | 检查是否可以设置呼叫转移时间。使用Promise异步回调。 |
| [closeUnfinishedUssd](arkts-telephony-call-closeunfinishedussd-f-sys.md) | 取消未激活完成的非结构化补充数据业务。使用callback异步回调。 |
| [closeUnfinishedUssd](arkts-telephony-call-closeunfinishedussd-f-sys.md) | 取消未激活完成的非结构化补充数据业务。使用Promise异步回调。 |
| [combineConference](arkts-telephony-call-combineconference-f-sys.md) | 合并通话，将两通电话合并成会议电话。使用callback异步回调。 |
| [combineConference](arkts-telephony-call-combineconference-f-sys.md) | 合并通话，将两通电话合并成会议电话。使用Promise异步回调。 |
| [controlCamera](arkts-telephony-call-controlcamera-f-sys.md) | 设置使用指定的相机进行视频通话，cameraId为空表示关闭相机。使用Promise异步回调。 |
| [dialCall](arkts-telephony-call-dialcall-f-sys.md) | 拨打电话，可设置通话参数。使用callback异步回调。 |
| [dialCall](arkts-telephony-call-dialcall-f-sys.md) | 拨打电话，可设置通话参数。使用Promise异步回调。 |
| [dialCall](arkts-telephony-call-dialcall-f-sys.md) | 拨打电话。使用callback异步回调。 |
| [disableImsSwitch](arkts-telephony-call-disableimsswitch-f-sys.md) | 禁用Ims开关。使用callback异步回调。 |
| [disableImsSwitch](arkts-telephony-call-disableimsswitch-f-sys.md) | 禁用Ims开关。使用Promise异步回调。 |
| [enableImsSwitch](arkts-telephony-call-enableimsswitch-f-sys.md) | 启用Ims开关。使用callback异步回调。 |
| [enableImsSwitch](arkts-telephony-call-enableimsswitch-f-sys.md) | 启用Ims开关。使用Promise异步回调。 |
| [getCallIdListForConference](arkts-telephony-call-getcallidlistforconference-f-sys.md) | 获取会议的呼叫Id列表。使用callback异步回调。 |
| [getCallIdListForConference](arkts-telephony-call-getcallidlistforconference-f-sys.md) | 获取会议的呼叫Id列表。使用Promise异步回调。 |
| [getCallRestrictionStatus](arkts-telephony-call-getcallrestrictionstatus-f-sys.md) | 获取呼叫限制状态。使用callback异步回调。 |
| [getCallRestrictionStatus](arkts-telephony-call-getcallrestrictionstatus-f-sys.md) | 获取呼叫限制状态。使用Promise异步回调。 |
| [getCallTransferInfo](arkts-telephony-call-getcalltransferinfo-f-sys.md) | 获取呼叫转移信息。使用callback异步回调。 |
| [getCallTransferInfo](arkts-telephony-call-getcalltransferinfo-f-sys.md) | 获取呼叫转移信息。使用Promise异步回调。 |
| [getCallWaitingStatus](arkts-telephony-call-getcallwaitingstatus-f-sys.md) | 获取呼叫等待状态。使用callback异步回调。 |
| [getCallWaitingStatus](arkts-telephony-call-getcallwaitingstatus-f-sys.md) | 获取呼叫等待状态。使用Promise异步回调。 |
| [getMainCallId](arkts-telephony-call-getmaincallid-f-sys.md) | 获取主呼叫Id。使用callback异步回调。 |
| [getMainCallId](arkts-telephony-call-getmaincallid-f-sys.md) | 获取主呼叫Id。使用Promise异步回调。 |
| [getSubCallIdList](arkts-telephony-call-getsubcallidlist-f-sys.md) | 获取子呼叫Id列表。使用callback异步回调。 |
| [getSubCallIdList](arkts-telephony-call-getsubcallidlist-f-sys.md) | 获取子呼叫Id列表。使用Promise异步回调。 |
| [getVoNRState](arkts-telephony-call-getvonrstate-f-sys.md) | 查询NR语音的开关状态。使用callback异步回调。 |
| [getVoNRState](arkts-telephony-call-getvonrstate-f-sys.md) | 查询NR语音的开关状态。使用Promise异步回调。 |
| [hangUpCall](arkts-telephony-call-hangupcall-f-sys.md) | 挂断电话。使用callback异步回调。 |
| [hangUpCall](arkts-telephony-call-hangupcall-f-sys.md) | 挂断电话。使用Promise异步回调。 |
| [holdCall](arkts-telephony-call-holdcall-f-sys.md) | 保持通话。使用callback异步回调。 |
| [holdCall](arkts-telephony-call-holdcall-f-sys.md) | 保持通话。使用Promise异步回调。 |
| [inputDialerSpecialCode](arkts-telephony-call-inputdialerspecialcode-f-sys.md) | 暗码广播。使用callback异步回调。 |
| [inputDialerSpecialCode](arkts-telephony-call-inputdialerspecialcode-f-sys.md) | 暗码广播。使用Promise异步回调。 |
| [isImsSwitchEnabled](arkts-telephony-call-isimsswitchenabled-f-sys.md) | 判断Ims开关是否启用。使用callback异步回调。 |
| [isImsSwitchEnabled](arkts-telephony-call-isimsswitchenabled-f-sys.md) | 判断Ims开关是否启用。使用Promise异步回调。 |
| [isImsSwitchEnabledSync](arkts-telephony-call-isimsswitchenabledsync-f-sys.md) | 判断Ims开关是否启用。调用此API返回结果。 |
| [isInEmergencyCall](arkts-telephony-call-isinemergencycall-f-sys.md) | 判断是否正在处于紧急呼叫。使用callback异步回调。 |
| [isInEmergencyCall](arkts-telephony-call-isinemergencycall-f-sys.md) | 判断是否正在处于紧急呼叫。使用Promise异步回调。 |
| [isNewCallAllowed](arkts-telephony-call-isnewcallallowed-f-sys.md) | 判断是否允许再拨打一通新电话。使用callback异步回调。 |
| [isNewCallAllowed](arkts-telephony-call-isnewcallallowed-f-sys.md) | 判断是否允许再拨打一通新电话。使用Promise异步回调。 |
| [isRinging](arkts-telephony-call-isringing-f-sys.md) | 判断是否正在响铃。使用callback异步回调。 |
| [isRinging](arkts-telephony-call-isringing-f-sys.md) | 判断是否正在响铃。使用Promise异步回调。 |
| [joinConference](arkts-telephony-call-joinconference-f-sys.md) | 加入会议。使用callback异步回调。 |
| [joinConference](arkts-telephony-call-joinconference-f-sys.md) | 加入会议。使用Promise异步回调。 |
| [kickOutFromConference](arkts-telephony-call-kickoutfromconference-f-sys.md) | 移出电话会议，将指定通话从会议电话中挂断。使用callback异步回调。 |
| [kickOutFromConference](arkts-telephony-call-kickoutfromconference-f-sys.md) | 移出电话会议，将指定通话从会议电话中挂断。使用Promise异步回调。 |
| [muteRinger](arkts-telephony-call-muteringer-f-sys.md) | 如果来电铃声响起，设备将停止铃声。否则，此方法不起作用。使用callback异步回调。 |
| [muteRinger](arkts-telephony-call-muteringer-f-sys.md) | 如果来电铃声响起，设备将停止铃声。否则，此方法不起作用。使用Promise异步回调。 |
| [off](arkts-telephony-call-off-f-sys.md#offcalldetailschange) | 取消订阅callDetailsChange事件。使用callback异步回调。 |
| [off](arkts-telephony-call-off-f-sys.md#offcalleventchange) | 取消订阅callEventChange事件。使用callback异步回调。 |
| [off](arkts-telephony-call-off-f-sys.md#offcalldisconnectedcause) | 取消订阅callDisconnectedCause事件。使用callback异步回调。 |
| [off](arkts-telephony-call-off-f-sys.md#offmmicoderesult) | 取消订阅mmiCodeResult事件。使用callback异步回调。 |
| [off](arkts-telephony-call-off-f-sys.md#offaudiodevicechange) | 取消订阅audioDeviceChange事件。使用callback异步回调。 |
| [off](arkts-telephony-call-off-f-sys.md#offpostdialdelay) | 取消订阅拨号后延迟事件。使用callback异步回调。 |
| [off](arkts-telephony-call-off-f-sys.md#offimscallmodechange) | 取消订阅imsCallModeChange事件。使用callback异步回调。 |
| [off](arkts-telephony-call-off-f-sys.md#offcallsessionevent) | 取消订阅callSessionEvent事件。使用callback异步回调。 |
| [off](arkts-telephony-call-off-f-sys.md#offpeerdimensionschange) | 取消订阅peerDimensionsChange事件。使用callback异步回调。 |
| [off](arkts-telephony-call-off-f-sys.md#offcameracapabilitieschange) | 取消订阅cameraCapabilitiesChange事件。使用callback异步回调。 |
| [offReceiveRttMessage](arkts-telephony-call-offreceiverttmessage-f-sys.md) | 去订阅rtt消息事件 |
| [offRttErrCause](arkts-telephony-call-offrtterrcause-f-sys.md) | 去订阅rtt通话错误事件 |
| [offRttModifyInd](arkts-telephony-call-offrttmodifyind-f-sys.md) | 去订阅rtt通话变化事件 |
| [on](arkts-telephony-call-on-f-sys.md#oncalldetailschange) | 订阅callDetailsChange事件。使用callback异步回调。 |
| [on](arkts-telephony-call-on-f-sys.md#oncalleventchange) | 订阅callEventChange事件。使用callback异步回调。 |
| [on](arkts-telephony-call-on-f-sys.md#oncalldisconnectedcause) | 订阅callDisconnectedCause事件。使用callback异步回调。 |
| [on](arkts-telephony-call-on-f-sys.md#onmmicoderesult) | 订阅mmiCodeResult事件。使用callback异步回调。 |
| [on](arkts-telephony-call-on-f-sys.md#onaudiodevicechange) | 订阅通话音频设备切换事件。使用callback异步回调。 |
| [on](arkts-telephony-call-on-f-sys.md#onpostdialdelay) | 订阅拨号后延迟事件。使用callback异步回调。 |
| [on](arkts-telephony-call-on-f-sys.md#onimscallmodechange) | 订阅imsCallModeChange事件。使用callback异步回调。 |
| [on](arkts-telephony-call-on-f-sys.md#oncallsessionevent) | 订阅callSessionEvent事件。使用callback异步回调。 |
| [on](arkts-telephony-call-on-f-sys.md#onpeerdimensionschange) | 订阅peerDimensionsChange事件。使用callback异步回调。 |
| [on](arkts-telephony-call-on-f-sys.md#oncameracapabilitieschange) | 订阅cameraCapabilitiesChange事件。使用callback异步回调。 |
| [onReceiveRttMessage](arkts-telephony-call-onreceiverttmessage-f-sys.md) | 订阅RTT消息事件 |
| [onRttErrCause](arkts-telephony-call-onrtterrcause-f-sys.md) | 订阅rtt通话错误事件 |
| [onRttModifyInd](arkts-telephony-call-onrttmodifyind-f-sys.md) | 订阅rtt通话变化 |
| [postDialProceed](arkts-telephony-call-postdialproceed-f-sys.md) | 继续进行通话。使用callback异步回调。 |
| [postDialProceed](arkts-telephony-call-postdialproceed-f-sys.md) | 继续进行通话。使用Promise异步回调。 |
| [preloadCallUI](arkts-telephony-call-preloadcallui-f-sys.md) | 预加载通话应用 |
| [rejectCall](arkts-telephony-call-rejectcall-f-sys.md) | 拒绝来电。使用callback异步回调。 |
| [rejectCall](arkts-telephony-call-rejectcall-f-sys.md) | 拒绝来电。使用Promise异步回调。 |
| [rejectCall](arkts-telephony-call-rejectcall-f-sys.md) | 拒绝来电。使用callback异步回调。 |
| [rejectCall](arkts-telephony-call-rejectcall-f-sys.md) | 拒绝来电。使用callback异步回调。 |
| [removeMissedIncomingCallNotification](arkts-telephony-call-removemissedincomingcallnotification-f-sys.md) | 删除未接来电通知。使用callback异步回调。 |
| [removeMissedIncomingCallNotification](arkts-telephony-call-removemissedincomingcallnotification-f-sys.md) | 删除未接来电通知。使用Promise异步回调。 |
| [sendCallUiEvent](arkts-telephony-call-sendcalluievent-f-sys.md) | 发布通话界面事件。使用Promise异步回调。 |
| [sendRttMessage](arkts-telephony-call-sendrttmessage-f-sys.md) | 发送rtt消息 |
| [sendUssdResponse](arkts-telephony-call-sendussdresponse-f-sys.md) | 用于向运营商发送USSD业务（Unstructured Supplementary Service Data，非结构化补充数据业务）的响应消息。 |
| [separateConference](arkts-telephony-call-separateconference-f-sys.md) | 分离会议电话。使用callback异步回调。 |
| [separateConference](arkts-telephony-call-separateconference-f-sys.md) | 分离会议电话。使用Promise异步回调。 |
| [setAudioDevice](arkts-telephony-call-setaudiodevice-f-sys.md) | 设置通话音频设备。使用callback异步回调。 |
| [setAudioDevice](arkts-telephony-call-setaudiodevice-f-sys.md) | 设置通话音频设备。使用Promise异步回调。 |
| [setCallRestriction](arkts-telephony-call-setcallrestriction-f-sys.md) | 设置呼叫限制状态。使用callback异步回调。 |
| [setCallRestriction](arkts-telephony-call-setcallrestriction-f-sys.md) | 设置呼叫限制状态。使用Promise异步回调。 |
| [setCallRestrictionPassword](arkts-telephony-call-setcallrestrictionpassword-f-sys.md) | 修改呼叫限制密码。使用callback异步回调。 |
| [setCallRestrictionPassword](arkts-telephony-call-setcallrestrictionpassword-f-sys.md) | 修改呼叫限制密码。使用Promise异步回调。 |
| [setCallTransfer](arkts-telephony-call-setcalltransfer-f-sys.md) | 设置呼叫转移信息。使用callback异步回调。 |
| [setCallTransfer](arkts-telephony-call-setcalltransfer-f-sys.md) | 设置呼叫转移信息。使用Promise异步回调。 |
| [setCallWaiting](arkts-telephony-call-setcallwaiting-f-sys.md) | 设置呼叫等待。使用callback异步回调。 |
| [setCallWaiting](arkts-telephony-call-setcallwaiting-f-sys.md) | 设置呼叫等待。使用Promise异步回调。 |
| [setDeviceDirection](arkts-telephony-call-setdevicedirection-f-sys.md) | 设置视频通话画面显示方向为设备方向。使用Promise异步回调。 |
| [setDisplaySurface](arkts-telephony-call-setdisplaysurface-f-sys.md) | 设置远端画面窗口。使用Promise异步回调。 |
| [setMuted](arkts-telephony-call-setmuted-f-sys.md) | 设置通话中的静音。使用callback异步回调。 |
| [setMuted](arkts-telephony-call-setmuted-f-sys.md) | 设置通话中的静音。使用Promise异步回调。 |
| [setPreviewSurface](arkts-telephony-call-setpreviewsurface-f-sys.md) | 设置本端预览画面窗口。使用Promise异步回调。 |
| [setRttCapability](arkts-telephony-call-setrttcapability-f-sys.md) | 设置rtt功能 |
| [setVoNRState](arkts-telephony-call-setvonrstate-f-sys.md) | 设置NR语音的开关状态。使用callback异步回调。 |
| [setVoNRState](arkts-telephony-call-setvonrstate-f-sys.md) | 设置NR语音的开关状态。使用Promise异步回调。 |
| [startDTMF](arkts-telephony-call-startdtmf-f-sys.md) | 启动双音多频。使用callback异步回调。 |
| [startDTMF](arkts-telephony-call-startdtmf-f-sys.md) | 启动双音多频。使用Promise异步回调。 |
| [startRtt](arkts-telephony-call-startrtt-f-sys.md) | 启动rtt |
| [stopDTMF](arkts-telephony-call-stopdtmf-f-sys.md) | 停止双音多频。使用callback异步回调。 |
| [stopDTMF](arkts-telephony-call-stopdtmf-f-sys.md) | 停止双音多频。使用Promise异步回调。 |
| [stopRtt](arkts-telephony-call-stoprtt-f-sys.md) | 停止rtt |
| [switchCall](arkts-telephony-call-switchcall-f-sys.md) | 切换呼叫。使用callback异步回调。 |
| [switchCall](arkts-telephony-call-switchcall-f-sys.md) | 切换呼叫。使用Promise异步回调。 |
| [unHoldCall](arkts-telephony-call-unholdcall-f-sys.md) | 取消保持通话。使用callback异步回调。 |
| [unHoldCall](arkts-telephony-call-unholdcall-f-sys.md) | 取消保持通话。使用Promise异步回调。 |
| [unloadCallUI](arkts-telephony-call-unloadcallui-f-sys.md) | 卸载通话应用 |
| [updateImsCallMode](arkts-telephony-call-updateimscallmode-f-sys.md) | 更新Ims呼叫模式。使用callback异步回调。 |
| [updateImsCallMode](arkts-telephony-call-updateimscallmode-f-sys.md) | 更新Ims呼叫模式。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CallTransferResult](arkts-telephony-call-calltransferresult-i.md) | 呼叫转移结果。 |
| [DialOptions](arkts-telephony-call-dialoptions-i.md) | 拨打电话的可选参数。 |
| [EmergencyNumberOptions](arkts-telephony-call-emergencynumberoptions-i.md) | 判断是否是紧急电话号码的可选参数。 |
| [MakeCallOptions](arkts-telephony-call-makecalloptions-i.md) | 拨打电话的可选参数。 |
| [NumberFormatOptions](arkts-telephony-call-numberformatoptions-i.md) | 格式化号码的可选参数。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AudioDevice](arkts-telephony-call-audiodevice-i-sys.md) | 音频设备。 |
| [AudioDeviceCallbackInfo](arkts-telephony-call-audiodevicecallbackinfo-i-sys.md) | 音频设备信息。 |
| [CallAttributeOptions](arkts-telephony-call-callattributeoptions-i-sys.md) | 调用属性选项。 |
| [CallEventOptions](arkts-telephony-call-calleventoptions-i-sys.md) | 呼叫事件的可选参数。 |
| [CallRestrictionInfo](arkts-telephony-call-callrestrictioninfo-i-sys.md) | 呼叫限制信息。 |
| [CallSessionEvent](arkts-telephony-call-callsessionevent-i-sys.md) | 视频通话事件信息。 |
| [CallTransferInfo](arkts-telephony-call-calltransferinfo-i-sys.md) | 呼叫转移信息。 |
| [CallTransferResult](arkts-telephony-call-calltransferresult-i-sys.md) | 呼叫转移结果。 |
| [CameraCapabilities](arkts-telephony-call-cameracapabilities-i-sys.md) | 视频通话本端相机画面分辨率信息。 |
| [DialCallOptions](arkts-telephony-call-dialcalloptions-i-sys.md) | 拨打电话的可选参数。 |
| [DialOptions](arkts-telephony-call-dialoptions-i-sys.md) | 拨打电话的可选参数。 |
| [DisconnectedDetails](arkts-telephony-call-disconnecteddetails-i-sys.md) | 通话结束原因。 |
| [ImsCallModeInfo](arkts-telephony-call-imscallmodeinfo-i-sys.md) | 视频通话模式信息。 |
| [MmiCodeResults](arkts-telephony-call-mmicoderesults-i-sys.md) | MMI码结果。 |
| [NumberMarkInfo](arkts-telephony-call-numbermarkinfo-i-sys.md) | 电话号码的标记信息。 |
| [PeerDimensionsDetail](arkts-telephony-call-peerdimensionsdetail-i-sys.md) | 视频通话对端画面分辨率信息。 |
| [RejectMessageOptions](arkts-telephony-call-rejectmessageoptions-i-sys.md) | 拒绝消息可选参数。 |
| [RttErrorInfo](arkts-telephony-call-rtterrorinfo-i-sys.md) | rtt通话错误报告 |
| [RttEventInfo](arkts-telephony-call-rtteventinfo-i-sys.md) | rtt通话事件 |
| [RttMessageInfo](arkts-telephony-call-rttmessageinfo-i-sys.md) | rtt通话消息 |
| [VoipCallAttribute](arkts-telephony-call-voipcallattribute-i-sys.md) | VoIP通话信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CallState](arkts-telephony-call-callstate-e.md) | 通话状态码。 |
| [CallTransferType](arkts-telephony-call-calltransfertype-e.md) | 呼叫转移类型。 |
| [CCallState](arkts-telephony-call-ccallstate-e.md) | 运营商通话状态码。 |
| [TelCallState](arkts-telephony-call-telcallstate-e.md) | 通话状态码。 |
| [TransferStatus](arkts-telephony-call-transferstatus-e.md) | 转移状态。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AudioDeviceType](arkts-telephony-call-audiodevicetype-e-sys.md) | 音频设备类型。 |
| [CallAbilityEventId](arkts-telephony-call-callabilityeventid-e-sys.md) | 呼叫能力事件Id。 |
| [CallRestrictionMode](arkts-telephony-call-callrestrictionmode-e-sys.md) | 呼叫限制模式。 |
| [CallRestrictionType](arkts-telephony-call-callrestrictiontype-e-sys.md) | 呼叫限制类型。 |
| [CallSessionEventId](arkts-telephony-call-callsessioneventid-e-sys.md) | 视频通话事件类型。 |
| [CallTransferSettingType](arkts-telephony-call-calltransfersettingtype-e-sys.md) | 设置呼叫转移类型。 |
| [CallType](arkts-telephony-call-calltype-e-sys.md) | 通话类型。 |
| [CallWaitingStatus](arkts-telephony-call-callwaitingstatus-e-sys.md) | 呼叫等待状态。 |
| [ConferenceState](arkts-telephony-call-conferencestate-e-sys.md) | 会议状态。 |
| [DetailedCallState](arkts-telephony-call-detailedcallstate-e-sys.md) | 详细的呼叫状态。 |
| [DeviceDirection](arkts-telephony-call-devicedirection-e-sys.md) | 视频通话画面方向类型。 |
| [DialScene](arkts-telephony-call-dialscene-e-sys.md) | 拨号场景。 |
| [DialType](arkts-telephony-call-dialtype-e-sys.md) | 拨号类型。 |
| [DisconnectedReason](arkts-telephony-call-disconnectedreason-e-sys.md) | 断开连接的详细信息。 |
| [ImsCallMode](arkts-telephony-call-imscallmode-e-sys.md) | IP多媒体系统调用模式。 |
| [ImsRttMode](arkts-telephony-call-imsrttmode-e-sys.md) | rtt通话模式 |
| [MarkType](arkts-telephony-call-marktype-e-sys.md) | 号码标记的类型。 |
| [MmiCodeResult](arkts-telephony-call-mmicoderesult-e-sys.md) | MMI码结果。 |
| [RestrictionStatus](arkts-telephony-call-restrictionstatus-e-sys.md) | 限制状态。 |
| [RttState](arkts-telephony-call-rttstate-e-sys.md) | rtt通话状态 |
| [VideoRequestResultType](arkts-telephony-call-videorequestresulttype-e-sys.md) | 视频通话升降级请求结果类型。 |
| [VideoStateType](arkts-telephony-call-videostatetype-e-sys.md) | 视频状态类型。 |
| [VoNRState](arkts-telephony-call-vonrstate-e-sys.md) | 5G语音开关状态。 |
| [XCallType](arkts-telephony-call-xcalltype-e-sys.md) | 表示XCall的类型。 |
<!--DelEnd-->
