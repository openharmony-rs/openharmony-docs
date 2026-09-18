# AVRecorderState

```TypeScript
type AVRecorderState = 'idle' | 'prepared' | 'started' | 'paused' | 'stopped' | 'released' | 'error'
```

音视频录制的状态机。可通过state属性获取当前状态。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

| 类型 | 说明 |
| --- | --- |
| 'idle' | 闲置状态。此时可以调用[AVRecorder.prepare()](arkts-media-media-avrecorder-i.md#prepare)方法设置录制参数，进入prepared状态。AVRecorder刚被创建，或者在任何非released状态下调用[AVRecorder.reset()](arkts-media-media-avrecorder-i.md#reset)方法，均进入idle状态。 |
| 'prepared' | 参数设置完成。此时可以调用[AVRecorder.start()](arkts-media-media-avrecorder-i.md#start)方法开始录制，进入started状态。 |
| 'started' | 正在录制。此时可以调用[AVRecorder.pause()](arkts-media-media-avrecorder-i.md#pause)方法暂停录制，进入paused状态。也可以调用[AVRecorder.stop()](arkts-media-media-avrecorder-i.md#stop)方法结束录制，进入stopped状态。 |
| 'paused' | 录制暂停。此时可以调用[AVRecorder.resume()](arkts-media-media-avrecorder-i.md#resume)方法继续录制，进入started状态。也可以调用[AVRecorder.stop()](arkts-media-media-avrecorder-i.md#stop)方法结束录制，进入stopped状态。 |
| 'stopped' | 录制停止。此时可以调用[AVRecorder.prepare()](arkts-media-media-avrecorder-i.md#prepare)方法设置录制参数，重新进入prepared状态。 |
| 'released' | 录制资源释放。此时不能再进行任何操作。在任何其他状态下，均可以通过调用[AVRecorder.release()](arkts-media-media-avrecorder-i.md#release)方法进入released状态。 |
| 'error' | 错误状态。当AVRecorder实例发生不可逆错误，会转换至当前状态。切换至error状态时会伴随[AVRecorder.on('error')](arkts-media-media-avrecorder-i.md#onerror)，该事件会上报详细错误原因。在error状态时，用户需要调用[AVRecorder.reset()](arkts-media-media-avrecorder-i.md#reset)方法重置AVRecorder实例，或者调用[AVRecorder.release()](arkts-media-media-avrecorder-i.md#release)方法释放资源。 |
