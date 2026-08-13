# getHistoricalAVQueueInfos（系统接口）

## getHistoricalAVQueueInfos

```TypeScript
function getHistoricalAVQueueInfos(maxSize: int, maxAppSize: int, callback: AsyncCallback<Array<Readonly<AVQueueInfo>>>): void
```

获取全部的历史播放歌单。结果通过callback异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function getHistoricalAVQueueInfos(maxSize: int, maxAppSize: int, callback: AsyncCallback<Array<Readonly<AVQueueInfo>>>): void--><!--Device-avSession-function getHistoricalAVQueueInfos(maxSize: int, maxAppSize: int, callback: AsyncCallback<Array<Readonly<AVQueueInfo>>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxSize | int | 是 | 指定获取歌曲列表数量的最大值，暂与获取歌单数量无关。 |
| maxAppSize | int | 是 | 指定获取歌曲列表所属应用数量的最大值，暂与获取歌单数量无关。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;Readonly&lt;[AVQueueInfo](arkts-avsession-avsession-avqueueinfo-i-sys.md)&gt;&gt;&gt; | 是 | 回调函数。返回所有历史播放歌单的只读对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

## 示例

```TypeScript
avSession.getHistoricalAVQueueInfos(3, 5, (avQueueInfos: avSession.AVQueueInfo[]) => { 
    console.info(`Succeeded in getting historical AV queue infos, length: ${avQueueInfos.length}`); 
});
```


## getHistoricalAVQueueInfos

```TypeScript
function getHistoricalAVQueueInfos(maxSize: int, maxAppSize: int): Promise<Array<Readonly<AVQueueInfo>>>
```

获取全部的历史播放歌单。结果通过Promise异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function getHistoricalAVQueueInfos(maxSize: int, maxAppSize: int): Promise<Array<Readonly<AVQueueInfo>>>--><!--Device-avSession-function getHistoricalAVQueueInfos(maxSize: int, maxAppSize: int): Promise<Array<Readonly<AVQueueInfo>>>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Manager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxSize | int | 是 | 指定获取歌曲列表数量的最大值，暂与获取歌单数量无关。 |
| maxAppSize | int | 是 | 指定获取歌曲列表所属应用数量的最大值，暂与获取歌单数量无关。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Readonly&lt;[AVQueueInfo](arkts-avsession-avsession-avqueueinfo-i-sys.md)&gt;&gt;&gt; | Promise对象。返回所有历史播放歌单的只读对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

## 示例

```TypeScript
avSession.getHistoricalAVQueueInfos(3, 5).then((avQueueInfos: avSession.AVQueueInfo[]) => {
  console.info(`Succeeded in getting historical AV queue infos, length: ${avQueueInfos.length}`);
});
```

