# AdInteractionListener

Defines the ad status change callback.

**Since:** 11

**System capability:** SystemCapability.Advertising.Ads

## Modules to Import

```TypeScript
import { advertising } from '@kit.AdsKit';
```

## onStatusChanged

```TypeScript
onStatusChanged(status: string, ad: Advertisement, data: string)
```

Called when the ad display status changes.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| status | string | Yes | Ad show status.   - onAdLoad: Ad loaded successfully.   - onAdFail: Ad failed to load.   - onAdOpen: Ad opened.   - onAdClick: Ad clicked.   - onAdClose: Ad closed.   - onMediaProgress: Ad playback progress.   - onMediaStart: Ad playback started.   - onMediaPause: Ad playback paused.   - onMediaStop: Ad playback stopped.   - onMediaComplete: Ad playback completed.   - onMediaCountDown: Ad countdown.   - onMediaError: Ad playback failed.   - onLandscape: Full-screen button clicked in portrait mode.   - onPortrait: Back button clicked in full-screen mode.   - onBackClicked: Back button clicked.   - onAdSubWindow: Sheet opened. |
| ad | [Advertisement](arkts-ads-advertising-advertisement-t.md) | Yes | Content of the ad. |
| data | string | Yes | Extended information. When **status** is **onAdClose**, the data value is the close reason, described as follows:   - adShowEnded: Ad show ended.   - adCloseBtnClicked: Close button clicked.   - adSkipBtnClicked: Skip button clicked.   - adFeedbackClosed: The ad is closed due to negative feedback.   - adBackgroundClosed: The splash ad is closed when the app switches to the background. |

**Examples**

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
        // The data value is the close reason.
        hilog.info(0x0000, 'testTag', `Status is onAdClose, Close Reason is ${data}`);
        if (data === 'adShowEnded') {
          // The close reason is that the ad show has ended. You can add processing logic based on the actual scenario.
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
