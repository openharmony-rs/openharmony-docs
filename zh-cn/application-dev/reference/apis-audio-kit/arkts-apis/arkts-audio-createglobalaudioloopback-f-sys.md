# createGlobalAudioLoopback（系统接口）

## createGlobalAudioLoopback

```TypeScript
function createGlobalAudioLoopback(mode: AudioLoopbackMode, isController: boolean): Promise<AudioLoopback | null>
```

创建全局音频环回实例，提供低时延入耳监听功能。
硬件音频环回只能在支持的平台中创建，应用程序可以使用
> **说明**
> {@link AudioStreamManager#isAudioLoopbackSupported}先检查。
> 系统中应该只有一个拥有全局环回的主实例，其他
> 是控制器。控制器可以通过向主设备发送命令来管理全局环回。
> 实例，并从中监听状态变化。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | AudioLoopbackMode | 是 | 要创建的音频环回模式 |
| isController | boolean | 是 | 创建拥有音频环回或仅拥有控制器的对象 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AudioLoopback \| null&gt; | Promise用于返回音频环回实例。或者发生错误时为null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-无效入参) | Parameter verification failed. |
| [6800104](../errorcode-audio.md#6800104-参数选项不支持) | Loopback mode is unsupported. |

