# @ohos.telephony.call

该模块提供呼叫管理功能，包括拨打电话、跳转到拨号界面、获取通话状态、格式化电话号码等。 如需订阅通话状态请使用 `observer.on('callStateChange')` 。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace call--><!--Device-unnamed-declare namespace call-End-->

**系统能力：** SystemCapability.Telephony.CallManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [dial](arkts-telephony-call-dial-f.md#dial) | 拨打电话，可设置通话参数。使用callback异步回调。 |
| [dial](arkts-telephony-call-dial-f.md#dial) | 拨打电话，可设置通话参数。使用Promise异步回调。 |
| [dial](arkts-telephony-call-dial-f.md#dial) | 拨打电话。使用callback异步回调。 |
| [formatPhoneNumber](arkts-telephony-call-formatphonenumber-f.md#formatPhoneNumber) | 格式化电话号码，可设置格式化参数。使用callback异步回调。 电话号码格式化后为标准数字字符串，例如：“138 xxxx xxxx”、“0755 xxxx xxxx”。 |
| [formatPhoneNumber](arkts-telephony-call-formatphonenumber-f.md#formatPhoneNumber) | 格式化电话号码，可设置格式化参数。使用Promise异步回调。 电话号码格式化后为标准数字字符串，例如：“138 xxxx xxxx”、“0755 xxxx xxxx”。 |
| [formatPhoneNumber](arkts-telephony-call-formatphonenumber-f.md#formatPhoneNumber) | 格式化电话号码。使用callback异步回调。 电话号码格式化后为标准数字字符串，例如：“138 xxxx xxxx”、“0755 xxxx xxxx”。 |
| [formatPhoneNumberToE164](arkts-telephony-call-formatphonenumbertoe164-f.md#formatPhoneNumberToE164) | 将电话号码格式化为E.164表示形式，使用callback异步回调。 待格式化的电话号码需要与传入的国家码相匹配，如中国电话号码需要传入国家码CN，否则格式化后的电话号码为null。 |
| [formatPhoneNumberToE164](arkts-telephony-call-formatphonenumbertoe164-f.md#formatPhoneNumberToE164) | 将电话号码格式化为E.164表示形式，使用Promise异步回调。 待格式化的电话号码需要与传入的国家码相匹配，如中国电话号码需要传入国家码CN，否则格式化后的电话号码为null。 支持所有国家码。 |
| [getCallState](arkts-telephony-call-getcallstate-f.md#getCallState) | 获取当前通话状态。使用callback异步回调。 |
| [getCallState](arkts-telephony-call-getcallstate-f.md#getCallState) | 获取当前通话状态。使用Promise异步回调。 |
| [getCallStateSync](arkts-telephony-call-getcallstatesync-f.md#getCallStateSync) | 获取当前通话状态。 |
| [getCallTransferInfo](arkts-telephony-call-getcalltransferinfo-f.md#getCallTransferInfo) | 获取电话号码的呼叫转移状态。使用Promise异步回调。 |
| [hasCall](arkts-telephony-call-hascall-f.md#hasCall) | 判断是否存在通话。使用callback异步回调。 |
| [hasCall](arkts-telephony-call-hascall-f.md#hasCall) | 判断是否存在通话。使用Promise异步回调。 |
| [hasCallSync](arkts-telephony-call-hascallsync-f.md#hasCallSync) | 判断是否存在通话。 |
| [hasVoiceCapability](arkts-telephony-call-hasvoicecapability-f.md#hasVoiceCapability) | 检查当前设备是否具备语音通话能力。 |
| [isEmergencyPhoneNumber](arkts-telephony-call-isemergencyphonenumber-f.md#isEmergencyPhoneNumber) | 根据电话号码参数，判断是否是紧急电话号码。使用callback异步回调。 |
| [isEmergencyPhoneNumber](arkts-telephony-call-isemergencyphonenumber-f.md#isEmergencyPhoneNumber) | 根据电话号码参数，判断是否是紧急电话号码。使用Promise异步回调。 |
| [isEmergencyPhoneNumber](arkts-telephony-call-isemergencyphonenumber-f.md#isEmergencyPhoneNumber) | 判断是否是紧急电话号码。使用callback异步回调。 |
| [makeCall](arkts-telephony-call-makecall-f.md#makeCall) | 跳转到拨号界面，并显示待拨出的号码。使用callback异步回调。只支持在UIAbility中调用。 |
| [makeCall](arkts-telephony-call-makecall-f.md#makeCall) | 跳转到拨号界面，并显示待拨出的号码。使用Promise异步回调。只支持在UIAbility中调用。 |
| [makeCall](arkts-telephony-call-makecall-f.md#makeCall) | 跳转到拨号界面，并显示待拨出的号码。使用Promise异步回调。只支持在UIAbility中调用。 |
| [makeCall](arkts-telephony-call-makecall-f.md#makeCall) | 跳转到拨号界面，并显示待拨出的号码。使用Promise异步回调。后台调用需要申请ohos.permission.START_ABILITIES_FROM_BACKGROUND权限。 |
| [makeCallWithToken](arkts-telephony-call-makecallwithtoken-f.md#makeCallWithToken) | 跳转到拨号界面，并显示待拨出的号码。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [answerCall](arkts-telephony-call-answercall-f-sys.md#answerCall) | 接听来电。使用callback异步回调。 |
| [answerCall](arkts-telephony-call-answercall-f-sys.md#answerCall（系统接口）) | 接听来电。使用Promise异步回调。 |
| [answerCall](arkts-telephony-call-answercall-f-sys.md#answerCall（系统接口）) | 接听来电。使用callback异步回调。 |
| [answerCall](arkts-telephony-call-answercall-f-sys.md#answerCall（系统接口）) | 接听来电。使用Promise异步回调。 |
| [answerCall](arkts-telephony-call-answercall-f-sys.md#answerCall（系统接口）) | 接听rtt来电 |
| [canSetCallTransferTime](arkts-telephony-call-cansetcalltransfertime-f-sys.md#canSetCallTransferTime) | 检查是否可以设置呼叫转移时间。使用callback异步回调。 |
| [canSetCallTransferTime](arkts-telephony-call-cansetcalltransfertime-f-sys.md#canSetCallTransferTime（系统接口）) | 检查是否可以设置呼叫转移时间。使用Promise异步回调。 |
| [cancelCallUpgrade](arkts-telephony-call-cancelcallupgrade-f-sys.md#cancelCallUpgrade) | 视频通话升级过程中取消升级。使用Promise异步回调。 |
| [cancelMuted](arkts-telephony-call-cancelmuted-f-sys.md#cancelMuted) | 取消通话中的静音。使用callback异步回调。 |
| [cancelMuted](arkts-telephony-call-cancelmuted-f-sys.md#cancelMuted（系统接口）) | 取消通话中的静音。使用Promise异步回调。 |
| [closeUnfinishedUssd](arkts-telephony-call-closeunfinishedussd-f-sys.md#closeUnfinishedUssd) | 取消未激活完成的非结构化补充数据业务。使用callback异步回调。 |
| [closeUnfinishedUssd](arkts-telephony-call-closeunfinishedussd-f-sys.md#closeUnfinishedUssd（系统接口）) | 取消未激活完成的非结构化补充数据业务。使用Promise异步回调。 |
| [combineConference](arkts-telephony-call-combineconference-f-sys.md#combineConference) | 合并通话，将两通电话合并成会议电话。使用callback异步回调。 |
| [combineConference](arkts-telephony-call-combineconference-f-sys.md#combineConference（系统接口）) | 合并通话，将两通电话合并成会议电话。使用Promise异步回调。 |
| [controlCamera](arkts-telephony-call-controlcamera-f-sys.md#controlCamera) | 设置使用指定的相机进行视频通话，cameraId为空表示关闭相机。使用Promise异步回调。 |
| [dialCall](arkts-telephony-call-dialcall-f-sys.md#dialCall) | 拨打电话，可设置通话参数。使用callback异步回调。 |
| [dialCall](arkts-telephony-call-dialcall-f-sys.md#dialCall（系统接口）) | 拨打电话，可设置通话参数。使用Promise异步回调。 |
| [dialCall](arkts-telephony-call-dialcall-f-sys.md#dialCall（系统接口）) | 拨打电话。使用callback异步回调。 |
| [disableImsSwitch](arkts-telephony-call-disableimsswitch-f-sys.md#disableImsSwitch) | 禁用Ims开关。使用callback异步回调。 |
| [disableImsSwitch](arkts-telephony-call-disableimsswitch-f-sys.md#disableImsSwitch（系统接口）) | 禁用Ims开关。使用Promise异步回调。 |
| [enableImsSwitch](arkts-telephony-call-enableimsswitch-f-sys.md#enableImsSwitch) | 启用Ims开关。使用callback异步回调。 |
| [enableImsSwitch](arkts-telephony-call-enableimsswitch-f-sys.md#enableImsSwitch（系统接口）) | 启用Ims开关。使用Promise异步回调。 |
| [getCallIdListForConference](arkts-telephony-call-getcallidlistforconference-f-sys.md#getCallIdListForConference) | 获取会议的呼叫Id列表。使用callback异步回调。 |
| [getCallIdListForConference](arkts-telephony-call-getcallidlistforconference-f-sys.md#getCallIdListForConference（系统接口）) | 获取会议的呼叫Id列表。使用Promise异步回调。 |
| [getCallRestrictionStatus](arkts-telephony-call-getcallrestrictionstatus-f-sys.md#getCallRestrictionStatus) | 获取呼叫限制状态。使用callback异步回调。 |
| [getCallRestrictionStatus](arkts-telephony-call-getcallrestrictionstatus-f-sys.md#getCallRestrictionStatus（系统接口）) | 获取呼叫限制状态。使用Promise异步回调。 |
| [getCallTransferInfo](arkts-telephony-call-getcalltransferinfo-f-sys.md#getCallTransferInfo（系统接口）) | 获取呼叫转移信息。使用callback异步回调。 |
| [getCallTransferInfo](arkts-telephony-call-getcalltransferinfo-f-sys.md#getCallTransferInfo（系统接口）) | 获取呼叫转移信息。使用Promise异步回调。 |
| [getCallWaitingStatus](arkts-telephony-call-getcallwaitingstatus-f-sys.md#getCallWaitingStatus) | 获取呼叫等待状态。使用callback异步回调。 |
| [getCallWaitingStatus](arkts-telephony-call-getcallwaitingstatus-f-sys.md#getCallWaitingStatus（系统接口）) | 获取呼叫等待状态。使用Promise异步回调。 |
| [getMainCallId](arkts-telephony-call-getmaincallid-f-sys.md#getMainCallId) | 获取主呼叫Id。使用callback异步回调。 |
| [getMainCallId](arkts-telephony-call-getmaincallid-f-sys.md#getMainCallId（系统接口）) | 获取主呼叫Id。使用Promise异步回调。 |
| [getSubCallIdList](arkts-telephony-call-getsubcallidlist-f-sys.md#getSubCallIdList) | 获取子呼叫Id列表。使用callback异步回调。 |
| [getSubCallIdList](arkts-telephony-call-getsubcallidlist-f-sys.md#getSubCallIdList（系统接口）) | 获取子呼叫Id列表。使用Promise异步回调。 |
| [getVoNRState](arkts-telephony-call-getvonrstate-f-sys.md#getVoNRState) | 查询NR语音的开关状态。使用callback异步回调。 |
| [getVoNRState](arkts-telephony-call-getvonrstate-f-sys.md#getVoNRState（系统接口）) | 查询NR语音的开关状态。使用Promise异步回调。 |
| [hangUpCall](arkts-telephony-call-hangupcall-f-sys.md#hangUpCall) | 挂断电话。使用callback异步回调。 |
| [hangUpCall](arkts-telephony-call-hangupcall-f-sys.md#hangUpCall（系统接口）) | 挂断电话。使用Promise异步回调。 |
| [hangUpCall](arkts-telephony-call-hangupcall-f-sys.md#hangUpCall（系统接口）) | 挂断电话。使用callback异步回调。 |
| [holdCall](arkts-telephony-call-holdcall-f-sys.md#holdCall) | 保持通话。使用callback异步回调。 |
| [holdCall](arkts-telephony-call-holdcall-f-sys.md#holdCall（系统接口）) | 保持通话。使用Promise异步回调。 |
| [inputDialerSpecialCode](arkts-telephony-call-inputdialerspecialcode-f-sys.md#inputDialerSpecialCode) | 暗码广播。使用callback异步回调。 |
| [inputDialerSpecialCode](arkts-telephony-call-inputdialerspecialcode-f-sys.md#inputDialerSpecialCode（系统接口）) | 暗码广播。使用Promise异步回调。 |
| [isImsSwitchEnabled](arkts-telephony-call-isimsswitchenabled-f-sys.md#isImsSwitchEnabled) | 判断Ims开关是否启用。使用callback异步回调。 |
| [isImsSwitchEnabled](arkts-telephony-call-isimsswitchenabled-f-sys.md#isImsSwitchEnabled（系统接口）) | 判断Ims开关是否启用。使用Promise异步回调。 |
| [isImsSwitchEnabledSync](arkts-telephony-call-isimsswitchenabledsync-f-sys.md#isImsSwitchEnabledSync) | 判断Ims开关是否启用。调用此API返回结果。 |
| [isInEmergencyCall](arkts-telephony-call-isinemergencycall-f-sys.md#isInEmergencyCall) | 判断是否正在处于紧急呼叫。使用callback异步回调。 |
| [isInEmergencyCall](arkts-telephony-call-isinemergencycall-f-sys.md#isInEmergencyCall（系统接口）) | 判断是否正在处于紧急呼叫。使用Promise异步回调。 |
| [isNewCallAllowed](arkts-telephony-call-isnewcallallowed-f-sys.md#isNewCallAllowed) | 判断是否允许再拨打一通新电话。使用callback异步回调。 |
| [isNewCallAllowed](arkts-telephony-call-isnewcallallowed-f-sys.md#isNewCallAllowed（系统接口）) | 判断是否允许再拨打一通新电话。使用Promise异步回调。 |
| [isRinging](arkts-telephony-call-isringing-f-sys.md#isRinging) | 判断是否正在响铃。使用callback异步回调。 |
| [isRinging](arkts-telephony-call-isringing-f-sys.md#isRinging（系统接口）) | 判断是否正在响铃。使用Promise异步回调。 |
| [joinConference](arkts-telephony-call-joinconference-f-sys.md#joinConference) | 加入会议。使用callback异步回调。 |
| [joinConference](arkts-telephony-call-joinconference-f-sys.md#joinConference（系统接口）) | 加入会议。使用Promise异步回调。 |
| [kickOutFromConference](arkts-telephony-call-kickoutfromconference-f-sys.md#kickOutFromConference) | 移出电话会议，将指定通话从会议电话中挂断。使用callback异步回调。 |
| [kickOutFromConference](arkts-telephony-call-kickoutfromconference-f-sys.md#kickOutFromConference（系统接口）) | 移出电话会议，将指定通话从会议电话中挂断。使用Promise异步回调。 |
| [muteRinger](arkts-telephony-call-muteringer-f-sys.md#muteRinger) | 如果来电铃声响起，设备将停止铃声。否则，此方法不起作用。使用callback异步回调。 |
| [muteRinger](arkts-telephony-call-muteringer-f-sys.md#muteRinger（系统接口）) | 如果来电铃声响起，设备将停止铃声。否则，此方法不起作用。使用Promise异步回调。 |
| [offAudioDeviceChange](arkts-telephony-call-offaudiodevicechange-f-sys.md#offAudioDeviceChange) | Unsubscribe from the audioDeviceChange event. |
| [offCallDetailsChange](arkts-telephony-call-offcalldetailschange-f-sys.md#offCallDetailsChange) | Unsubscribe from the callDetailsChange event. |
| [offCallDisconnectedCause](arkts-telephony-call-offcalldisconnectedcause-f-sys.md#offCallDisconnectedCause) | Unsubscribe from the callDisconnectedCause event. |
| [offCallEventChange](arkts-telephony-call-offcalleventchange-f-sys.md#offCallEventChange) | Unsubscribe from the callEventChange event. |
| [offCallSessionEvent](arkts-telephony-call-offcallsessionevent-f-sys.md#offCallSessionEvent) | Unsubscribe from the callSessionEvent. |
| [offCameraCapabilitiesChange](arkts-telephony-call-offcameracapabilitieschange-f-sys.md#offCameraCapabilitiesChange) | Unsubscribe from the cameraCapabilitiesChange event. |
| [offImsCallModeChange](arkts-telephony-call-offimscallmodechange-f-sys.md#offImsCallModeChange) | Unsubscribe from the imsCallModeChange event. |
| [offMmiCodeResult](arkts-telephony-call-offmmicoderesult-f-sys.md#offMmiCodeResult) | Unsubscribe from the mmiCodeResult event. |
| [offPeerDimensionsChange](arkts-telephony-call-offpeerdimensionschange-f-sys.md#offPeerDimensionsChange) | Unsubscribe from the peerDimensionsChange event. |
| [offPostDialDelay](arkts-telephony-call-offpostdialdelay-f-sys.md#offPostDialDelay) | Unsubscribe from the postDialDelay event. |
| [offReceiveRttMessage](arkts-telephony-call-offreceiverttmessage-f-sys.md#offReceiveRttMessage) | 去订阅rtt消息事件 |
| [offRttErrCause](arkts-telephony-call-offrtterrcause-f-sys.md#offRttErrCause) | 去订阅rtt通话错误事件 |
| [offRttModifyInd](arkts-telephony-call-offrttmodifyind-f-sys.md#offRttModifyInd) | 去订阅rtt通话变化事件 |
| off_audioDeviceChange | 取消订阅audioDeviceChange事件。使用callback异步回调。 |
| off_callDetailsChange | 取消订阅callDetailsChange事件。使用callback异步回调。 |
| off_callDisconnectedCause | 取消订阅callDisconnectedCause事件。使用callback异步回调。 |
| off_callEventChange | 取消订阅callEventChange事件。使用callback异步回调。 |
| off_callSessionEvent | 取消订阅callSessionEvent事件。使用callback异步回调。 |
| off_cameraCapabilitiesChange | 取消订阅cameraCapabilitiesChange事件。使用callback异步回调。 |
| off_imsCallModeChange | 取消订阅imsCallModeChange事件。使用callback异步回调。 |
| off_mmiCodeResult | 取消订阅mmiCodeResult事件。使用callback异步回调。 |
| off_peerDimensionsChange | 取消订阅peerDimensionsChange事件。使用callback异步回调。 |
| off_postDialDelay | 取消订阅拨号后延迟事件。使用callback异步回调。 |
| [onAudioDeviceChange](arkts-telephony-call-onaudiodevicechange-f-sys.md#onAudioDeviceChange) | Subscribe to the audioDeviceChange event. |
| [onCallDetailsChange](arkts-telephony-call-oncalldetailschange-f-sys.md#onCallDetailsChange) | Subscribe to the callDetailsChange event. |
| [onCallDisconnectedCause](arkts-telephony-call-oncalldisconnectedcause-f-sys.md#onCallDisconnectedCause) | Subscribe to the callDisconnectedCause event. |
| [onCallEventChange](arkts-telephony-call-oncalleventchange-f-sys.md#onCallEventChange) | Subscribe to the callEventChange event. |
| [onCallSessionEvent](arkts-telephony-call-oncallsessionevent-f-sys.md#onCallSessionEvent) | Subscribe to the callSessionEvent. |
| [onCameraCapabilitiesChange](arkts-telephony-call-oncameracapabilitieschange-f-sys.md#onCameraCapabilitiesChange) | Subscribe to the cameraCapabilitiesChange event. |
| [onImsCallModeChange](arkts-telephony-call-onimscallmodechange-f-sys.md#onImsCallModeChange) | Subscribe to the imsCallModeChange event. |
| [onMmiCodeResult](arkts-telephony-call-onmmicoderesult-f-sys.md#onMmiCodeResult) | Subscribe to the mmiCodeResult event. |
| [onPeerDimensionsChange](arkts-telephony-call-onpeerdimensionschange-f-sys.md#onPeerDimensionsChange) | Subscribe to the peerDimensionsChange event. |
| [onPostDialDelay](arkts-telephony-call-onpostdialdelay-f-sys.md#onPostDialDelay) | Subscribe to the postDialDelay event. |
| [onReceiveRttMessage](arkts-telephony-call-onreceiverttmessage-f-sys.md#onReceiveRttMessage) | 订阅RTT消息事件 |
| [onRttErrCause](arkts-telephony-call-onrtterrcause-f-sys.md#onRttErrCause) | 订阅rtt通话错误事件 |
| [onRttModifyInd](arkts-telephony-call-onrttmodifyind-f-sys.md#onRttModifyInd) | 订阅rtt通话变化 |
| on_audioDeviceChange | 订阅通话音频设备切换事件。使用callback异步回调。 |
| on_callDetailsChange | 订阅callDetailsChange事件。使用callback异步回调。 |
| on_callDisconnectedCause | 订阅callDisconnectedCause事件。使用callback异步回调。 |
| on_callEventChange | 订阅callEventChange事件。使用callback异步回调。 |
| on_callSessionEvent | 订阅callSessionEvent事件。使用callback异步回调。 |
| on_cameraCapabilitiesChange | 订阅cameraCapabilitiesChange事件。使用callback异步回调。 |
| on_imsCallModeChange | 订阅imsCallModeChange事件。使用callback异步回调。 |
| on_mmiCodeResult | 订阅mmiCodeResult事件。使用callback异步回调。 |
| on_peerDimensionsChange | 订阅peerDimensionsChange事件。使用callback异步回调。 |
| on_postDialDelay | 订阅拨号后延迟事件。使用callback异步回调。 |
| [postDialProceed](arkts-telephony-call-postdialproceed-f-sys.md#postDialProceed) | 继续进行通话。使用callback异步回调。 当用户呼叫号码为：“普通电话号码”+“;”+"DTMF字符"(例如：“400xxxxxxx;123”)，并且已经订阅了通话后延迟事件，电话接通后，系统将上报通话后延迟事件，应用可以调用此接口选择是否发送DTMF音。 |
| [postDialProceed](arkts-telephony-call-postdialproceed-f-sys.md#postDialProceed（系统接口）) | 继续进行通话。使用Promise异步回调。 当用户呼叫号码为：“普通电话号码”+“;”+"DTMF字符"(例如：“400xxxxxxx;123”)，并且已经订阅了通话后延迟事件，电话接通后，系统将上报通话后延迟事件，应用可以调用此接口选择是否发送DTMF音。 |
| [preloadCallUI](arkts-telephony-call-preloadcallui-f-sys.md#preloadCallUI) | 预加载通话应用 |
| [rejectCall](arkts-telephony-call-rejectcall-f-sys.md#rejectCall) | 拒绝来电。使用callback异步回调。 |
| [rejectCall](arkts-telephony-call-rejectcall-f-sys.md#rejectCall（系统接口）) | 拒绝来电。使用Promise异步回调。 |
| [rejectCall](arkts-telephony-call-rejectcall-f-sys.md#rejectCall（系统接口）) | 拒绝来电。使用callback异步回调。 |
| [rejectCall](arkts-telephony-call-rejectcall-f-sys.md#rejectCall（系统接口）) | 拒绝来电。使用callback异步回调。 |
| [rejectCall](arkts-telephony-call-rejectcall-f-sys.md#rejectCall（系统接口）) | 拒绝来电。使用callback异步回调。 |
| [removeMissedIncomingCallNotification](arkts-telephony-call-removemissedincomingcallnotification-f-sys.md#removeMissedIncomingCallNotification) | 删除未接来电通知。使用callback异步回调。 |
| [removeMissedIncomingCallNotification](arkts-telephony-call-removemissedincomingcallnotification-f-sys.md#removeMissedIncomingCallNotification（系统接口）) | 删除未接来电通知。使用Promise异步回调。 |
| [sendCallUiEvent](arkts-telephony-call-sendcalluievent-f-sys.md#sendCallUiEvent) | 发布通话界面事件。使用Promise异步回调。 |
| [sendRttMessage](arkts-telephony-call-sendrttmessage-f-sys.md#sendRttMessage) | 发送rtt消息 |
| [sendUssdResponse](arkts-telephony-call-sendussdresponse-f-sys.md#sendUssdResponse) | 用于向运营商发送USSD业务（Unstructured Supplementary Service Data，非结构化补充数据业务）的响应消息。 |
| [separateConference](arkts-telephony-call-separateconference-f-sys.md#separateConference) | 分离会议电话。使用callback异步回调。 |
| [separateConference](arkts-telephony-call-separateconference-f-sys.md#separateConference（系统接口）) | 分离会议电话。使用Promise异步回调。 |
| [setAudioDevice](arkts-telephony-call-setaudiodevice-f-sys.md#setAudioDevice) | 设置通话音频设备。使用callback异步回调。 |
| [setAudioDevice](arkts-telephony-call-setaudiodevice-f-sys.md#setAudioDevice（系统接口）) | 设置通话音频设备。使用Promise异步回调。 |
| [setCallRestriction](arkts-telephony-call-setcallrestriction-f-sys.md#setCallRestriction) | 设置呼叫限制状态。使用callback异步回调。 |
| [setCallRestriction](arkts-telephony-call-setcallrestriction-f-sys.md#setCallRestriction（系统接口）) | 设置呼叫限制状态。使用Promise异步回调。 |
| [setCallRestrictionPassword](arkts-telephony-call-setcallrestrictionpassword-f-sys.md#setCallRestrictionPassword) | 修改呼叫限制密码。使用callback异步回调。 |
| [setCallRestrictionPassword](arkts-telephony-call-setcallrestrictionpassword-f-sys.md#setCallRestrictionPassword（系统接口）) | 修改呼叫限制密码。使用Promise异步回调。 |
| [setCallTransfer](arkts-telephony-call-setcalltransfer-f-sys.md#setCallTransfer) | 设置呼叫转移信息。使用callback异步回调。 |
| [setCallTransfer](arkts-telephony-call-setcalltransfer-f-sys.md#setCallTransfer（系统接口）) | 设置呼叫转移信息。使用Promise异步回调。 |
| [setCallWaiting](arkts-telephony-call-setcallwaiting-f-sys.md#setCallWaiting) | 设置呼叫等待。使用callback异步回调。 |
| [setCallWaiting](arkts-telephony-call-setcallwaiting-f-sys.md#setCallWaiting（系统接口）) | 设置呼叫等待。使用Promise异步回调。 |
| [setDeviceDirection](arkts-telephony-call-setdevicedirection-f-sys.md#setDeviceDirection) | 设置视频通话画面显示方向为设备方向。使用Promise异步回调。 |
| [setDisplaySurface](arkts-telephony-call-setdisplaysurface-f-sys.md#setDisplaySurface) | 设置远端画面窗口。使用Promise异步回调。 |
| [setMuted](arkts-telephony-call-setmuted-f-sys.md#setMuted) | 设置通话中的静音。使用callback异步回调。 |
| [setMuted](arkts-telephony-call-setmuted-f-sys.md#setMuted（系统接口）) | 设置通话中的静音。使用Promise异步回调。 |
| [setPreviewSurface](arkts-telephony-call-setpreviewsurface-f-sys.md#setPreviewSurface) | 设置本端预览画面窗口。使用Promise异步回调。 |
| [setRttCapability](arkts-telephony-call-setrttcapability-f-sys.md#setRttCapability) | 设置rtt功能 |
| [setVoNRState](arkts-telephony-call-setvonrstate-f-sys.md#setVoNRState) | 设置NR语音的开关状态。使用callback异步回调。 |
| [setVoNRState](arkts-telephony-call-setvonrstate-f-sys.md#setVoNRState（系统接口）) | 设置NR语音的开关状态。使用Promise异步回调。 |
| [startDTMF](arkts-telephony-call-startdtmf-f-sys.md#startDTMF) | 启动双音多频。使用callback异步回调。 |
| [startDTMF](arkts-telephony-call-startdtmf-f-sys.md#startDTMF（系统接口）) | 启动双音多频。使用Promise异步回调。 |
| [startRtt](arkts-telephony-call-startrtt-f-sys.md#startRtt) | 启动rtt |
| [stopDTMF](arkts-telephony-call-stopdtmf-f-sys.md#stopDTMF) | 停止双音多频。使用callback异步回调。 |
| [stopDTMF](arkts-telephony-call-stopdtmf-f-sys.md#stopDTMF（系统接口）) | 停止双音多频。使用Promise异步回调。 |
| [stopRtt](arkts-telephony-call-stoprtt-f-sys.md#stopRtt) | 停止rtt |
| [switchCall](arkts-telephony-call-switchcall-f-sys.md#switchCall) | 切换呼叫。使用callback异步回调。 |
| [switchCall](arkts-telephony-call-switchcall-f-sys.md#switchCall（系统接口）) | 切换呼叫。使用Promise异步回调。 |
| [unHoldCall](arkts-telephony-call-unholdcall-f-sys.md#unHoldCall) | 取消保持通话。使用callback异步回调。 |
| [unHoldCall](arkts-telephony-call-unholdcall-f-sys.md#unHoldCall（系统接口）) | 取消保持通话。使用Promise异步回调。 |
| [unloadCallUI](arkts-telephony-call-unloadcallui-f-sys.md#unloadCallUI) | 卸载通话应用 |
| [updateImsCallMode](arkts-telephony-call-updateimscallmode-f-sys.md#updateImsCallMode) | 更新Ims呼叫模式。使用callback异步回调。 |
| [updateImsCallMode](arkts-telephony-call-updateimscallmode-f-sys.md#updateImsCallMode（系统接口）) | 更新Ims呼叫模式。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
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
| [CCallState](arkts-telephony-call-ccallstate-e.md) | 运营商通话状态码。 |
| [CallState](arkts-telephony-call-callstate-e.md) | 通话状态码。 |
| [TelCallState](arkts-telephony-call-telcallstate-e.md) | 通话状态码。 |

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
| [CallTransferType](arkts-telephony-call-calltransfertype-e-sys.md) | 呼叫转移类型。 |
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
| [TransferStatus](arkts-telephony-call-transferstatus-e-sys.md) | 转移状态。 |
| [VideoRequestResultType](arkts-telephony-call-videorequestresulttype-e-sys.md) | 视频通话升降级请求结果类型。 |
| [VideoStateType](arkts-telephony-call-videostatetype-e-sys.md) | 视频状态类型。 |
| [VoNRState](arkts-telephony-call-vonrstate-e-sys.md) | 5G语音开关状态。 |
| [XCallType](arkts-telephony-call-xcalltype-e-sys.md) | 表示XCall的类型。 |
<!--DelEnd-->

