# 废弃的Interface (AudioPlayer, deprecated)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xushubo; @chennotfound-->
<!--Designer: @dongyu_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @zengyawen-->

> **说明：**
>
> 从API version 6开始支持，从API version 9开始废弃，建议使用[AVPlayer](arkts-apis-media-AVPlayer.md)替代。

音频播放管理类，用于管理和播放音频媒体。在调用AudioPlayer的方法前，需要先通过[createAudioPlayer()](arkts-apis-media-f.md#mediacreateaudioplayerdeprecated)构建一个AudioPlayer实例。

## 导入模块

```ts
import { media } from '@kit.MediaKit';
```

## 属性<sup>(deprecated)</sup>

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

| 名称                            | 类型                                                   | 只读 | 可选 | 说明                                                         |
| ------------------------------- | ------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| src                             | string                                                 | 否   | 否   | 音频媒体URI，支持当前主流的音频格式(m4a、aac、mp3、ogg、wav、amr)。<br>**支持路径示例**：<br>1. fd类型播放：fd://xx<br>![](figures/zh-cn_image_url.png)<br>2. http网络播放: http\://xx<br/>3. https网络播放: https\://xx<br/>4. hls网络播放路径：http\://xx或者https\://xx <br/>**需要权限：** ohos.permission.READ_MEDIA 或 ohos.permission.INTERNET。 |
| fdSrc<sup>9+</sup>              | [AVFileDescriptor](arkts-apis-media-i.md#avfiledescriptor9)                 | 否   | 否   | 音频媒体文件描述，使用场景：应用中的音频资源被连续存储在同一个文件中。<br/>**使用示例**：<br/>假设一个连续存储的音乐文件: <br/>音乐1(地址偏移:0，字节长度:100)<br/>音乐2(地址偏移:101，字节长度:50)<br/>音乐3(地址偏移:151，字节长度:150)<br/>1. 播放音乐1：AVFileDescriptor { fd = 资源句柄; offset = 0; length = 100; }<br/>2. 播放音乐2：AVFileDescriptor { fd = 资源句柄; offset = 101; length = 50; }<br/>3. 播放音乐3：AVFileDescriptor { fd = 资源句柄; offset = 151; length = 150; }<br/>假设是一个独立的音乐文件: 请使用src=fd://xx <br/> |
| loop                            | boolean                                                | 否   | 否  | 音频循环播放属性，设置为'true'表示循环播放。                 |
| audioInterruptMode<sup>9+</sup> | [audio.InterruptMode](../apis-audio-kit/arkts-apis-audio-e.md#interruptmode9) | 是   | 是   | 音频焦点模型。                                               |
| currentTime                     | number                                                 | 是   | 否   | 音频的当前播放位置，单位为毫秒（ms）。                       |
| duration                        | number                                                 | 是   | 否   | 音频时长，单位为毫秒（ms）。                                 |
| state                           | [AudioState](arkts-apis-media-t.md#audiostatedeprecated)                              | 是   | 否   | 可以查询音频播放的状态，该状态不可作为调用play/pause/stop等状态切换的触发条件。 |

## play<sup>(deprecated)</sup>

play(): void

开始播放音频资源，需在'dataLoad'事件成功触发后，才能调用。

> **说明：**
> 从API version 6开始支持，从API version 9开始废弃，建议使用[AVPlayer.play](arkts-apis-media-AVPlayer.md#play9)替代。

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**示例：**

```ts
audioPlayer.on('play', () => {    //设置'play'事件回调。
  console.info('audio play called');
});
audioPlayer.play();
```

## pause<sup>(deprecated)</sup>

pause(): void

暂停播放音频资源。

> **说明：**
> 从API version 6开始支持，从API version 9开始废弃，建议使用[AVPlayer.pause](arkts-apis-media-AVPlayer.md#pause9)替代。

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**示例：**

```ts
audioPlayer.on('pause', () => {    //设置'pause'事件回调。
  console.info('audio pause called');
});
audioPlayer.pause();
```

## stop<sup>(deprecated)</sup>

stop(): void

停止播放音频资源。

> **说明：**
> 从API version 6开始支持，从API version 9开始废弃，建议使用[AVPlayer.stop](arkts-apis-media-AVPlayer.md#stop9)替代。

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**示例：**

```ts
audioPlayer.on('stop', () => {    //设置'stop'事件回调。
  console.info('audio stop called');
});
audioPlayer.stop();
```

## reset<sup>(deprecated)</sup>

reset(): void

重置播放音频资源。

> **说明：**
> 从API version 7开始支持，从API version 9开始废弃，建议使用[AVPlayer.reset](arkts-apis-media-AVPlayer.md#reset9)替代。

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**示例：**

```ts
audioPlayer.on('reset', () => {    //设置'reset'事件回调。
  console.info('audio reset called');
});
audioPlayer.reset();
```

## seek<sup>(deprecated)</sup>

seek(timeMs: number): void

跳转到指定播放位置。

> **说明：**
> 从API version 6开始支持，从API version 9开始废弃，建议使用[AVPlayer.seek](arkts-apis-media-AVPlayer.md#seek9)替代。

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                        |
| ------ | ------ | ---- | ----------------------------------------------------------- |
| timeMs | number | 是   | 指定的跳转时间节点，单位毫秒（ms），取值范围[0, duration]。 |

**示例：**

```ts
audioPlayer.on('timeUpdate', (seekDoneTime: number) => {    //设置'timeUpdate'事件回调。
  if (seekDoneTime == null) {
    console.error('Failed to seek');
    return;
  }
  console.info('Succeeded in seek. seekDoneTime: ' + seekDoneTime);
});
audioPlayer.seek(30000);    //seek到30000ms的位置。
```

## setVolume<sup>(deprecated)</sup>

setVolume(vol: number): void

设置音量。

> **说明：**
> 从API version 6开始支持，从API version 9开始废弃，建议使用[AVPlayer.setVolume](arkts-apis-media-AVPlayer.md#setvolume9)替代。

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                         |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| vol    | number | 是   | 指定的相对音量大小，取值范围为[0.00-1.00]，1表示最大音量，即100%。 |

**示例：**

```ts
audioPlayer.on('volumeChange', () => {    //设置'volumeChange'事件回调。
  console.info('audio volumeChange called');
});
audioPlayer.setVolume(1);    //设置音量到100%。
```

## release<sup>(deprecated)</sup>

release(): void

释放音频资源。

> **说明：**
> 从API version 6开始支持，从API version 9开始废弃，建议使用[AVPlayer.release](arkts-apis-media-AVPlayer.md#release9)替代。

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**示例：**

```ts
audioPlayer.release();
audioPlayer = undefined;
```

## getTrackDescription<sup>(deprecated)</sup>

getTrackDescription(callback: AsyncCallback\<Array\<MediaDescription>>): void

获取音频轨道信息。需在'dataLoad'事件成功触发后，才能调用。通过回调函数获取返回值。

> **说明：**
> 从API version 8开始支持，从API version 9开始废弃，建议使用[AVPlayer.getTrackDescription](arkts-apis-media-AVPlayer.md#gettrackdescription9)替代。

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                       |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------ |
| callback | AsyncCallback\<Array\<[MediaDescription](arkts-apis-media-i.md#mediadescription8)>> | 是   | 回调函数。获取音频轨道信息成功时，err为undefined，data为获取到的MediaDescription数组，否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioPlayer.getTrackDescription((error: BusinessError, arrList: Array<media.MediaDescription>) => {
  if (arrList != null) {
    console.info('Succeeded in getting TrackDescription');
  } else {
    console.error(`Failed to get TrackDescription, error:${error}`);
  }
});
```

## getTrackDescription<sup>(deprecated)</sup>

getTrackDescription(): Promise\<Array\<MediaDescription>>

获取音频轨道信息。需在'dataLoad'事件成功触发后，才能调用。通过Promise获取返回值。

> **说明：**
> 从API version 8开始支持，从API version 9开始废弃，建议使用[AVPlayer.getTrackDescription](arkts-apis-media-AVPlayer.md#gettrackdescription9-1)替代。

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**返回值：**

| 类型                                                   | 说明                                            |
| ------------------------------------------------------ | ----------------------------------------------- |
| Promise<Array<[MediaDescription](arkts-apis-media-i.md#mediadescription8)>> | 音频轨道信息MediaDescription数组Promise返回值。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioPlayer.getTrackDescription().then((arrList: Array<media.MediaDescription>) => {
  console.info('Succeeded in getting TrackDescription');
}).catch((error: BusinessError) => {
  console.error(`Failed to get TrackDescription, error:${error}`);
});
```

## on('bufferingUpdate')<sup>(deprecated)</sup>

on(type: 'bufferingUpdate', callback: (infoType: BufferingInfoType, value: number) => void): void

开始订阅音频缓存更新事件。仅网络播放支持该订阅事件。

> **说明：**
> 从API version 8开始支持，从API version 9开始废弃，建议使用[AVPlayer.on('bufferingUpdate')](arkts-apis-media-AVPlayer.md#onbufferingupdate9)替代。

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名   | 类型     | 必填 | 说明                                                         |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | 是   | 音频缓存事件回调类型，支持的事件：'bufferingUpdate'。        |
| callback | function | 是   | 音频缓存事件回调方法。<br>[BufferingInfoType](arkts-apis-media-e.md#bufferinginfotype8)value值固定为0。 |

**示例：**

```ts
audioPlayer.on('bufferingUpdate', (infoType: media.BufferingInfoType, value: number) => {
  console.info('audio bufferingInfo type: ' + infoType);
  console.info('audio bufferingInfo value: ' + value);
});
```

## on('play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange')<sup>(deprecated)</sup>

on(type: 'play' | 'pause' | 'stop' | 'reset' | 'dataLoad' | 'finish' | 'volumeChange', callback: () => void): void

开始订阅音频播放事件。

> **说明：**
> 从API version 6开始支持，从API version 9开始废弃，建议使用[AVPlayer.on('stateChange')](arkts-apis-media-AVPlayer.md#onstatechange9)替代。

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名   | 类型       | 必填 | 说明                                                         |
| -------- | ---------- | ---- | ------------------------------------------------------------ |
| type     | string     | 是   | 播放事件回调类型，支持的事件包括：'play' \| 'pause' \| 'stop' \| 'reset' \| 'dataLoad' \| 'finish' \| 'volumeChange'。<br>- 'play'：完成[play()](#playdeprecated)调用，音频开始播放，触发该事件。<br>- 'pause'：完成[pause()](#pausedeprecated)调用，音频暂停播放，触发该事件。<br>- 'stop'：完成[stop()](#stopdeprecated)调用，音频停止播放，触发该事件。<br>- 'reset'：完成[reset()](#resetdeprecated)调用，播放器重置，触发该事件。<br>- 'dataLoad'：完成音频数据加载后触发该事件，即src属性设置完成后触发该事件。<br>- 'finish'：完成音频播放后触发该事件。<br>- 'volumeChange'：完成[setVolume()](#setvolumedeprecated)调用，播放音量改变后触发该事件。 |
| callback | () => void | 是   | 播放事件回调方法。                                           |

**示例：**

```ts
import { fileIo as fs } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioPlayer: media.AudioPlayer = media.createAudioPlayer();  //创建一个音频播放实例。
audioPlayer.on('dataLoad', () => {            //设置'dataLoad'事件回调，src属性设置成功后，触发此回调。
  console.info('audio set source called');
  audioPlayer.play();                       //开始播放，并触发'play'事件回调。
});
audioPlayer.on('play', () => {                //设置'play'事件回调。
  console.info('audio play called');
  audioPlayer.seek(30000);                  //调用seek方法，并触发'timeUpdate'事件回调。
});
audioPlayer.on('pause', () => {               //设置'pause'事件回调。
  console.info('audio pause called');
  audioPlayer.stop();                       //停止播放，并触发'stop'事件回调。
});
audioPlayer.on('reset', () => {               //设置'reset'事件回调。
  console.info('audio reset called');
  audioPlayer.release();                    //释放播放实例资源。
  audioPlayer = undefined;
});
audioPlayer.on('timeUpdate', (seekDoneTime: number) => {  //设置'timeUpdate'事件回调。
  if (seekDoneTime == null) {
    console.error('Failed to seek');
    return;
  }
  console.info('Succeeded in seek, and seek time is ' + seekDoneTime);
  audioPlayer.setVolume(0.5);                //设置音量为50%，并触发'volumeChange'事件回调。
});
audioPlayer.on('volumeChange', () => {         //设置'volumeChange'事件回调。
  console.info('audio volumeChange called');
  audioPlayer.pause();                       //暂停播放，并触发'pause'事件回调。
});
audioPlayer.on('finish', () => {               //设置'finish'事件回调。
  console.info('audio play finish');
  audioPlayer.stop();                        //停止播放，并触发'stop'事件回调。
});
audioPlayer.on('error', (error: BusinessError) => {  //设置'error'事件回调。
  console.error(`audio error called, error: ${error}`);
});

// 用户选择音频设置fd(本地播放)。
let fdPath = 'fd://';
// path路径的码流可通过"hdc file send D:\xxx\01.mp3 /data/accounts/account_0/appdata" 命令，将其推送到设备上。
let path = '/data/accounts/account_0/appdata/ohos.xxx.xxx.xxx/01.mp3';
fs.open(path).then((file) => {
  fdPath = fdPath + '' + file.fd;
  console.info('Succeeded in opening fd, fd is' + fdPath);
  audioPlayer.src = fdPath;  //设置src属性，并触发'dataLoad'事件回调。
}, (err: BusinessError) => {
  console.error('Failed to open fd, err is' + err);
}).catch((err: BusinessError) => {
  console.error('Failed to open fd, err is' + err);
});
```

## on('timeUpdate')<sup>(deprecated)</sup>

on(type: 'timeUpdate', callback: Callback\<number>): void

开始订阅音频播放时间更新事件。处于播放状态时，每隔1s上报一次该事件。

> **说明：**
> 从API version 6开始支持，从API version 9开始废弃，建议使用[AVPlayer.on('timeUpdate')](arkts-apis-media-AVPlayer.md#ontimeupdate9)替代。

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名   | 类型              | 必填 | 说明                                                         |
| -------- | ----------------- | ---- | ------------------------------------------------------------ |
| type     | string            | 是   | 播放事件回调类型，支持的事件包括：'timeUpdate'。<br>- 'timeUpdate'：音频播放时间戳更新，开始播放后自动触发该事件。 |
| callback | Callback\<number> | 是   | 播放事件回调方法。回调方法入参为更新后的时间戳。             |

**示例：**

```ts
audioPlayer.on('timeUpdate', (newTime: number) => {    //设置'timeUpdate'事件回调。
  if (newTime == null) {
    console.error('Failed to do timeUpdate');
    return;
  }
  console.info('Succeeded in doing timeUpdate. seekDoneTime: ' + newTime);
});
audioPlayer.play();    // 开始播放后，自动触发时间戳更新事件。
```

## on('audioInterrupt')<sup>(deprecated)</sup>

on(type: 'audioInterrupt', callback: (info: audio.InterruptEvent) => void): void

监听音频焦点变化事件，参考[audio.InterruptEvent](../apis-audio-kit/arkts-apis-audio-i.md#interruptevent9)。

> **说明：**
> 从API version 9开始支持，从API version 9开始废弃，建议使用[AVPlayer.on('audioInterrupt')](arkts-apis-media-AVPlayer.md#onaudiointerrupt9)替代。

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                     |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------------------------- |
| type     | string                                                       | 是   | 音频焦点变化事件回调类型，支持的事件：'audioInterrupt'。 |
| callback | function  | 是   | 音频焦点变化事件回调方法。                               |

**示例：**

```ts
import { audio } from '@kit.AudioKit';

audioPlayer.on('audioInterrupt', (info: audio.InterruptEvent) => {
  console.info('audioInterrupt called,and InterruptEvent info is:' + info);
});
```

## on('error')<sup>(deprecated)</sup>

on(type: 'error', callback: ErrorCallback): void

开始订阅音频播放错误事件，当上报error错误事件后，用户需处理error事件，退出播放操作。

> **说明：**
> 从API version 6开始支持，从API version 9开始废弃，建议使用[AVPlayer.on('error')](arkts-apis-media-AVPlayer.md#onerror9)替代。

**系统能力：** SystemCapability.Multimedia.Media.AudioPlayer

**参数：**

| 参数名   | 类型          | 必填 | 说明                                                         |
| -------- | ------------- | ---- | ------------------------------------------------------------ |
| type     | string        | 是   | 播放错误事件回调类型，支持的事件包括：'error'。<br>- 'error'：音频播放中发生错误，触发该事件。 |
| callback | [ErrorCallback](../apis-basic-services-kit/js-apis-base.md#errorcallback) | 是   | 播放错误事件回调方法。                                       |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioPlayer.on('error', (error: BusinessError) => {  //设置'error'事件回调。
  console.error(`audio error called, error: ${error}`);
});
audioPlayer.setVolume(3);  //设置volume为无效值，触发'error'事件。
```