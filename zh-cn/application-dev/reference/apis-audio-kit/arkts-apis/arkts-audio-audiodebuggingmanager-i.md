# AudioDebuggingManager

实现音频调试功能。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.Core

## printAppInfo

```TypeScript
printAppInfo(fd: number): void
```

显示当前应用进程的完整运行时快照。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | fd为文件句柄，表示快照信息将要写入的位置。如果fd小于0，则将快照信息打印到运行日志中，否则快照将写入文件。取值限定为整数。 |

## printCapturerInfo

```TypeScript
printCapturerInfo(capturer: AudioCapturer, fd: number): void
```

打印目标音频捕获程序实例的完整音频运行时快照。
快照将包含流、管道、卷和设备信息。
请注意，不同版本的信息详情和格式可能会有所不同，它只能用于
手动调试，用户不应依赖实际功能实现或文件的信息
内容提取。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capturer | AudioCapturer | 是 | 目标音频捕获程序实例以打印快照。取值限定为整数。 |
| fd | number | 是 | fd是文件描述符，表示快照信息的位置写入到。如果fd小于0或无可写，则快照信息将打印到运行日志，否则快照将写入文件。取值限定为整数。 |

## printLoopbackInfo

```TypeScript
printLoopbackInfo(loopback: AudioLoopback, fd: number): void
```

打印目标音频环回实例的完整音频运行时快照。
快照将包含环回状态、设备和效果信息。
请注意，不同版本的信息详情和格式可能会有所不同，它只能用于
手动调试，用户不应依赖实际功能实现或文件的信息
内容提取。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| loopback | AudioLoopback | 是 | 目标音频环回实例以打印快照。取值限定为整数。 |
| fd | number | 是 | fd是文件描述符，表示快照信息的位置写入到。如果fd小于0或无可写，则快照信息将打印到运行日志，否则快照将写入文件。取值限定为整数。 |

## printRendererInfo

```TypeScript
printRendererInfo(renderer: AudioRenderer, fd: number): void
```

打印目标音频渲染器实例的完整音频运行时快照。
快照将包含流、管道、卷和设备信息。
请注意，不同版本的信息详情和格式可能会有所不同，它只能用于
手动调试，用户不应依赖实际功能实现或文件的信息
内容提取。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| renderer | AudioRenderer | 是 | 目标音频渲染器实例以打印快照。取值限定为整数。 |
| fd | number | 是 | fd是文件描述符，表示快照信息的位置写入到。如果fd小于0或无可写，则快照信息将打印到运行日志，否则快照将写入文件。取值限定为整数。 |

## printSessionInfo

```TypeScript
printSessionInfo(session: AudioSessionManager, fd: number): void
```

打印目标音频会话管理器实例的完整音频运行时快照。
快照将包含会话状态、场景、策略和设备信息。
请注意，不同版本的信息详情和格式可能会有所不同，它只能用于
手动调试，用户不应依赖实际功能实现或文件的信息
内容提取。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| session | AudioSessionManager | 是 | 目标音频会话管理器实例以打印快照。取值限定为整数。 |
| fd | number | 是 | fd是文件描述符，表示快照信息的位置写入到。如果fd小于0或无可写，则快照信息将打印到运行日志，否则快照将写入文件。取值限定为整数。 |

