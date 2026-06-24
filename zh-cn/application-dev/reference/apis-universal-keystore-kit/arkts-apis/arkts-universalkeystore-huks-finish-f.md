# finish

## finish

```TypeScript
function finish(handle: number, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

finish������Կ�ӿڡ�ʹ��callback�첽�ص���

huks.init��huks.update��huks.finishΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.finishSession<sup>9+</sup>](arkts-universalkeystore-huks-finishsession-f.md#finishSession-1)
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** finishSession(handle:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | Finish������uint64���͵�handleֵ�� |
| options | HuksOptions | 是 | Finish�Ĳ������ϡ� |
| callback | AsyncCallback&lt;HuksResult&gt; | 是 | �ص�����������Կ����finish�ɹ�ʱ��errΪundefined��dataΪ��ȡ����HuksResult������Ϊ������� |


## finish

```TypeScript
function finish(handle: number, options: HuksOptions): Promise<HuksResult>
```

finish������Կ�ӿڡ�ʹ��Promise�첽�ص���

huks.init��huks.update��huks.finishΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.finishSession<sup>9+</sup>](arkts-universalkeystore-huks-finishsession-f.md#finishSession-2)
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** finishSession(

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | Finish������uint64���͵�handleֵ�� |
| options | HuksOptions | 是 | Finish�����Ĳ������ϡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksResult&gt; | Promise���󣬷���HuksResult�� |

