# @ohos.vibrator

vibrator模块是设备马达振动的控制模块，属于SensorServiceKit。该模块提供精确控制设备马达振动的能力，支持按指定时长、预置效果、自定义配置文件、自定义振动模式等多种方式触发振动，并支持按指定模式或全部模式停止振动。 此外，模块还提供振动效果支持查询、马达设备信息查询、马达上下线状态监听等能力。 vibrator模块主要用于增强用户交互体验，通过触觉感知反馈为应用提供直观的物理反馈能力。典型使用场景包括： - 交互反馈：点击、长按、滑动、拖拽等触控操作的短振反馈，推荐使用VibratePreset预置效果以保持与系统整体振感风格一致。 - 通知提醒：消息通知、来电响铃、闹钟等场景的振动提醒。 - 游戏与多媒体：游戏操作反馈、表情包拟真效果等复杂场景的精细振动，推荐使用VibrateFromFile或VibrateFromPattern自定义振动效果。 - 多设备协同：在分布式场景下，通过指定设备ID和马达ID控制远端设备振动。 vibrator模块的核心能力围绕"启动振动"和"停止振动"两条主线展开，整体使用流程如下： 启动振动流程： 1. 若使用预置振动效果（VibratePreset），建议先调用[vibrator.isSupportEffect](arkts-sensorservice-vibrator-issupporteffect-f.md#isSupportEffect) 或[vibrator.isSupportEffectSync](arkts-sensorservice-vibrator-issupporteffectsync-f.md#isSupportEffectSync)查询当前设备是否支持该效果；若使用自定义振动配置文件（VibrateFromFile）， 建议先确认设备支持自定义振动模式（可通过[vibrator.isHdHapticSupported](arkts-sensorservice-vibrator-ishdhapticsupported-f.md#isHdHapticSupported)查询是否支持高清振动）； 若使用自定义振动模式（VibrateFromPattern），需先通过[VibratorPatternBuilder](arkts-sensorservice-vibrator-vibratorpatternbuilder-c.md#VibratorPatternBuilder)构建振动序列。 2. 调用[vibrator.startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 启动振动，需同时指定振动效果（VibrateEffect）和振动属性（VibrateAttribute）。振动属性中的usage参数决定了振动的场景类型，不同场景类型受系统振动开关管控规则不同。 停止振动流程： - 停止指定时长振动或预置效果振动：调用 [vibrator.stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md#stopVibration)（API version 9），传入对应的VibratorStopMode。 - 停止自定义振动（VibrateFromFile或VibrateFromPattern）：调用[vibrator.stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md#stopVibration)（API version 10+，无参数版本）停止所有模式振动。 - 停止所有模式振动：调用[vibrator.stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md#stopVibration)（无参数版本）或 [vibrator.stopVibrationSync](arkts-sensorservice-vibrator-stopvibrationsync-f.md#stopVibrationSync)（同步版本）。 - 停止指定设备的马达振动：调用[vibrator.stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md#stopVibration)（API version 19+，传入 VibratorInfoParam）。 多马达设备场景： 从API version 19开始，支持多设备多马达场景。可通过[vibrator.getVibratorInfoSync](arkts-sensorservice-vibrator-getvibratorinfosync-f.md#getVibratorInfoSync)查询马达信息，通过 vibrator.on监听马达上下线事件，以便动态选择合适的马达触发振动。 振动效果类型对比： | 振动效果类型 | 适用场景 | 个性化程度 | 推荐优先级 | | --- | --- | --- | --- | | VibratePreset | 交互反馈类的短振场景（点击、长按、滑动、拖拽等） | 低，使用系统预置效果 | 推荐，与系统整体振感反馈体验风格一致 | | VibrateFromFile | 复杂场景效果（表情包拟真效果、游戏场景/操作反馈） | 高，支持自定义振动配置文件 | 适用于需要精细振动的场景 | | VibrateFromPattern | 与VibrateFromFile一致，但更灵活 | 高，支持振动事件数组组合 | 适用于需要动态组合振动事件的场景 | | VibrateTime | 基础时长振动，仅控制启停 | 低，无法调节强度和频率 | 仅满足基础功能需求 |

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace vibrator--><!--Device-unnamed-declare namespace vibrator-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getEffectInfoSync](arkts-sensorservice-vibrator-geteffectinfosync-f.md#getEffectInfoSync) | 通过设备ID和马达ID获取预置振动效果信息，用于判断该预置振动效果是否受指定设备的指定马达支持。 用于多设备多马达场景下确认指定设备的指定马达是否支持某个预置振动效果，不传param时默认查询本地设备。适用于触发振动前确认效果可用性，避免在不支持的设备或马达上触发振动效果不佳。返回EffectInfo对象， isEffectSupported字段指示是否支持该预置振动效果：返回true时可直接用于startVibration (#vibratorstartvibration9)，返回false时使用该effectId触发振动可能效果不 佳。 |
| [getVibratorInfoSync](arkts-sensorservice-vibrator-getvibratorinfosync-f.md#getVibratorInfoSync) | 查询一个或所有设备的马达信息列表。适用于在触发振动前查询设备马达能力和多马达设备的马达ID，以便选择合适的马达触发振动。 不传param时查询所有设备马达信息；传入VibratorInfoParam可查询指定设备或马达。返回VibratorInfo数组，包含deviceId、vibratorId、deviceName、 isHdHapticSupported、isLocalVibrator等属性，可用于startVibration (#vibratorstartvibration9)和stopVibration (# vibratorstopvibration19)中指定马达和设备。 |
| [isHdHapticSupported](arkts-sensorservice-vibrator-ishdhapticsupported-f.md#isHdHapticSupported) | 查询当前设备是否支持高清振动。 适用于在触发高清振动前确认设备是否支持，避免在不支持的设备上调用VibrateFromFile或VibrateFromPattern类型振动导致振动效果不佳或返回错误码801。返回true表示设备支持高清振动，可使用 VibrateFromFile和VibrateFromPattern类型触发振动；返回false表示不支持，使用自定义振动类型将返回错误码801或效果不佳。 |
| [isSupportEffect](arkts-sensorservice-vibrator-issupporteffect-f.md#isSupportEffect) | 查询当前设备是否支持传入的预置振动效果effectId。使用callback异步回调。 当开发者需要在触发预置振动前确认当前设备是否支持指定的振动效果时使用此接口。由于不同设备可能预置不同的振动效果，建议在使用 [vibrator.startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 的VibratePreset类型前先调用此接口查询，避免在不支持的设备上触发振动效果不佳。调用成功后，通过callback返回boolean结果：返回true表示设备支持该effectId，可直接用于startVibration； 返回false表示不支持，此时使用该effectId触发振动可能效果不佳或无法振动。 |
| [isSupportEffect](arkts-sensorservice-vibrator-issupporteffect-f.md#isSupportEffect) | 查询当前设备是否支持传入的预置振动效果effectId。使用promise异步回调。 当开发者需要在触发预置振动前确认当前设备是否支持指定的振动效果时使用此接口。与callback版本功能一致，开发者可根据异步回调风格偏好选择使用。调用成功时Promise resolve返回boolean结果：返回true表示设备 支持该effectId；返回false表示不支持，此时使用该effectId触发振动可能效果不佳或无法振动。 |
| [isSupportEffectSync](arkts-sensorservice-vibrator-issupporteffectsync-f.md#isSupportEffectSync) | 查询当前设备是否支持预设的振动效果。此接口为同步接口，会阻塞主线程直到查询完成，容易影响UI交互，需谨慎使用。 当开发者需要在触发预置振动前立即确认当前设备是否支持指定的振动效果时使用此接口。适用于对实时性要求高且查询逻辑简单的场景。返回boolean结果：返回true表示设备支持该effectId，可用于 [startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) ；返回false表示不支持，使用该effectId触发振动可能效果不佳或无法振动。与异步版本 [vibrator.isSupportEffect](arkts-sensorservice-vibrator-issupporteffect-f.md#isSupportEffect)相比，本接 口为同步接口，直接返回结果无需回调，但会阻塞主线程。建议在非UI线程中使用，或在UI线程中优先使用异步版本以避免影响交互响应。 |
| [offVibratorStateChange](arkts-sensorservice-vibrator-offvibratorstatechange-f.md#offVibratorStateChange) | Unregister a callback function for vibrator plugin or unplug events. |
| off_vibratorStateChange | 注销马达上线或下线事件的回调函数。 当开发者不再需要监听马达上下线状态变化时使用此接口注销回调。传入callback时注销指定回调；不传callback时注销该类型下所有已注册的回调。注销成功后，不再触发对应的回调函数。若传入的callback未注册过，注销操作无效 但不会报错。需先通过vibrator.on注册回调后才能注销。同一type重复注册同一callback不会覆盖，需先off再on。 |
| [onVibratorStateChange](arkts-sensorservice-vibrator-onvibratorstatechange-f.md#onVibratorStateChange) | Register a callback function to be called when a vibrator plugin or unplug event occurs. |
| on_vibratorStateChange | 注册马达上线或下线事件的回调函数。当马达设备上线或下线时触发回调。 当开发者需要实时感知马达设备的上下线状态变化时使用此接口。适用于分布式多设备场景中动态获取马达设备信息，以便在马达上线时及时触发振动或在下线时停止振动。注册成功后，当马达设备上线或下线时，系统将回调 VibratorStatusEvent对象，包含设备ID、马达数量、上下线状态等信息。回调中获取的deviceId可用于 [startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 和[stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md#stopVibration)等接口指定目标设备。 注册回调后，需在合适的时机调用 vibrator.off注销回调，避免内存泄 露。同一type重复注册同一callback不会覆盖，需先off再on。 |
| [startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) | 根据指定的振动效果和振动属性触发马达振动，使用callback异步回调。 适用于为用户交互提供触觉反馈、为通知/闹钟等事件提供振动提醒，或在游戏、多媒体等场景中提供沉浸式振动体验。调用成功后，设备马达将按指定效果和属性开始振动；若同一马达已有正在进行的振动，新请求将按系统优先级规则处理。同功能还提供 Promise版本vibrator.startVibration (#vibratorstartvibration9-1)，开发者可根据回调风格偏好选择。 |
| [startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) | 根据指定的振动效果和振动属性触发马达振动，使用promise异步回调。 适用于交互触觉反馈、事件振动提醒或游戏、多媒体等沉浸式振动场景。调用成功时Promise resolve无返回值；调用失败时Promise reject返回错误对象。若同一马达已有振动正在进行，新请求按系统优先级规则处理。同功能还 提供callback版本vibrator.startVibration (#vibratorstartvibration9)，开发者可根据回调风格偏好选择。 |
| [stop](arkts-sensorservice-vibrator-stop-f.md#stop) | 按照指定模式停止马达的振动。 |
| [stop](arkts-sensorservice-vibrator-stop-f.md#stop) | 按照指定模式停止马达的振动。 |
| [stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md#stopVibration) | 按照指定模式停止马达的振动。调用成功后马达停止对应模式的振动。使用promise异步回调。 用于停止VibrateTime触发的指定时长振动或VibratePreset触发的预置振动。调用成功返回Promise resolve，失败返回错误对象；若无对应振动正在进行，仍返回成功。此接口无法停止自定义振动（ VibrateFromFile和VibrateFromPattern），需使用vibrator.stopVibration (#vibratorstopvibration10-1)。stopMode须与启动振动时的 VibrateEffect类型对应，否则停止无效：VibrateTime对应VIBRATOR_STOP_MODE_TIME，VibratePreset对应VIBRATOR_STOP_MODE_PRESET。 |
| [stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md#stopVibration) | 按照指定模式停止马达振动。调用成功后马达停止对应模式的振动。使用callback异步回调。 stopMode需与启动振动时的VibrateEffect类型对应：VIBRATOR_STOP_MODE_TIME用于停止VibrateTime类型振动，VIBRATOR_STOP_MODE_PRESET用于停止 VibratePreset类型振动，否则停止操作可能无效。调用成功后指定模式振动停止，若无对应振动正在进行也会成功返回。此接口无法停止自定义振动（VibrateFromFile和VibrateFromPattern），如需停止自定 义振动或所有模式振动，请使用vibrator.stopVibration (#vibratorstopvibration10)。 |
| [stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md#stopVibration) | 停止所有模式的马达振动。调用成功后马达停止振动。使用callback异步回调。 用于停止设备上所有类型的振动（包括VibrateTime、VibratePreset、VibrateFromFile、VibrateFromPattern），适用于应用退出、页面切换等需立即终止所有振动的场景。与 vibrator.stopVibration (#vibratorstopvibration9)（需传入stopMode）不同，本接口无需指定停止模式，可停止包括自定义振动在内的所有振动。 |
| [stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md#stopVibration) | 停止所有模式的马达振动。调用成功后马达停止振动。使用promise异步回调。 用于停止设备上所有类型的振动（包括VibrateTime、VibratePreset、VibrateFromFile、VibrateFromPattern），适用于应用退出、页面切换等需立即终止所有振动的场景。调用成功返回 Promise resolve，失败返回错误对象。与vibrator.stopVibration (#vibratorstopvibration9-1)（需传入stopMode）不同，本接口无需指定停止模式，可停止包括自定义振动在 内的所有振动。 |
| [stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md#stopVibration) | 停止指定设备马达振动。不传参默认停止本地设备所有马达的振动。使用promise异步回调。 用于多设备多马达场景下停止指定设备或指定马达的振动。不传参时默认停止本地设备全部马达振动；传入VibratorInfoParam可指定远程设备的特定马达。调用成功返回Promise resolve，失败返回错误对象。与 vibrator.stopVibration (#vibratorstopvibration10-1)（无参数版本）相比，本接口新增VibratorInfoParam可选参数，支持精确控制停止范围，前者仅能停止本地设备所有马达振动 。 |
| [stopVibrationSync](arkts-sensorservice-vibrator-stopvibrationsync-f.md#stopVibrationSync) | 停止任何形式的马达振动。调用成功后马达停止振动。此接口为同步接口，会阻塞主线程直到振动停止操作完成，容易影响UI交互，需谨慎使用。 当开发者需要立即停止所有振动且不关心异步回调结果时使用此接口。适用于对实时性要求极高的场景（如紧急中断振动）。调用成功后，设备上所有正在进行的马达振动立即停止。调用失败时会抛出异常，需使用try catch捕获。与异步版本 [vibrator.stopVibration](arkts-sensorservice-vibrator-stopvibration-f.md#stopVibration)相比，本接口为同步接口，直接返回结果无需回调，但会阻塞主线程。建议在非UI线程中使用，或在UI线程中优先使用异步版本以 避免影响交互响应。 |
| [vibrate](arkts-sensorservice-vibrator-vibrate-f.md#vibrate) | 按照指定持续时间触发马达振动。 |
| [vibrate](arkts-sensorservice-vibrator-vibrate-f.md#vibrate) | 按照指定持续时间触发马达振动。 |
| [vibrate](arkts-sensorservice-vibrator-vibrate-f.md#vibrate) | 按照预置振动效果触发马达振动。 |
| [vibrate](arkts-sensorservice-vibrator-vibrate-f.md#vibrate) | 按照指定振动效果触发马达振动。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [VibratorPatternBuilder](arkts-sensorservice-vibrator-vibratorpatternbuilder-c.md) | 提供添加长振、短振事件和生成VibratorPattern对象的方法。使用流程：先通过 [addContinuousEvent](arkts-sensorservice-vibrator-vibratorpatternbuilder-c.md#addContinuousEvent)或 [addTransientEvent](arkts-sensorservice-vibrator-vibratorpatternbuilder-c.md#addTransientEvent)添加振动事件，再通过 [build](arkts-sensorservice-vibrator-vibratorpatternbuilder-c.md#build)方法生成VibratorPattern对象，最后将该对象作为 [VibrateFromPattern](arkts-sensorservice-vibrator-vibratefrompattern-i.md#VibrateFromPattern)的pattern参数传入 [vibrator.startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 接口触发振动。 当开发者需要通过灵活组合振动事件（长振和短振）构建自定义振动序列时使用此接口。适用于需要动态排列振动事件的交互反馈场景（如表情包拟真效果、游戏场景反馈），相比VibrateFromFile以文件描述符方式传递振动事件， VibratorPatternBuilder以振动事件数组形式传递，支持更灵活的振动事件排列组合。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ContinuousParam](arkts-sensorservice-vibrator-continuousparam-i.md) | 连续振动参数。用于[VibratorPatternBuilder.addContinuousEvent](arkts-sensorservice-vibrator-vibratorpatternbuilder-c.md#addContinuousEvent)的 options参数，指定长振事件的振动强度、频率、振动调节曲线和通道编号。 |
| [EffectInfo](arkts-sensorservice-vibrator-effectinfo-i.md) | 查询的预置效果信息。通过[vibrator.getEffectInfoSync](arkts-sensorservice-vibrator-geteffectinfosync-f.md#getEffectInfoSync)返回此对象，用于判断预置振动效果是否受指定设备的指定马达支持。 |
| [HapticFileDescriptor](arkts-sensorservice-vibrator-hapticfiledescriptor-i.md) | 自定义振动配置文件的描述符，必须确认资源文件可用，其参数可通过fileIo.open从 沙箱路径获取或者通过 [getRawFd](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getRawFd) 从HAP资源获取。使用场景：振动序列被存储在一个文件中，需要根据偏移量和长度进行振动，振动序列存储格式，请参考 [振动效果说明](../../../device/sensor/vibrator-guidelines.md#振动效果说明)。 使用时需注意以下问题： - 振动结束后建议及时关闭文件描述符，避免资源泄露。使用getRawFd获取的文件描述符需通过closeRawFd关闭，使用fileIo.open获取的需通过fileIo.close关闭。 |
| [TransientParam](arkts-sensorservice-vibrator-transientparam-i.md) | 瞬态振动参数。用于[VibratorPatternBuilder.addTransientEvent](arkts-sensorservice-vibrator-vibratorpatternbuilder-c.md#addTransientEvent)的 options参数，指定短振事件的振动强度、频率和通道编号。 |
| [VibrateAttribute](arkts-sensorservice-vibrator-vibrateattribute-i.md) | 马达振动属性。用于 [startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 接口的attribute参数，指定马达ID、设备ID和振动使用场景。 |
| [VibrateFromFile](arkts-sensorservice-vibrator-vibratefromfile-i.md) | 自定义振动类型。仅部分设备支持高清振动的设备可用，当设备不支持此振动类型时，返回错误码801。当调用 [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 或 [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 时，[VibrateEffect&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-vibrateeffect-t.md#VibrateEffect)参数的值可以为VibrateFromFile，表示触发自定义振动类型。适用于匹配复杂场景效果的交互反馈（如表情 包触发的拟真效果、游戏场景/操作反馈）。 适用于需要按照振动配置文件定制精细振动效果的交互反馈场景。建议先通过[vibrator.isHdHapticSupported](arkts-sensorservice-vibrator-ishdhapticsupported-f.md#isHdHapticSupported)确认设备是否支持高清振动。 |
| [VibrateFromPattern](arkts-sensorservice-vibrator-vibratefrompattern-i.md) | 自定义振动效果触发马达振动。适用于需要灵活组合振动事件的交互反馈场景（如表情包拟真效果、游戏场景/操作反馈）。与VibrateFromFile相比，VibrateFromFile是面向文件中提前定制好的效果，将振动事件以文件描述符 形式传递；VibrateFromPattern提供更加灵活的振动事件排列组合，将振动事件以振动事件数组的形式传递。 |
| [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md) | 预置振动类型。当调用 [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 或 [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 时，[VibrateEffect&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-vibrateeffect-t.md#VibrateEffect)参数的值可以为VibratePreset，表示触发预置振动类型。适用于交互反馈类的短振场景（如点击、长按、滑动 、拖拽等），为确保与系统整体振感反馈体验风格一致，推荐使用此类型。 |
| [VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md) | 指定时长振动类型。仅对振动时长进行启动或停止控制，满足基础功能，无法对振动强度、频率等维度进行个性化设置。 |
| [VibratorCurvePoint](arkts-sensorservice-vibrator-vibratorcurvepoint-i.md) | 相对事件振动强度的增益。用于[ContinuousParam](arkts-sensorservice-vibrator-continuousparam-i.md#ContinuousParam)和[VibratorEvent](arkts-sensorservice-vibrator-vibratorevent-i.md#VibratorEvent)的 points字段，精细控制振动强度和频率的变化趋势。 |
| [VibratorEvent](arkts-sensorservice-vibrator-vibratorevent-i.md) | 振动事件。用于[VibratorPattern](arkts-sensorservice-vibrator-vibratorpattern-i.md#VibratorPattern)的events数组中定义具体的振动事件。 |
| [VibratorInfo](arkts-sensorservice-vibrator-vibratorinfo-i.md) | 表示查询的马达信息。通过[vibrator.getVibratorInfoSync](arkts-sensorservice-vibrator-getvibratorinfosync-f.md#getVibratorInfoSync)返回此对象，用于获取设备马达能力和选择合适的马达触发振动。 |
| [VibratorInfoParam](arkts-sensorservice-vibrator-vibratorinfoparam-i.md) | 设备上马达的参数。用于指定需要查询或控制的设备和马达信息。默认情况下，VibratorInfoParam默认为查询或控制本地全部马达。 |
| [VibratorPattern](arkts-sensorservice-vibrator-vibratorpattern-i.md) | 马达振动序列，每个events代表一个振动事件。通过[VibratorPatternBuilder.build](arkts-sensorservice-vibrator-vibratorpatternbuilder-c.md#build)方法生成，作为 [VibrateFromPattern](arkts-sensorservice-vibrator-vibratefrompattern-i.md#VibrateFromPattern)的pattern参数传入 [startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 接口触发振动。 |
| [VibratorStatusEvent](arkts-sensorservice-vibrator-vibratorstatusevent-i.md) | 振动设备上线、下线状态事件信息。当马达设备上线或下线时，通过vibrator.on回调传递此对象。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [VibrateAttribute](arkts-sensorservice-vibrator-vibrateattribute-i-sys.md) | 马达振动属性。用于 [startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 接口的attribute参数，指定马达ID、设备ID和振动使用场景。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EffectId](arkts-sensorservice-vibrator-effectid-e.md) | 预置的振动效果。在调用 [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 或[vibrator.stopVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-stopvibration-f.md#stopVibration)接口下发 [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md#VibratePreset)形式振动的时候需要使用此参数类型。此参数值种类多样，'haptic.clock.timer'为其中一种。 [HapticFeedback&lt;sup&gt;12+&lt;/sup&gt;](arkts-sensorservice-vibrator-hapticfeedback-e.md#HapticFeedback)展示了几种常用的EffectId值。 |
| [HapticFeedback](arkts-sensorservice-vibrator-hapticfeedback-e.md) | 简单而通用的振动效果。根据各设备的马达器件不同，同一振动效果的频率会有差异，但效果的频率趋向是统一的。这几种振动效果是EffectId参数的具体值，使用方法参考 [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 或[vibrator.stopVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-stopvibration-f.md#stopVibration)接口下发 [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md#VibratePreset)形式振动的示例代码。 |
| [VibratorEventType](arkts-sensorservice-vibrator-vibratoreventtype-e.md) | 振动事件类型。用于[VibratorEvent](arkts-sensorservice-vibrator-vibratorevent-i.md#VibratorEvent)的eventType字段指定振动事件的类型。 |
| [VibratorStopMode](arkts-sensorservice-vibrator-vibratorstopmode-e.md) | 停止振动的模式。在调用 [vibrator.stopVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-stopvibration-f.md#stopVibration) 或[vibrator.stopVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-stopvibration-f.md#stopVibration)接口时，需要使用此参数类型指定停止的振 动模式。停止模式和[VibrateEffect&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-vibrateeffect-t.md#VibrateEffect)中下发的模式为对应关系：VIBRATOR_STOP_MODE_TIME对应VibrateTime 类型，VIBRATOR_STOP_MODE_PRESET对应VibratePreset类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [Usage](arkts-sensorservice-vibrator-usage-t.md) | 振动使用场景。不同usage值对应不同的系统振动开关管控规则，开发者需根据实际业务场景选择合适的usage值。 &lt;!--RP1End--&gt; |
| [VibrateEffect](arkts-sensorservice-vibrator-vibrateeffect-t.md) | 马达振动效果，支持以下四种：在调用 [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 或 [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md#startVibration) 接口时，此参数的四种类型表示以四种不同的形式触发振动。 |

