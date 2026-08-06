# SoundPool

音频池提供了系统声音的加载、播放、音量设置、循环设置、停止播放和资源卸载等功能，在调用SoundPool的接口前，需要先通过 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 创建实例。 > **说明：** > > - 在使用SoundPool实例的方法时，建议开发者注册相关回调，主动获取当前状态变化。 > > - [on('loadComplete')]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_：监听资源加载完成。建议开发者监听此回调以确 > 保音频在加载完成后进行播放。 > > - > [on('playFinishedWithStreamId')]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_：监听播 > 放完成，同时返回播放结束的音频的streamId。 > > - [on('playFinished')]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_：监听播放完成。 > > - [on('error')]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_：监听错误事件。 > > - [on('errorOccurred')]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_：监听错误事件，同时返回 > [errorInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_。 > > - SoundPool目前不支持后台播放、设置音频打断等音频焦点策略和跳过音频头尾的静音帧。SoundPool低时延播放可参考 > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export declare interface SoundPool--><!--Device-unnamed-export declare interface SoundPool-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## load

ArkTS-Dyn:
```TypeScript
load(uri: string, callback: AsyncCallback<number>): void
```

ArkTS-Sta:
```TypeScript
load(uri: string, callback: AsyncCallback<int>): void
```

加载音频资源。使用callback异步回调。 通过callback异步回调获取资源ID，入参URL通过获取文件fd生成以"fd://"开头的文件描述字符串。 该方法不支持加载rawfile目录资源，需要通过 [load(fd: number, offset: number, length: number, callback: AsyncCallback\_\_\_ESCAPED\_UNDERSCORE\_DESC\_\_\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_): void]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 或者 [load(fd: number, offset: number, length: number): Promise\_\_\_ESCAPED\_UNDERSCORE\_DESC\_\_\_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 实现。 > **说明：** > > - 将资源句柄（fd）或加载路径描述（uri）传递给音频池播放器之后，请不要通过该资源句柄或加载路径描述做其他读写操作，包括但不限于将同一个资源句柄或加载路径描述传递给多个音频池播放器。 > > - 同一时间通过同一个资源句柄或加载路径描述读写文件时存在竞争关系，将导致播放异常。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-load(uri: string, callback: AsyncCallback<int>): void--><!--Device-SoundPool-load(uri: string, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 音频文件的加载路径描述，一般以"fd://"开头的文件描述。 |
| callback | ArkTS-Dyn: \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_2\_\_\_ArkTS-Sta：\_\_\_MD\_LINK\_USD\_1\_\_\_&lt;int&gt; | 是 | 异步音频资源加载返回的资源id，有效值大于0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400103](../../errorcode-media.md#5400103-出现io错误) | I/O error. Return by callback. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## load

ArkTS-Dyn:
```TypeScript
load(uri: string): Promise<number>
```

ArkTS-Sta:
```TypeScript
load(uri: string): Promise<int>
```

加载音频资源。使用Promise异步回调。 通过Promise异步回调获取资源ID，入参URL通过获取文件fd生成以"fd://"开头的文件描述字符串。 该方法不支持加载rawfile目录资源，需要通过 [load(fd: number, offset: number, length: number, callback: AsyncCallback\_\_\_ESCAPED\_UNDERSCORE\_DESC\_\_\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_): void]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 或者 [load(fd: number, offset: number, length: number): Promise\_\_\_ESCAPED\_UNDERSCORE\_DESC\_\_\_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 实现。 > **说明：** > > - 将资源句柄（fd）或加载路径描述（uri）传递给音频池播放器之后，请不要通过该资源句柄或加载路径描述做其他读写操作，包括但不限于将同一个资源句柄或加载路径描述传递给多个音频池播放器。 > > - 同一时间通过同一个资源句柄或加载路径描述读写文件时存在竞争关系，将导致播放异常。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-load(uri: string): Promise<int>--><!--Device-SoundPool-load(uri: string): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 音频文件的加载路径描述，一般以"fd://"开头的文件描述。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;int&gt; | Promise对象，返回资源的id，有效值大于0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../../errorcode-media.md#5400103-出现io错误) | I/O error. Return by promise. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## load

ArkTS-Dyn:
```TypeScript
load(fd: number, offset: number, length: number, callback: AsyncCallback<number>): void
```

ArkTS-Sta:
```TypeScript
load(fd: int, offset: long, length: long, callback: AsyncCallback<int>): void
```

加载音频资源。使用callback异步回调。 通过callback异步回调获取资源ID，入参可手动传入资源信息或通过读取应用内置资源自动获取。 > **说明：** > > - 将资源句柄（fd）或加载路径描述（uri）传递给音频池播放器之后，请不要通过该资源句柄或加载路径描述做其他读写操作，包括但不限于将同一个资源句柄或加载路径描述传递给多个音频池播放器。 > > - 同一时间通过同一个资源句柄或加载路径描述读写文件时存在竞争关系，将导致播放异常。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-load(fd: int, offset: long, length: long, callback: AsyncCallback<int>): void--><!--Device-SoundPool-load(fd: int, offset: long, length: long, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 资源句柄，通过\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_获取。 |
| offset | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 资源偏移量，需要基于预置资源的信息输入，非法值会造成音视频资源解析错误。 |
| length | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 资源长度，需要基于预置资源的信息输入，非法值会造成音视频资源解析错误。 |
| callback | ArkTS-Dyn: \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_2\_\_\_ArkTS-Sta：\_\_\_MD\_LINK\_USD\_1\_\_\_&lt;int&gt; | 是 | 获取回调的soundID，有效值大于0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400103](../../errorcode-media.md#5400103-出现io错误) | I/O error. Return by callback. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## load

ArkTS-Dyn:
```TypeScript
load(fd: number, offset: number, length: number): Promise<number>
```

ArkTS-Sta:
```TypeScript
load(fd: int, offset: long, length: long): Promise<int>
```

加载音频资源。使用Promise异步回调。 通过Promise异步回调获取资源ID，入参可手动传入资源信息或通过读取应用内置资源自动获取。 > **说明：** > > - 将资源句柄（fd）或加载路径描述（uri）传递给音频池播放器之后，请不要通过该资源句柄或加载路径描述做其他读写操作，包括但不限于将同一个资源句柄或加载路径描述传递给多个音频池播放器。 > > - 同一时间通过同一个资源句柄或加载路径描述读写文件时存在竞争关系，将导致播放异常。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-load(fd: int, offset: long, length: long): Promise<int>--><!--Device-SoundPool-load(fd: int, offset: long, length: long): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 资源句柄，通过\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_获取。 |
| offset | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 资源偏移量，需要基于预置资源的信息输入，非法值会造成音视频资源解析错误。 |
| length | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 资源长度，需要基于预置资源的信息输入，非法值会造成音视频资源解析错误。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;int&gt; | Promise对象，返回soundID，有效值大于0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../../errorcode-media.md#5400103-出现io错误) | I/O error. Return by promise. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## off

```TypeScript
off(type: 'loadComplete'): void
```

取消监听资源的加载完成。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-SoundPool-off(type: 'loadComplete'): void--><!--Device-SoundPool-off(type: 'loadComplete'): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'loadComplete' | 是 | 取消注册的事件：'loadComplete'。 |

## off

```TypeScript
off(type: 'playFinished'): void
```

取消监听音频池资源播放完成。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-SoundPool-off(type: 'playFinished'): void--><!--Device-SoundPool-off(type: 'playFinished'): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playFinished' | 是 | 取消注册的事件：'playFinished'。 |

## off

```TypeScript
off(type: 'error'): void
```

取消监听音频池的错误事件。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-SoundPool-off(type: 'error'): void--><!--Device-SoundPool-off(type: 'error'): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 错误事件回调类型，取消注册的事件：'error'。 |

## off

```TypeScript
off(type: 'playFinishedWithStreamId'): void
```

取消监听音频池资源播放完成。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

<!--Device-SoundPool-off(type: 'playFinishedWithStreamId'): void--><!--Device-SoundPool-off(type: 'playFinishedWithStreamId'): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playFinishedWithStreamId' | 是 | 取消注册的事件：'playFinishedWithStreamId'。 |

## off('errorOccurred')

```TypeScript
off(type: 'errorOccurred', callback?:Callback<ErrorInfo>): void
```

取消监听音频池的错误事件。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-SoundPool-off(type: 'errorOccurred', callback?:Callback<ErrorInfo>): void--><!--Device-SoundPool-off(type: 'errorOccurred', callback?:Callback<ErrorInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'errorOccurred' | 是 | 事件回调类型，取消注册的事件为'errorOccurred'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 否 | 错误事件回调方法。在使用播放器的过程中发生错误时，提供错误信息[ErrorInfo]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_，不设置callback时不提供相关信息。 |

## offError

```TypeScript
offError(): void
```

Unsubscribes from error events of this **SoundPool** instance.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SoundPool-offError(): void--><!--Device-SoundPool-offError(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## offErrorOccurred

```TypeScript
offErrorOccurred(callback?:Callback<ErrorInfo>): void
```

Unsubscribes from errorOccurred events of this **SoundPool** instance.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SoundPool-offErrorOccurred(callback?:Callback<ErrorInfo>): void--><!--Device-SoundPool-offErrorOccurred(callback?:Callback<ErrorInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 否 | Callback used to listen for soundpool errorOccurred events. |

## offLoadComplete

```TypeScript
offLoadComplete(): void
```

Unsubscribes from events indicating that a sound finishes loading.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SoundPool-offLoadComplete(): void--><!--Device-SoundPool-offLoadComplete(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## offPlayFinished

```TypeScript
offPlayFinished(): void
```

Unsubscribes from events indicating that a sound finishes playing.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SoundPool-offPlayFinished(): void--><!--Device-SoundPool-offPlayFinished(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## offPlayFinishedWithStreamId

```TypeScript
offPlayFinishedWithStreamId(): void
```

Unsubscribes from events indicating that a sound finishes playing.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SoundPool-offPlayFinishedWithStreamId(): void--><!--Device-SoundPool-offPlayFinishedWithStreamId(): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

## on('loadComplete')

```TypeScript
on(type: 'loadComplete', callback: Callback<int>): void
```

音频池资源加载完成监听。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-SoundPool-on(type: 'loadComplete', callback: Callback<int>): void--><!--Device-SoundPool-on(type: 'loadComplete', callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'loadComplete' | 是 | 支持的事件：'loadComplete'，对应的ID加载完成会触发此回调。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; | 是 | 回调函数，返回对应资源加载完成的资源ID。 |

## on('playFinished')

```TypeScript
on(type: 'playFinished', callback: Callback<void>): void
```

音频池资源播放完成监听。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-SoundPool-on(type: 'playFinished', callback: Callback<void>): void--><!--Device-SoundPool-on(type: 'playFinished', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playFinished' | 是 | 支持的事件：'playFinished'，音频流播放完成会触发此回调。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 异步'playFinished'的回调方法。 |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

监听\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_的错误事件，该事件仅用于错误提示。使 用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-SoundPool-on(type: 'error', callback: ErrorCallback): void--><!--Device-SoundPool-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 错误事件回调类型，支持的事件：'error'，用户操作和系统都会触发此事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 错误事件回调方法：使用播放器的过程中发生错误，会提供错误码ID和错误信息。 |

## on('playFinishedWithStreamId')

```TypeScript
on(type: 'playFinishedWithStreamId', callback: Callback<int>): void
```

音频池资源播放完成监听，同时返回播放结束的音频的streamId。使用callback异步回调。 当仅单独注册[on('playFinished')]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_事件回调或者 [on('playFinishedWithStreamId')]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_事件回调 时，当音频播放完成的时候，都会触发注册的回调。 当同时注册[on('playFinished')]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_事件回调和 [on('playFinishedWithStreamId')]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_事件回调 时，当音频播放完成的时候，仅会触发'playFinishedWithStreamId'事件回调，不会触发'playFinished'事件回调。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

<!--Device-SoundPool-on(type: 'playFinishedWithStreamId', callback: Callback<int>): void--><!--Device-SoundPool-on(type: 'playFinishedWithStreamId', callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playFinishedWithStreamId' | 是 | 支持的事件：'playFinishedWithStreamId'，音频流播放完成会触发此回调，并返回播放完成的音频的streamId。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; | 是 | 回调函数，返回播放完成的音频的streamId。 |

## on('errorOccurred')

```TypeScript
on(type:'errorOccurred', callback:Callback<ErrorInfo>): void
```

监听\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_的错误事件，并返回包含错误码、错误发 生阶段、资源ID和音频流ID的[ErrorInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。使用callback异步回调。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

<!--Device-SoundPool-on(type:'errorOccurred', callback:Callback<ErrorInfo>): void--><!--Device-SoundPool-on(type:'errorOccurred', callback:Callback<ErrorInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'errorOccurred' | 是 | 事件回调类型，支持的事件为'errorOccurred'，当用户或系统操作导致错误，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | 回调函数，返回错误事件回调方法。在使用播放器的过程中发生错误时，提供错误信息[ErrorInfo]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

## onError

```TypeScript
onError(callback: ErrorCallback): void
```

Subscribes to error events of this **SoundPool** instance. This event is used only for error prompt. This event can be triggered by both user operations and the system.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SoundPool-onError(callback: ErrorCallback): void--><!--Device-SoundPool-onError(callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback used to return the error code ID and error message. |

## onErrorOccurred

```TypeScript
onErrorOccurred(callback:Callback<ErrorInfo>): void
```

Subscribes to errorOccurred events of this **SoundPool** instance.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SoundPool-onErrorOccurred(callback:Callback<ErrorInfo>): void--><!--Device-SoundPool-onErrorOccurred(callback:Callback<ErrorInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | Callback used to listen for soundpool errorOccurred events. |

## onLoadComplete

```TypeScript
onLoadComplete(callback: Callback<int>): void
```

Subscribes to events indicating that a sound finishes loading. This event is triggered when a sound is loaded.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SoundPool-onLoadComplete(callback: Callback<int>): void--><!--Device-SoundPool-onLoadComplete(callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; | 是 | ID of the sound that has been loaded. |

## onPlayFinished

```TypeScript
onPlayFinished(callback: Callback<void>): void
```

Subscribes to events indicating that a sound finishes playing. This event is triggered when a sound finishes playing.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SoundPool-onPlayFinished(callback: Callback<void>): void--><!--Device-SoundPool-onPlayFinished(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | Callback used to return the result. |

## onPlayFinishedWithStreamId

```TypeScript
onPlayFinishedWithStreamId(callback: Callback<int>): void
```

Subscribes to events indicating the completion of audio playback and returns the stream ID of the audio that finishes playing. When only onPlayFinished or onPlayFinishedWithStreamId is subscribed to, the registered callback is triggered when the audio playback is complete. When both onPlayFinished and onPlayFinishedWithStreamId are subscribed to, the 'playFinishedWithStreamId' callback is triggered, but the 'playFinished' callback is not triggered, when the audio playback is complete.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SoundPool-onPlayFinishedWithStreamId(callback: Callback<int>): void--><!--Device-SoundPool-onPlayFinishedWithStreamId(callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; | 是 | Callback used to return the result. Stream ID of the audio that finishes playing. |

## play

ArkTS-Dyn:
```TypeScript
play(soundID: number, params: PlayParameters, callback: AsyncCallback<number>): void
```

ArkTS-Sta:
```TypeScript
play(soundID: int, params: PlayParameters, callback: AsyncCallback<int>): void
```

播放音频资源，获取音频流streamID。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-play(soundID: int, params: PlayParameters, callback: AsyncCallback<int>): void--><!--Device-SoundPool-play(soundID: int, params: PlayParameters, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| soundID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 资源ID，通过load方法获取。 |
| params | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | play播放相关参数的设置。 |
| callback | ArkTS-Dyn: \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_2\_\_\_ArkTS-Sta：\_\_\_MD\_LINK\_USD\_1\_\_\_&lt;int&gt; | 是 | 获取回调的音频流ID，有效值大于0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. Return by callback. |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## play

ArkTS-Dyn:
```TypeScript
play(soundID: number, callback: AsyncCallback<number>): void
```

ArkTS-Sta:
```TypeScript
play(soundID: int, callback: AsyncCallback<int>): void
```

使用默认参数播放音频资源，获取音频流streamID。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-play(soundID: int, callback: AsyncCallback<int>): void--><!--Device-SoundPool-play(soundID: int, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| soundID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 资源ID，通过load方法获取。 |
| callback | ArkTS-Dyn: \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_2\_\_\_ArkTS-Sta：\_\_\_MD\_LINK\_USD\_1\_\_\_&lt;int&gt; | 是 | 获取回调的音频流ID，有效值大于0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. Return by callback. |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## play

ArkTS-Dyn:
```TypeScript
play(soundID: number, params?: PlayParameters): Promise<number>
```

ArkTS-Sta:
```TypeScript
play(soundID: int, params?: PlayParameters): Promise<int>
```

播放音频资源，获取音频流streamID。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-play(soundID: int, params?: PlayParameters): Promise<int>--><!--Device-SoundPool-play(soundID: int, params?: PlayParameters): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| soundID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 资源ID，通过load方法获取。 |
| params | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | play播放相关参数的设置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;int&gt; | Promise对象，返回音频流ID，有效值大于0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. Return by promise. |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放音频池实例。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-release(callback: AsyncCallback<void>): void--><!--Device-SoundPool-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当音频池release方法回调成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## release

```TypeScript
release(): Promise<void>
```

释放音频池实例。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-release(): Promise<void>--><!--Device-SoundPool-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## setInterruptMode

```TypeScript
setInterruptMode(interruptMode: media.SoundInterruptMode): void
```

设置同一ID音频在播放时的打断模式。创建soundPool之后，该接口仅在首次调用soundPool的Play函数之前设置有效，期间可多次设置，否则将默认使用 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_，即对同一ID的音频，如果前者尚未播放完成，后者在播放前会先打断前 者的播放。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SoundPool-setInterruptMode(interruptMode: media.SoundInterruptMode): void--><!--Device-SoundPool-setInterruptMode(interruptMode: media.SoundInterruptMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| interruptMode | media.SoundInterruptMode | 是 | 同一ID音频在播放时的打断模式，通过media.SoundInterruptMode枚举获取。 |

## setLoop

ArkTS-Dyn:
```TypeScript
setLoop(streamID: number, loop: number, callback: AsyncCallback<void>): void
```

ArkTS-Sta:
```TypeScript
setLoop(streamID: int, loop: int, callback: AsyncCallback<void>): void
```

设置循环模式。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-setLoop(streamID: int, loop: int, callback: AsyncCallback<void>): void--><!--Device-SoundPool-setLoop(streamID: int, loop: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 音频流ID，通过play方法获取。 |
| loop | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 设置循环次数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当loop≥0时，实际播放次数为loop+1。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 当loop＜0时，表示一直循环。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当setLoop的回调成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. Return by callback. |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## setLoop

ArkTS-Dyn:
```TypeScript
setLoop(streamID: number, loop: number): Promise<void>
```

ArkTS-Sta:
```TypeScript
setLoop(streamID: int, loop: int): Promise<void>
```

设置循环模式。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-setLoop(streamID: int, loop: int): Promise<void>--><!--Device-SoundPool-setLoop(streamID: int, loop: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 音频流ID，通过play方法获取。 |
| loop | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 设置循环次数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当loop≥0时，实际播放次数为loop+1。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 当loop＜0时，表示一直循环。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. Return by promise. |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## setPriority

ArkTS-Dyn:
```TypeScript
setPriority(streamID: number, priority: number, callback: AsyncCallback<void>): void
```

ArkTS-Sta:
```TypeScript
setPriority(streamID: int, priority: int, callback: AsyncCallback<void>): void
```

设置音频流播放的优先级。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-setPriority(streamID: int, priority: int, callback: AsyncCallback<void>): void--><!--Device-SoundPool-setPriority(streamID: int, priority: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 音频流ID，通过play方法获取。 |
| priority | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 优先级，0表示最低优先级。设置范围为大于等于0的整数。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当音频池setPriority方法回调成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. Return by callback. |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## setPriority

ArkTS-Dyn:
```TypeScript
setPriority(streamID: number, priority: number): Promise<void>
```

ArkTS-Sta:
```TypeScript
setPriority(streamID: int, priority: int): Promise<void>
```

设置音频流优先级。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-setPriority(streamID: int, priority: int): Promise<void>--><!--Device-SoundPool-setPriority(streamID: int, priority: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 音频流ID，通过play方法获取。 |
| priority | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 优先级，0表示最低优先级。设置范围为大于等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. Return by promise. |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## setRate

ArkTS-Dyn:
```TypeScript
setRate(streamID: number, rate: audio.AudioRendererRate, callback: AsyncCallback<void>): void
```

ArkTS-Sta:
```TypeScript
setRate(streamID: int, rate: audio.AudioRendererRate, callback: AsyncCallback<void>): void
```

设置音频流播放速率。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-setRate(streamID: int, rate: audio.AudioRendererRate, callback: AsyncCallback<void>): void--><!--Device-SoundPool-setRate(streamID: int, rate: audio.AudioRendererRate, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 音频流ID，通过play方法获取。 |
| rate | audio.AudioRendererRate | 是 | 音频rate相关参数。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当音频池setRate方法回调成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. Return by callback. |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## setRate

ArkTS-Dyn:
```TypeScript
setRate(streamID: number, rate: audio.AudioRendererRate): Promise<void>
```

ArkTS-Sta:
```TypeScript
setRate(streamID: int, rate: audio.AudioRendererRate): Promise<void>
```

设置音频流的播放速率。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-setRate(streamID: int, rate: audio.AudioRendererRate): Promise<void>--><!--Device-SoundPool-setRate(streamID: int, rate: audio.AudioRendererRate): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 音频流ID，通过play方法获取。 |
| rate | audio.AudioRendererRate | 是 | 音频rate相关参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. Return by promise. |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## setVolume

ArkTS-Dyn:
```TypeScript
setVolume(streamID: number, leftVolume: number, rightVolume: number, callback: AsyncCallback<void>): void
```

ArkTS-Sta:
```TypeScript
setVolume(streamID: int, leftVolume: double, rightVolume: double, callback: AsyncCallback<void>): void
```

设置音频流播放音量。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-setVolume(streamID: int, leftVolume: double, rightVolume: double, callback: AsyncCallback<void>): void--><!--Device-SoundPool-setVolume(streamID: int, leftVolume: double, rightVolume: double, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 音频流ID，通过play方法获取。 |
| leftVolume | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 左声道音量，设置范围为[0.0, 1.0]。 |
| rightVolume | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 右声道音量，设置范围为[0.0, 1.0]，当前右声道设置无效，以左声道为准。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当音频池setVolume方法回调成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. Return by callback. |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## setVolume

ArkTS-Dyn:
```TypeScript
setVolume(streamID: number, leftVolume: number, rightVolume: number): Promise<void>
```

ArkTS-Sta:
```TypeScript
setVolume(streamID: int, leftVolume: double, rightVolume: double): Promise<void>
```

设置音频流的播放音量。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-setVolume(streamID: int, leftVolume: double, rightVolume: double): Promise<void>--><!--Device-SoundPool-setVolume(streamID: int, leftVolume: double, rightVolume: double): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 音频流ID，通过play方法获取。 |
| leftVolume | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 左声道音量，设置范围为[0.0, 1.0]。 |
| rightVolume | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 右声道音量，设置范围为[0.0, 1.0]，当前右声道设置无效，以左声道为准。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. Return by promise. |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## stop

ArkTS-Dyn:
```TypeScript
stop(streamID: number, callback: AsyncCallback<void>): void
```

ArkTS-Sta:
```TypeScript
stop(streamID: int, callback: AsyncCallback<void>): void
```

停止播放音频资源。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-stop(streamID: int, callback: AsyncCallback<void>): void--><!--Device-SoundPool-stop(streamID: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 音频流ID，通过play方法获取。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当音频池stop回调成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. Return by callback. |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## stop

ArkTS-Dyn:
```TypeScript
stop(streamID: number): Promise<void>
```

ArkTS-Sta:
```TypeScript
stop(streamID: int): Promise<void>
```

停止streamID对应的音频播放。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-stop(streamID: int): Promise<void>--><!--Device-SoundPool-stop(streamID: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streamID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 音频流ID，通过play方法获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. Return by promise. |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## unload

ArkTS-Dyn:
```TypeScript
unload(soundID: number, callback: AsyncCallback<void>): void
```

ArkTS-Sta:
```TypeScript
unload(soundID: int, callback: AsyncCallback<void>): void
```

卸载音频资源。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-unload(soundID: int, callback: AsyncCallback<void>): void--><!--Device-SoundPool-unload(soundID: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| soundID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 资源ID，通过load方法获取。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当音频池unload方法回调成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400103](../../errorcode-media.md#5400103-出现io错误) | I/O error. Return by callback. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |

## unload

ArkTS-Dyn:
```TypeScript
unload(soundID: number): Promise<void>
```

ArkTS-Sta:
```TypeScript
unload(soundID: int): Promise<void>
```

卸载音频资源。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-SoundPool-unload(soundID: int): Promise<void>--><!--Device-SoundPool-unload(soundID: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.SoundPool

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| soundID | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 资源ID，通过load方法获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../../errorcode-media.md#5400103-出现io错误) | I/O error. Return by promise. |
| [5400105](../../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

