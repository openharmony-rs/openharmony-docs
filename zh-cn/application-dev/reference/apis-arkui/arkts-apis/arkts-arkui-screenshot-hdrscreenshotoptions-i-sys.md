# HdrScreenshotOptions（系统接口）

���ý�ȡHDRͼ�����Ϣ��

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## displayId

```TypeScript
displayId?: number
```

��ʾ��ȡͼ�����ʾ�豸[Display](arkts-arkui-display-displaystate-e.md#DisplayState)��ID�ţ��ò���ӦΪ������Ĭ��Ϊ0��

**类型：** number

**默认值：** The ID of the current display. The value is a positive integer greater than or equal to 0.

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## displayIntent

```TypeScript
displayIntent?: DisplayIntentType
```

��ȡͼ�����ʾ���͡�

**类型：** DisplayIntentType

**默认值：** DisplayIntentType.CANONICAL

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## isCaptureFullOfScreen

```TypeScript
isCaptureFullOfScreen?: boolean
```

��ʾ�Ƿ��ȡ��ǰ������������DisplayId��Ӧ���߼���������һ�����������ж��DisplayId�ĳ�����true��ʾ��ȡ������������false��ʾֻ��ȡDisplayId����������߼�����Ĭ��ֵΪfalse��

**类型：** boolean

**默认值：** false

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## isNotificationNeeded

```TypeScript
isNotificationNeeded?: boolean
```

��ʾ��ȡͼ��֮���Ƿ��ͽ���֪ͨ��true��ʾ���ͽ���֪ͨ��false��ʾ�����ͽ���֪ͨ��Ĭ��ֵΪtrue������֪ͨ����ͨ��
[captureStatusChange](arkts-arkui-display-on-f.md#on-7)�ӿ�
������

**类型：** boolean

**默认值：** true

**起始版本：** 20

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

