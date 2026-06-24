# AdInteractionListener

广告状态变化回调。

**起始版本：** 11

**系统能力：** SystemCapability.Advertising.Ads

## onStatusChanged

```TypeScript
onStatusChanged(status: string, ad: Advertisement, data: string)
```

广告状态回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Advertising.Ads

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| status | string | 是 | 广告展示状态。<br/>- onAdLoad：广告加载成功。<br/>- onAdFail：广告加载失败。<br/>- onAdOpen：打开广告。<br/>- onAdClick：点击广告。<br/>- onAdClose：关闭广告。<br/>- onMediaProgress：广告播放进度。<br/>- onMediaStart：广告开始播放。<br/>- onMediaPause：广告暂停播放。<br/>- onMediaStop：广告停止播放。<br/>- onMediaComplete：广告播放完成。<br/>- onMediaCountDown：广告倒计时。<br/>- onMediaError：广告播放失败。<br/>- onLandscape：竖屏状态下点击全屏按钮。<br/>- onPortrait：全屏状态下点击返回按钮。<br/>- onBackClicked：点击返回按钮。<br/>- onAdSubWindow：打开半模态。 |
| ad | Advertisement | 是 | 发生状态变化的广告内容。 |
| data | string | 是 | 扩展信息。<br/>当status参数为onAdClose时，data值为关闭原因，关闭原因描述如下：<br/>- adShowEnded：广告展示结束。<br/>- adCloseBtnClicked：点击关闭按钮。<br/>- adSkipBtnClicked：点击跳过。<br/>- adFeedbackClosed：负反馈关闭。<br/>- adBackgroundClosed：开屏切后台关闭。 |

**示例：**

```TypeScript
import { advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const adInteractionListener: advertising.AdInteractionListener = {
  onStatusChanged: (status: string, ad: advertising.Advertisement, data: string) => {
    switch (status) {
      case 'onAdLoad':
        hilog.info(0x0000, 'testTag', 'Status is onAdLoad');
        break;
      case 'onAdFail':
        hilog.error(0x0000, 'testTag', 'Status is onAdFail');
        break;
      case 'onAdOpen':
        hilog.info(0x0000, 'testTag', 'Status is onAdOpen');
        break;
      case 'onAdClick':
        hilog.info(0x0000, 'testTag', 'Status is onAdClick');
        break;
      case 'onAdClose':
        // data值为关闭原因
        hilog.info(0x0000, 'testTag', `Status is onAdClose, Close Reason is ${data}`);
        if (data === 'adShowEnded') {
          // 关闭原因为广告展示结束，可根据实际场景添加处理逻辑
        }
        break;
      case 'onMediaProgress':
        hilog.info(0x0000, 'testTag', 'Status is onMediaProgress');
        break;
      case 'onMediaStart':
        hilog.info(0x0000, 'testTag', 'Status is onMediaStart');
        break;
      case 'onMediaPause':
        hilog.info(0x0000, 'testTag', 'Status is onMediaPause');
        break;
      case 'onMediaStop':
        hilog.info(0x0000, 'testTag', 'Status is onMediaStop');
        break;
      case 'onMediaComplete':
        hilog.info(0x0000, 'testTag', 'Status is onMediaComplete');
        break;
      case 'onMediaCountDown':
        hilog.info(0x0000, 'testTag', 'Status is onMediaCountDown');
        break;
      case 'onMediaError':
        hilog.info(0x0000, 'testTag', 'Status is onMediaError');
        break;
      case 'onLandscape':
        hilog.info(0x0000, 'testTag', 'Status is onLandscape');
        break;
      case 'onPortrait':
        hilog.info(0x0000, 'testTag', 'Status is onPortrait');
        break;
      case 'onBackClicked':
        hilog.info(0x0000, 'testTag', 'Status is onBackClicked');
        break;
      default:
        break;
    }
  }
}

```

