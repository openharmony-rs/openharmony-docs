# createAVAdsController

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## createAVAdsController

```TypeScript
function createAVAdsController(player: AVPlayer): Promise<AVAdsController | undefined>
```

创建一个与播放器实例关联的广告播放控制器。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| player | [AVPlayer](arkts-media-media-avplayer-i.md) | 是 | 已创建的播放器实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AVAdsController](arkts-media-media-avadscontroller-i.md) \| undefined&gt; | Promise对象。成功时返回广告播放控制器实例，失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | The player object corresponding to player does not exist or is invalid. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function test() {
  let player: media.AVPlayer = await media.createAVPlayer();
  media.createAVAdsController(player).then((adsController: media.AVAdsController | undefined) => {
    if (adsController) {
      console.info('Succeeded in creating AVAdsController');
    } else {
      console.error('Failed to create AVAdsController');
    }
  }).catch((error: BusinessError) => {
    console.error(`Failed to create AVAdsController, error: ${error}`);
  });
}
```
