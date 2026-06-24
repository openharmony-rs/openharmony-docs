# @ohos.screenshot

��ģ���ṩ��Ļ��ͼ��������

**起始版本：** 12

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [capture](arkts-arkui-screenshot-capture-f.md#capture-1) | ��ȡ��Ļȫ����ͼ��ʹ��Promise�첽�ص���<br/><br/>�˽ӿڿ���ͨ�����ò�ͬ��displayId��ȡ��ͬ��Ļ�Ľ�ͼ����ֻ�ܽ�ȡȫ����[pick](arkts-arkui-screenshot-pick-f.md#pick-1)�ӿڿ�ʵ�����������<br/> |
| [pick](arkts-arkui-screenshot-pick-f.md#pick-1) | ��ȡ��Ļ��ͼ����ǰ��֧�ֻ�ȡdisplayIdΪ0����Ļ��ͼ�������Ҫ����չ����ͼ������ͨ��[capture](arkts-arkui-screenshot-capture-f.md#capture-1)�ӿ�ʵ�֣���ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[save](arkts-arkui-screenshot-save-f-sys.md#save-1) | ��ȡ��Ļ��ͼ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[save](arkts-arkui-screenshot-save-f-sys.md#save-2) | ��ȡ��Ļ��ͼ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[save](arkts-arkui-screenshot-save-f-sys.md#save-3) | ��ȡ��Ļ��ͼ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[saveHdrPicture](arkts-arkui-screenshot-savehdrpicture-f-sys.md#saveHdrPicture-1) | ��ȡ��Ļ��ͼ��ʹ��Promise�첽�ص���SDRΪ��׼��̬��Χͼ��HDRΪ�߶�̬��Χͼ��<br/><br/>- ������������HDR��Դ������HDR��Դ���ڵ���ʱ������HDR�Ƿ������ýӿڷ���һ������SDR��HDR��PixelMap���顣<br/>- ��������������HDR��Դʱ����[save](screenshot.save(options: ScreenshotOptions, callback: AsyncCallback&lt;image.PixelMap&gt;))<br/>�ӿڷ���һ��SDR��PixelMap��ͬ���ýӿڷ��ذ���һ��SDR��PixelMap���顣ͬʱ�ýӿڲ��߱�<br/>[save](screenshot.save(options: ScreenshotOptions, callback: AsyncCallback&lt;image.PixelMap&gt;))�ӿڵĲü������졢��ת���ܡ�<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CaptureOption](arkts-arkui-screenshot-captureoption-i.md) | ���ý�ȡͼ�����Ϣ��<br/> |
| <!--DelRow-->[HdrScreenshotOptions](arkts-arkui-screenshot-hdrscreenshotoptions-i-sys.md) | ���ý�ȡHDRͼ�����Ϣ��<br/> |
| [PickInfo](arkts-arkui-screenshot-pickinfo-i.md) | ��ȡͼ�����Ϣ��<br/> |
| [Rect](arkts-arkui-screenshot-rect-i.md) | ��ʾ��ȡͼ�������<br/> |
| <!--DelRow-->[ScreenshotOptions](arkts-arkui-screenshot-screenshotoptions-i-sys.md) | ���ý�ȡͼ�����Ϣ��<br/> |
| <!--DelRow-->[Size](arkts-arkui-screenshot-size-i-sys.md) | ��ʾ��ȡͼ��Ĵ�С��<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[DisplayIntentType](arkts-arkui-screenshot-displayintenttype-e-sys.md) | ö�ٽ�ͼ��ʾ��ͼ���͡�<br/> |

