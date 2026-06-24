# ScreenshotOptions（系统接口）

���ý�ȡͼ�����Ϣ��

**起始版本：** 7

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## displayId

```TypeScript
displayId?: number
```

��ʾ��ȡͼ�����ʾ�豸[Display](arkts-arkui-display-displaystate-e.md#DisplayState)��ID�ţ��ò���ӦΪ������

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## imageSize

```TypeScript
imageSize?: Size
```

��ʾ��ȡͼ������򣬲���ֵĬ�Ϸ���displayId�����߼���������

**类型：** Size

**起始版本：** 7

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## isCaptureFullOfScreen

```TypeScript
isCaptureFullOfScreen?: boolean
```

��ʾ�Ƿ��ȡ��ǰScreen�ϵ�����display������һ��Screen���ж��display�ĳ�����Ϊtrue��ʾ��ȡ����Screen��false��ֻ��ȡdisplayId�����߼���������Ĭ��ֵΪfalse��

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## isNotificationNeeded

```TypeScript
isNotificationNeeded?: boolean
```

��ʾ��ȡͼ��֮���Ƿ��ͽ���֪ͨ��true��ʾ���ͽ���֪ͨ��false��ʾ�����ͽ���֪ͨ��Ĭ��ֵΪtrue������֪ͨ����ͨ��
[captureStatusChange](arkts-arkui-display-on-f.md#on-7)�ӿ�
������

**类型：** boolean

**起始版本：** 14

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## rotation

```TypeScript
rotation?: number
```

��ʾ��ȡͼ���Ҫ��ת�ĽǶȣ���ǰ��֧������ֵΪ0��Ĭ��ֵΪ0��

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## screenRect

```TypeScript
screenRect?: Rect
```

��ʾ��ȡͼ������򣬲���ֵĬ�Ϸ���displayId�����߼���������

**类型：** Rect

**起始版本：** 7

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

