# MediaDescription

Provides the container definition for media description key-value pairs.

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Media.Core

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## [key: string]

```TypeScript
[key: string]: Object
```

key:value pair, key see @MediaDescriptionKey .

**类型：** Object

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

function printfItemDescription(obj: media.MediaDescription, key: string) {
  let property: Object | undefined = obj[key];
  console.info('audio key is ' + key); // 通过key值获取对应的value。key值具体可见MediaDescriptionKey。
  console.info('audio value is ' + property); // 对应key值的value。其类型可为任意类型，具体key对应value的类型可参考MediaDescriptionKey。
}

let avPlayer: media.AVPlayer | undefined = undefined;
media.createAVPlayer((err: BusinessError, player: media.AVPlayer) => {
  if (player != null) {
    avPlayer = player;
    console.info(`Succeeded in creating AVPlayer`);
    avPlayer.getTrackDescription((error: BusinessError, arrList: Array<media.MediaDescription>) => {
      if (arrList != null) {
        for (let i = 0; i < arrList.length; i++) {
          printfItemDescription(arrList[i], media.MediaDescriptionKey.MD_KEY_TRACK_TYPE); // 打印出每条轨道MD_KEY_TRACK_TYPE的值。
        }
      } else {
        console.error(`Failed to get TrackDescription, error:${error}`);
      }
    });
  } else {
    console.error(`Failed to create AVPlayer, error message:${err.message}`);
  }
});
```
