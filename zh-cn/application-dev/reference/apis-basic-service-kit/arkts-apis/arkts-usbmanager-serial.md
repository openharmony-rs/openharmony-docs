# @ohos.usbManager.serial

��ģ����Ҫ�ṩ���ڹ������ܣ������򿪺͹ر��豸�Ĵ��ڡ�д��Ͷ�ȡ���ݡ����úͻ�ȡ���ڵ����ò�����Ȩ�޹����ȡ�

**起始版本：** 19

**系统能力：** SystemCapability.USB.USBManager.Serial

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[addSerialRight](arkts-basicservices-serialmanager-addserialright-f-sys.md#addSerialRight-1) | ΪӦ�ó������ӷ��ʴ����豸Ȩ�ޡ�<br/>serialManager.requestSerialRight�ᴥ�����������û���Ȩ��addSerialRight���ᴥ������������ֱ������Ӧ�ó�������豸��Ȩ�ޡ�Ӧ���˳��Զ��Ƴ��Դ����豸�ķ���Ȩ�ޣ���Ӧ����������Ҫ����������<br/>Ȩ��<br/> |
| [cancelSerialRight](arkts-basicservices-serialmanager-cancelserialright-f.md#cancelSerialRight-1) | �Ƴ�Ӧ�ó�������ʱ���ʴ����豸��Ȩ�ޡ��˽ӿڻ����close�ر��Ѵ򿪵Ĵ��ڡ�<br/> |
| [close](arkts-basicservices-serialmanager-close-f.md#close-1) | �رմ��ڡ�<br/> |
| [getAttribute](arkts-basicservices-serialmanager-getattribute-f.md#getAttribute-1) | ��ȡָ�����ڵ����ò�����<br/> |
| [getPortList](arkts-basicservices-serialmanager-getportlist-f.md#getPortList-1) | ��ѯ�����豸�嵥�������豸���ƺͶ�Ӧ�Ķ˿ںš�<br/> |
| [hasSerialRight](arkts-basicservices-serialmanager-hasserialright-f.md#hasSerialRight-1) | ���Ӧ�ó����Ƿ���з��ʴ����豸��Ȩ�ޡ�Ӧ���˳���������ʱ����Ҫ����������Ȩ��<br/> |
| [open](arkts-basicservices-serialmanager-open-f.md#open-1) | �򿪴����豸��<br/> |
| [read](arkts-basicservices-serialmanager-read-f.md#read-1) | �Ӵ����豸�첽��ȡ���ݡ�ʹ��Promise�첽�ص���<br/> |
| [readSync](arkts-basicservices-serialmanager-readsync-f.md#readSync-1) | �Ӵ����豸ͬ����ȡ���ݡ�<br/> |
| [requestSerialRight](arkts-basicservices-serialmanager-requestserialright-f.md#requestSerialRight-1) | ����Ӧ�ó�����ʴ����豸��Ȩ�ޡ�Ӧ���˳��Զ��Ƴ��Դ����豸�ķ���Ȩ�ޣ���Ӧ����������Ҫ����������Ȩ��ʹ��Promise�첽�ص���<br/> |
| [setAttribute](arkts-basicservices-serialmanager-setattribute-f.md#setAttribute-1) | ���ô��ڵ����ò��������δ���ø÷�����ʹ��Ĭ�����ò����������ʣ�9600bps������λ��8��У��λ��0��ֹͣλ��1����<br/> |
| [write](arkts-basicservices-serialmanager-write-f.md#write-1) | �򴮿��豸�첽д���ݣ�ÿ��д�����ݳ��Ȳ�����4KB�����ݹ���ᵼ�����ݶ�ʧ�������ݽ���ְ�д�롣ʹ��Promise�첽�ص���<br/> |
| [writeSync](arkts-basicservices-serialmanager-writesync-f.md#writeSync-1) | �򴮿��豸ͬ��д���ݣ�ÿ��д�����ݳ��Ȳ�����4KB�����ݹ���ᵼ�����ݶ�ʧ�������ݽ���ְ�д�롣<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [SerialAttribute](arkts-basicservices-serialmanager-serialattribute-i.md) | ���ڵ����ò�����<br/> |
| [SerialPort](arkts-basicservices-serialmanager-serialport-i.md) | ���ڲ�����<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BaudRates](arkts-basicservices-serialmanager-baudrates-e.md) | Enumerates the baud rates.<br/> |
| [DataBits](arkts-basicservices-serialmanager-databits-e.md) | Enumerates the number of data bits.<br/> |
| [Parity](arkts-basicservices-serialmanager-parity-e.md) | Enumerates the parity check modes.<br/> |
| [StopBits](arkts-basicservices-serialmanager-stopbits-e.md) | Enumerates of the number of stop bits.<br/> |

