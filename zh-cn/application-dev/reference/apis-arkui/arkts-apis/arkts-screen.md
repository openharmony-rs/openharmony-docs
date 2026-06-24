# @ohos.screen

��ģ���ṩ������Ļ��һЩ����������������ȡ��Ļ���󣬼�����Ļ�仯������������������Ļ�ȡ�

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[createVirtualScreen](arkts-arkui-screen-createvirtualscreen-f-sys.md#createVirtualScreen-1) | ����������Ļ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[createVirtualScreen](arkts-arkui-screen-createvirtualscreen-f-sys.md#createVirtualScreen-2) | ����������Ļ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[destroyVirtualScreen](arkts-arkui-screen-destroyvirtualscreen-f-sys.md#destroyVirtualScreen-1) | ����������Ļ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[destroyVirtualScreen](arkts-arkui-screen-destroyvirtualscreen-f-sys.md#destroyVirtualScreen-2) | ����������Ļ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getAllScreens](arkts-arkui-screen-getallscreens-f-sys.md#getAllScreens-1) | ��ȡ���е���Ļ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getAllScreens](arkts-arkui-screen-getallscreens-f-sys.md#getAllScreens-2) | ��ȡ���е���Ļ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[isScreenRotationLocked](arkts-arkui-screen-isscreenrotationlocked-f-sys.md#isScreenRotationLocked-1) | ��ѯ��ǰ�Զ�ת���Ƿ�������ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[isScreenRotationLocked](arkts-arkui-screen-isscreenrotationlocked-f-sys.md#isScreenRotationLocked-2) | ��ѯ��ǰ�Զ�ת���Ƿ�������ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[makeExpand](arkts-arkui-screen-makeexpand-f-sys.md#makeExpand-1) | ����Ļ����Ϊ��չģʽ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[makeExpand](arkts-arkui-screen-makeexpand-f-sys.md#makeExpand-2) | ����Ļ����Ϊ��չģʽ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[makeMirror](arkts-arkui-screen-makemirror-f-sys.md#makeMirror-1) | ����Ļ����Ϊ����ģʽ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[makeMirror](arkts-arkui-screen-makemirror-f-sys.md#makeMirror-2) | ����Ļ����Ϊ����ģʽ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[makeMirrorWithRegion](arkts-arkui-screen-makemirrorwithregion-f-sys.md#makeMirrorWithRegion-1) | ����Ļ��ĳһ������������Ϊ����ģʽ��ʹ��Promise�첽�ص������øýӿں󣬲������ٽ�����Ļ����ת/�۵���������ܵ��¾��������쳣��<br/> |
| <!--DelRow-->[makeUnique](arkts-arkui-screen-makeunique-f-sys.md#makeUnique-1) | ����Ļ����Ϊ��Դģʽ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[off](arkts-arkui-screen-off-f-sys.md#off-1) | �ر���Ļ״̬�仯�ļ�����<br/> |
| <!--DelRow-->[off](arkts-arkui-screen-off-f-sys.md#off-2) | �ر���Ļ״̬�仯�ļ�����<br/> |
| <!--DelRow-->[off](arkts-arkui-screen-off-f-sys.md#off-3) | �ر���Ļ״̬�仯�ļ�����<br/> |
| <!--DelRow-->[on](arkts-arkui-screen-on-f-sys.md#on-1) | ������Ļ״̬�仯�ļ�����<br/> |
| <!--DelRow-->[on](arkts-arkui-screen-on-f-sys.md#on-2) | ������Ļ״̬�仯�ļ�����<br/> |
| <!--DelRow-->[on](arkts-arkui-screen-on-f-sys.md#on-3) | ������Ļ״̬�仯�ļ�����<br/> |
| <!--DelRow-->[resizeVirtualScreen](arkts-arkui-screen-resizevirtualscreen-f-sys.md#resizeVirtualScreen-1) | �޸�ָ���������ĳߴ磬ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setMultiScreenMode](arkts-arkui-screen-setmultiscreenmode-f-sys.md#setMultiScreenMode-1) | ������չ��Ļ����ʾģʽ������/��չ����ʹ��Promise�첽�ص���primaryScreenId��secondaryScreenId��Ϊ0ʱ��������չ����ʾ��<br/> |
| <!--DelRow-->[setMultiScreenRelativePosition](arkts-arkui-screen-setmultiscreenrelativeposition-f-sys.md#setMultiScreenRelativePosition-1) | ������չģʽ�£�������������չ��Ļ��λ����Ϣ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setScreenPrivacyMaskImage](arkts-arkui-screen-setscreenprivacymaskimage-f-sys.md#setScreenPrivacyMaskImage-1) | ������Ļ����˽�ɰ�ͼƬ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setScreenRotationLocked](arkts-arkui-screen-setscreenrotationlocked-f-sys.md#setScreenRotationLocked-1) | �����Զ�ת�������Ƿ�������ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[setScreenRotationLocked](arkts-arkui-screen-setscreenrotationlocked-f-sys.md#setScreenRotationLocked-2) | �����Զ�ת�������Ƿ�������ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setVirtualScreenSurface](arkts-arkui-screen-setvirtualscreensurface-f-sys.md#setVirtualScreenSurface-1) | ����������Ļ��surface����ʾ��ǰ������������ʾ��Ӧsurface�е����ݣ�ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[setVirtualScreenSurface](arkts-arkui-screen-setvirtualscreensurface-f-sys.md#setVirtualScreenSurface-2) | ����������Ļ��surface����ʾ��ǰ������������ʾ��Ӧsurface�е����ݣ�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[stopExpand](arkts-arkui-screen-stopexpand-f-sys.md#stopExpand-1) | ֹͣ��Ļ����չģʽ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[stopExpand](arkts-arkui-screen-stopexpand-f-sys.md#stopExpand-2) | ֹͣ��Ļ����չģʽ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[stopMirror](arkts-arkui-screen-stopmirror-f-sys.md#stopMirror-1) | ֹͣ��Ļ�ľ���ģʽ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[stopMirror](arkts-arkui-screen-stopmirror-f-sys.md#stopMirror-2) | ֹͣ��Ļ�ľ���ģʽ��ʹ��Promise�첽�ص���<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[ExpandOption](arkts-arkui-screen-expandoption-i-sys.md) | ��չ��Ļ�Ĳ�����<br/> |
| <!--DelRow-->[MultiScreenPositionOptions](arkts-arkui-screen-multiscreenpositionoptions-i-sys.md) | ��Ļλ����Ϣ��<br/> |
| <!--DelRow-->[OrientationOptions](arkts-arkui-screen-orientationoptions-i-sys.md) | ������ת��Ϊ�Ĳ���<br/> |
| <!--DelRow-->[Rect](arkts-arkui-screen-rect-i-sys.md) | ������Ϣ��<br/> |
| <!--DelRow-->[Screen](arkts-arkui-screen-screen-i-sys.md) | [������](../../../../displaymanager/display-terminology.md#������)��Ļʵ����<br/><br/>����APIʾ���ж�����ʹ��[getAllScreens()](screen.getAllScreens(callback: AsyncCallback&lt;Array&lt;Screen&gt;&gt;))��<br/>[createVirtualScreen()](screen.createVirtualScreen(options:VirtualScreenOption, callback: AsyncCallback&lt;Screen&gt;))<br/>�е���һ������ȡ��Screenʵ������ͨ����ʵ�����ö�Ӧ������<br/> |
| <!--DelRow-->[ScreenModeInfo](arkts-arkui-screen-screenmodeinfo-i-sys.md) | ��Ļ��ʾģʽ��Ϣ��<br/> |
| <!--DelRow-->[VirtualScreenOption](arkts-arkui-screen-virtualscreenoption-i-sys.md) | ����������Ļ�Ĳ�����<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[MultiScreenMode](arkts-arkui-screen-multiscreenmode-e-sys.md) | ��Ļģʽö�١�<br/> |
| <!--DelRow-->[Orientation](arkts-arkui-screen-orientation-e-sys.md) | ��Ļ����ö�١�<br/> |
| <!--DelRow-->[ScreenSourceMode](arkts-arkui-screen-screensourcemode-e-sys.md) | ��Ļ��ʾ������Դģʽö�١�<br/> |

