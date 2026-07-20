# SystemSoundPlayer

音效播放器提供了加载、卸载和播放系统声音的功能。

SystemSoundPlayer需要和[@ohos.multimedia.systemSoundManager](arkts-multimedia-systemsoundmanager.md)配合使用，才能完成管理系统音效的功能。

**起始版本：** 23

<!--Device-unnamed-export interface SystemSoundPlayer--><!--Device-unnamed-export interface SystemSoundPlayer-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

<a id="load"></a>
## load

```TypeScript
load(soundType: systemSoundManager.SystemSoundType): Promise<void>
```

加载系统音效。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemSoundPlayer-load(soundType: systemSoundManager.SystemSoundType): Promise<void>--><!--Device-SystemSoundPlayer-load(soundType: systemSoundManager.SystemSoundType): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| soundType | systemSoundManager.SystemSoundType | 是 | 系统音效类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-播放服务死亡) | Crash or blocking occurs in system process. |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-参数超过取值范围) | Parameter check failed. Returned by promise. |

<a id="play"></a>
## play

```TypeScript
play(soundType: systemSoundManager.SystemSoundType): Promise<void>
```

播放系统音效。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemSoundPlayer-play(soundType: systemSoundManager.SystemSoundType): Promise<void>--><!--Device-SystemSoundPlayer-play(soundType: systemSoundManager.SystemSoundType): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| soundType | systemSoundManager.SystemSoundType | 是 | 系统音效类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-播放服务死亡) | Crash or blocking occurs in system process. |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-参数超过取值范围) | Parameter check failed. Returned by promise. |

<a id="release"></a>
## release

```TypeScript
release(): Promise<void>
```

释放系统音效播放器。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemSoundPlayer-release(): Promise<void>--><!--Device-SystemSoundPlayer-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-播放服务死亡) | Crash or blocking occurs in system process. |

<a id="unload"></a>
## unload

```TypeScript
unload(soundType: systemSoundManager.SystemSoundType): Promise<void>
```

卸载之前已加载的系统音效。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemSoundPlayer-unload(soundType: systemSoundManager.SystemSoundType): Promise<void>--><!--Device-SystemSoundPlayer-unload(soundType: systemSoundManager.SystemSoundType): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| soundType | systemSoundManager.SystemSoundType | 是 | 系统音效类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-播放服务死亡) | Crash or blocking occurs in system process. |
| [5400108](../../apis-media-kit/errorcode-media.md#5400108-参数超过取值范围) | Parameter check failed. Returned by promise. |

