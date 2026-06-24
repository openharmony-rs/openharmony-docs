# update

## update

```TypeScript
function update(handle: number, token?: Uint8Array, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

update������Կ�ӿڡ�ʹ��callback�첽�ص���

huks.init��huks.update��huks.finishΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.updateSession<sup>9+</sup>](arkts-universalkeystore-huks-updatesession-f.md#updateSession-2)
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** updateSession(

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | Update������uint64���͵�handleֵ�� |
| token | Uint8Array | 否 | Update������token�� |
| options | HuksOptions | 是 | Update�����Ĳ������ϡ� |
| callback | AsyncCallback&lt;HuksResult&gt; | 是 | �ص�����������Կ����update�ɹ�ʱ��errΪundefined��dataΪ��ȡ����HuksResult������Ϊ������� |


## update

```TypeScript
function update(handle: number, token?: Uint8Array, options: HuksOptions): Promise<HuksResult>
```

update������Կ�ӿڡ�ʹ��Promise�첽�ص���

huks.init��huks.update��huks.finishΪ����ʽ�ӿڣ���Ҫһ��ʹ�á�

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [huks.updateSession<sup>9+</sup>](arkts-universalkeystore-huks-updatesession-f.md#updateSession-3)
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** updateSession(handle:

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | Update������uint64���͵�handleֵ�� |
| token | Uint8Array | 否 | Update������token�� |
| options | HuksOptions | 是 | Update�����Ĳ������ϡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksResult&gt; | Promise���󣬷���HuksResult�� |

