# TonePlayer（系统接口）

**起始版本：** 9

<!--Device-audio-interface TonePlayer--><!--Device-audio-interface TonePlayer-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Tone

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## load

```TypeScript
load(type: ToneType, callback: AsyncCallback<void>): void
```

Loads tone. This method uses an asynchronous callback to return the result.

**起始版本：** 9

<!--Device-TonePlayer-load(type: ToneType, callback: AsyncCallback<void>): void--><!--Device-TonePlayer-load(type: ToneType, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Tone

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ToneType](arkts-audio-audio-tonetype-e-sys.md) | 是 | Tone type to play. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

tonePlayer.load(audio.ToneType.TONE_TYPE_DIAL_5, (err: BusinessError) => {
  if (err) {
    console.error(`callback call load failed error: ${err.message}`);
    return;
  } else {
    console.info('callback call load success');
  }
});

```

## load

```TypeScript
load(type: ToneType): Promise<void>
```

Loads tone. This method uses a promise to return the result.

**起始版本：** 9

<!--Device-TonePlayer-load(type: ToneType): Promise<void>--><!--Device-TonePlayer-load(type: ToneType): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Tone

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ToneType](arkts-audio-audio-tonetype-e-sys.md) | 是 | Tone type to play. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**示例：**

```TypeScript
tonePlayer.load(audio.ToneType.TONE_TYPE_DIAL_1).then(() => {
  console.info('promise call load ');
}).catch(() => {
  console.error('promise call load fail');
});

```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases the player. This method uses an asynchronous callback to return the result.

**起始版本：** 9

<!--Device-TonePlayer-release(callback: AsyncCallback<void>): void--><!--Device-TonePlayer-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Tone

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

tonePlayer.release((err: BusinessError) => {
  if (err) {
    console.error(`callback call release failed error: ${err.message}`);
    return;
  } else {
    console.info('callback call release success ');
  }
});

```

## release

```TypeScript
release(): Promise<void>
```

Releases the player. This method uses a promise to return the result.

**起始版本：** 9

<!--Device-TonePlayer-release(): Promise<void>--><!--Device-TonePlayer-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Tone

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**示例：**

```TypeScript
tonePlayer.release().then(() => {
  console.info('promise call release');
}).catch(() => {
  console.error('promise call release fail');
});

```

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

Starts player. This method uses an asynchronous callback to return the result.

**起始版本：** 9

<!--Device-TonePlayer-start(callback: AsyncCallback<void>): void--><!--Device-TonePlayer-start(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Tone

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

tonePlayer.start((err: BusinessError) => {
  if (err) {
    console.error(`callback call start failed error: ${err.message}`);
    return;
  } else {
    console.info('callback call start success');
  }
});

```

## start

```TypeScript
start(): Promise<void>
```

Starts player. This method uses a promise to return the result.

**起始版本：** 9

<!--Device-TonePlayer-start(): Promise<void>--><!--Device-TonePlayer-start(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Tone

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; |  |

**示例：**

```TypeScript
tonePlayer.start().then(() => {
  console.info('promise call start');
}).catch(() => {
  console.error('promise call start fail');
});

```

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

Stops player. This method uses an asynchronous callback to return the result.

**起始版本：** 9

<!--Device-TonePlayer-stop(callback: AsyncCallback<void>): void--><!--Device-TonePlayer-stop(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Tone

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | Callback used to return the result. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

tonePlayer.stop((err: BusinessError) => {
  if (err) {
    console.error(`callback call stop error: ${err.message}`);
    return;
  } else {
    console.error('callback call stop success ');
  }
});

```

## stop

```TypeScript
stop(): Promise<void>
```

Stops player. This method uses a promise to return the result.

**起始版本：** 9

<!--Device-TonePlayer-stop(): Promise<void>--><!--Device-TonePlayer-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Tone

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**示例：**

```TypeScript
tonePlayer.stop().then(() => {
  console.info('promise call stop finish');
}).catch(() => {
  console.error('promise call stop fail');
});

```

