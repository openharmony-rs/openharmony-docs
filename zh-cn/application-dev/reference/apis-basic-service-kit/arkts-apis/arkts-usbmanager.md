# @ohos.usbManager

��ģ����Ҫ�ṩ����USB�豸����ع��ܣ��������豸�ϲ�ѯUSB�豸�б����������ݴ��䡢��������䡢Ȩ�޿��Ƶȣ����豸�϶˿ڹ����������л�����ѯ�ȡ�

> **ʹ��˵��**
>
> ���ǲ�������Ϊ[usbManager.USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md#USBDevicePipe)�Ľӿ�,����Ҫִ�����²�����
> **��ʹ�ýӿ�ǰ��**
> 1. ����[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)��ȡ�豸�б���
> 2. ����[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md#requestRight-1)��ȡ����Ȩ�ޡ�
> 3. ����[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice-1)�õ�[usbManager.USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md#USBDevicePipe)��Ϊ������
> **��ʹ�ýӿں�**
> ����[usbManager.closePipe](usbManager.closePipe(USBDevicePipe: pipe))�ر��豸��Ϣ����ͨ����

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[addAccessoryRight](arkts-basicservices-usbmanager-addaccessoryright-f-sys.md#addAccessoryRight-1) | ΪӦ�ó������ӷ���USB��requestAccessoryRight��Ȩ�ޡ�<br/>[usbManager.]{(@link usbManager.requestAccessoryRight)}�ᴥ�����������û���Ȩ��addAccessoryRight���ᴥ������������ֱ������Ӧ�ó�������豸��Ȩ�ޡ�<br/> |
| <!--DelRow-->[addDeviceAccessRight](arkts-basicservices-usbmanager-adddeviceaccessright-f-sys.md#addDeviceAccessRight-1) | ���������������豸��Ȩ�ޡ�ϵͳӦ��Ĭ��ӵ�з����豸Ȩ�ޣ����ô˽ӿڲ������Ӱ�졣<br/>[usbManager.requestRight]{(@link usbManager.requestRight)}�ᴥ�����������û���Ȩ��addDeviceAccessRight���ᴥ�����򣬶���ֱ�����������������豸��Ȩ�ޡ�<br/> |
| [bulkTransfer](arkts-basicservices-usbmanager-bulktransfer-f.md#bulkTransfer-1) | �������䡣ʹ��Promise�첽�ص���<br/><br/>&gt; **˵����** <br/>&gt;<br/>&gt; ������������Ĵ�����������������pipe��endpoint��buffer��timeout���������200KB���£�������������ᵼ�´���ʧ�ܷ���-1��<br/>&gt;<br/>&gt; �ڵ��ýӿ�ǰ��Ҫͨ��<br/>&gt; [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md#claimInterface-1)<br/>&gt; claimͨ�Žӿڡ�<br/> |
| [cancelAccessoryRight](arkts-basicservices-usbmanager-cancelaccessoryright-f.md#cancelAccessoryRight-1) | ȡ����ǰӦ�ó������USB�����Ȩ�ޡ�<br/>��Ҫ����[usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md#getAccessoryList-1)��ȡ����б����õ�<br/>[USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md#USBAccessory)��Ϊ������<br/> |
| [claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md#claimInterface-1) | ������USB�豸ĳ���ӿڵĿ���Ȩ��<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��USB����У�claim interface��һ������������ָ����Ӧ�ó����������ϵͳ��ĳ��USB�ӿڴ��ں��������ͷŲ������û��ռ������ơ�&lt;br&gt;<br/>&gt; &gt; �����õ���claimͨ�Žӿڶ���ʾclaim interface������<br/> |
| [closeAccessory](arkts-basicservices-usbmanager-closeaccessory-f.md#closeAccessory-1) | �ر�����ļ���������<br/>��Ҫ����[usbManager.openAccessory](arkts-basicservices-usbmanager-openaccessory-f.md#openAccessory-1)��ȡ����б����õ�<br/>[USBAccessoryHandle](arkts-basicservices-usbmanager-usbaccessoryhandle-i.md#USBAccessoryHandle)��Ϊ������<br/> |
| [closePipe](arkts-basicservices-usbmanager-closepipe-f.md#closePipe-1) | �ر��豸��Ϣ����ͨ����<br/><br/>1. ��Ҫ����[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)��ȡ�豸�б���<br/>2. ����[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md#requestRight-1)��ȡ�豸����Ȩ�ޣ�<br/>3. ����[usbManager.connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice-1)�õ�devicepipe��Ϊ������<br/> |
| [connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md#connectDevice-1) | ����getDevices()���ص��豸��Ϣ��USB�豸�����USB�����쳣�����ܷ���`undefined`��ע����Ҫ�Խӿڷ���ֵ���пմ�����<br/><br/>1. ��Ҫ����[usbManager.getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1)��ȡ�豸��Ϣ�Լ�device;<br/>2. ����[usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md#requestRight-1)����ʹ�ø��豸��Ȩ�ޡ�<br/> |
| [controlTransfer](arkts-basicservices-usbmanager-controltransfer-f.md#controlTransfer-1) | ���ƴ��䡣ʹ��Promise�첽�ص���<br/> |
| [getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md#getAccessoryList-1) | ��ȡ��ǰ�ѽ���������USB����б���<br/> |
| <!--DelRow-->[getCurrentFunctions](arkts-basicservices-usbmanager-getcurrentfunctions-f-sys.md#getCurrentFunctions-1) | ���豸ģʽ�£���ȡ��ǰ��USB�����б�������������롣������ģʽ�ر�ʱ�����û���豸���룬�ӿڿ��ܷ���`undefined`��ע����Ҫ�Խӿڷ���ֵ���пմ�����<br/> |
| <!--DelRow-->[getDeviceFunctions](arkts-basicservices-usbmanager-getdevicefunctions-f-sys.md#getDeviceFunctions-1) | ���豸ģʽ�£���ȡ��ǰ��USB�����б�������������롣������ģʽ�ر�ʱ�����û���豸���룬�ӿڿ��ܷ���`undefined`��ע����Ҫ�Խӿڷ���ֵ���пմ�����<br/> |
| [getDevices](arkts-basicservices-usbmanager-getdevices-f.md#getDevices-1) | ��ȡ�������豸��USB�豸�б���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ����Ӧ��û��Ȩ�޻�ȡserial�ֶζ�ȡ�豸���кţ���Ҫͨ��<br/>&gt; [usbManager.requestRight](arkts-basicservices-usbmanager-requestright-f.md#requestRight-1)����Ȩ�޺����з�����ƴ����ȡ��<br/> |
| [getFileDescriptor](arkts-basicservices-usbmanager-getfiledescriptor-f.md#getFileDescriptor-1) | ��ȡ�ļ���������<br/> |
| <!--DelRow-->[getFunctionsFromString](arkts-basicservices-usbmanager-getfunctionsfromstring-f-sys.md#getFunctionsFromString-1) | ���豸ģʽ�£����ַ�����ʽ��USB�����б�ת��Ϊ�������롣<br/> |
| <!--DelRow-->[getPortList](arkts-basicservices-usbmanager-getportlist-f-sys.md#getPortList-1) | ��ȡ��������USB�˿�������Ϣ��������ģʽ�ر�ʱ�����û���豸���룬�ӿڿ��ܷ���`undefined`��ע����Ҫ�Խӿڷ���ֵ���пմ�����<br/> |
| <!--DelRow-->[getPortSupportModes](arkts-basicservices-usbmanager-getportsupportmodes-f-sys.md#getPortSupportModes-1) | ��ȡָ���Ķ˿�֧�ֵ�ģʽ�б���������롣<br/> |
| <!--DelRow-->[getPorts](arkts-basicservices-usbmanager-getports-f-sys.md#getPorts-1) | ��ȡ��������USB�˿�������Ϣ��������ģʽ�ر�ʱ�����û���豸���룬�ӿڿ��ܷ���`undefined`��ע����Ҫ�Խӿڷ���ֵ���пմ�����<br/> |
| [getRawDescriptor](arkts-basicservices-usbmanager-getrawdescriptor-f.md#getRawDescriptor-1) | ��ȡԭʼ��USB�����������USB�����쳣�����ܷ���`undefined`��ע����Ҫ�Խӿڷ���ֵ���пմ�����<br/> |
| <!--DelRow-->[getStringFromFunctions](arkts-basicservices-usbmanager-getstringfromfunctions-f-sys.md#getStringFromFunctions-1) | ���豸ģʽ�£�������������ʽ��USB�����б�ת��Ϊ�ַ�����<br/> |
| <!--DelRow-->[getSupportedModes](arkts-basicservices-usbmanager-getsupportedmodes-f-sys.md#getSupportedModes-1) | ��ȡָ���Ķ˿�֧�ֵ�ģʽ�б���������롣<br/> |
| [hasAccessoryRight](arkts-basicservices-usbmanager-hasaccessoryright-f.md#hasAccessoryRight-1) | ���Ӧ�ó����Ƿ���Ȩ����USB�����<br/>��Ҫ����[usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md#getAccessoryList-1)��ȡ����б����õ�<br/>[USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md#USBAccessory)��Ϊ������<br/> |
| [hasRight](arkts-basicservices-usbmanager-hasright-f.md#hasRight-1) | �ж��Ƿ���Ȩ���ʸ��豸��<br/>�����ʹ���ߡ��������App��ϵͳ����Ȩ�����豸�򷵻�true����Ȩ�����豸�򷵻�false��<br/> |
| [openAccessory](arkts-basicservices-usbmanager-openaccessory-f.md#openAccessory-1) | ��ȡ��������������ļ���������֮�����ͨ��CoreFileKit�ṩ��read/write�ӿں��������ͨ�š�<br/>��Ҫ����[usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md#getAccessoryList-1)��ȡ����б����õ�<br/>[USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md#USBAccessory)��Ϊ������<br/> |
| [releaseInterface](arkts-basicservices-usbmanager-releaseinterface-f.md#releaseInterface-1) | �ͷ�claim����ͨ�Žӿڡ�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; �ڵ��øýӿ�ǰ��Ҫͨ��<br/>&gt; [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md#claimInterface-1)<br/>&gt; claimͨ�Žӿڡ�<br/> |
| [removeRight](arkts-basicservices-usbmanager-removeright-f.md#removeRight-1) | �Ƴ������������豸��Ȩ�ޡ�ϵͳӦ��Ĭ��ӵ�з����豸Ȩ�ޣ����ô˽ӿڲ������Ӱ�졣<br/> |
| [requestAccessoryRight](arkts-basicservices-usbmanager-requestaccessoryright-f.md#requestAccessoryRight-1) | Ϊָ��Ӧ�ó����������USB����ķ���Ȩ�ޡ�ʹ��Promise�첽�ص���<br/>��Ҫ����[usbManager.getAccessoryList](arkts-basicservices-usbmanager-getaccessorylist-f.md#getAccessoryList-1)��ȡ����б����õ�<br/>[USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md#USBAccessory)��Ϊ������<br/> |
| [requestRight](arkts-basicservices-usbmanager-requestright-f.md#requestRight-1) | ��������������ʱȨ���Է����豸��ʹ��Promise�첽�ص���ϵͳӦ��Ĭ��ӵ�з����豸Ȩ�ޣ�������ô˽ӿ����롣<br/> |
| [resetUsbDevice](arkts-basicservices-usbmanager-resetusbdevice-f.md#resetUsbDevice-1) | ����USB���衣<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ���ӿڵ��ú�����ô�ǰ���õ����ú��滻�ӿڣ����ڵ���֮ǰȷ�����ҵ���ѽ�����<br/> |
| [setConfiguration](arkts-basicservices-usbmanager-setconfiguration-f.md#setConfiguration-1) | �����豸���á�<br/> |
| <!--DelRow-->[setCurrentFunctions](arkts-basicservices-usbmanager-setcurrentfunctions-f-sys.md#setCurrentFunctions-1) | ���豸ģʽ�£����õ�ǰ��USB�����б���ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setDeviceFunctions](arkts-basicservices-usbmanager-setdevicefunctions-f-sys.md#setDeviceFunctions-1) | ���豸ģʽ�£����õ�ǰ��USB�����б���ʹ��Promise�첽�ص���<br/> |
| [setInterface](arkts-basicservices-usbmanager-setinterface-f.md#setInterface-1) | �����豸�ӿڡ�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; һ��USB�ӿڿ��ܴ��ڶ���ѡ��ģʽ��֧�ֶ�̬�л���ʹ�õĳ��������ݴ���ʱ��ͨ���ýӿڿ��������ö˵㣬ʹ�˵��봫������ƥ�䡣<br/>&gt;<br/>&gt; �ڵ��øýӿ�ǰ��Ҫͨ��<br/>&gt; [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md#claimInterface-1)<br/>&gt; claimͨ�Žӿڡ�<br/> |
| <!--DelRow-->[setPortRoleTypes](arkts-basicservices-usbmanager-setportroletypes-f-sys.md#setPortRoleTypes-1) | ����ָ���Ķ˿�֧�ֵĽ�ɫģʽ����������ɫ�����ݴ����ɫ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setPortRoles](arkts-basicservices-usbmanager-setportroles-f-sys.md#setPortRoles-1) | ����ָ���Ķ˿�֧�ֵĽ�ɫģʽ����������ɫ�����ݴ����ɫ��ʹ��Promise�첽�ص���<br/> |
| [usbCancelTransfer](arkts-basicservices-usbmanager-usbcanceltransfer-f.md#usbCancelTransfer-1) | ȡ���첽��������<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; �ýӿڵ���Ҫ����������ȡ����δ��ɵ�USB���ݴ���������usbSubmitTransfer�ύ�Ĵ��䣩��&lt;br&gt;<br/>&gt; &gt; �ڵ��øýӿ�ǰ��Ҫͨ��<br/>&gt; [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md#claimInterface-1)<br/>&gt; claimͨ�Žӿڡ�<br/> |
| [usbControlTransfer](arkts-basicservices-usbmanager-usbcontroltransfer-f.md#usbControlTransfer-1) | ���ƴ��䡣ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[usbFunctionsFromString](arkts-basicservices-usbmanager-usbfunctionsfromstring-f-sys.md#usbFunctionsFromString-1) | ���豸ģʽ�£����ַ�����ʽ��USB�����б�ת��Ϊ�������롣<br/> |
| <!--DelRow-->[usbFunctionsToString](arkts-basicservices-usbmanager-usbfunctionstostring-f-sys.md#usbFunctionsToString-1) | ���豸ģʽ�£�������������ʽ��USB�����б�ת��Ϊ�ַ�����<br/> |
| [usbSubmitTransfer](arkts-basicservices-usbmanager-usbsubmittransfer-f.md#usbSubmitTransfer-1) | �ύ�첽��������<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ���ӿ�Ϊ�첽�ӿڣ����ú����̷��أ�ʵ�ʶ�д�����Ľ���Իص��ķ�ʽ���ء�<br/>&gt;<br/>&gt; �ڵ��øýӿ�ǰ��Ҫͨ��<br/>&gt; [usbManager.claimInterface](arkts-basicservices-usbmanager-claiminterface-f.md#claimInterface-1)<br/>&gt; claimͨ�Žӿڡ�<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [SubmitTransferCallback](arkts-basicservices-usbmanager-submittransfercallback-i.md) | Usb�첽����ص���<br/> |
| [USBAccessory](arkts-basicservices-usbmanager-usbaccessory-i.md) | USB�����Ϣ��<br/> |
| [USBAccessoryHandle](arkts-basicservices-usbmanager-usbaccessoryhandle-i.md) | USB��������<br/> |
| [USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md) | USB���ã�һ��[USBDevice](arkts-basicservices-usbmanager-usbdevice-i.md#USBDevice)�п��Ժ��ж�����á�<br/> |
| [USBControlParams](arkts-basicservices-usbmanager-usbcontrolparams-i.md) | ���ƴ��������<br/> |
| [USBDevice](arkts-basicservices-usbmanager-usbdevice-i.md) | USB�豸��Ϣ��<br/> |
| [USBDevicePipe](arkts-basicservices-usbmanager-usbdevicepipe-i.md) | USB�豸��Ϣ����ͨ��������ȷ���豸��<br/> |
| [USBDeviceRequestParams](arkts-basicservices-usbmanager-usbdevicerequestparams-i.md) | ���ƴ��������<br/> |
| [USBEndpoint](arkts-basicservices-usbmanager-usbendpoint-i.md) | ͨ��USB���ͺͽ������ݵĶ˿ڡ�ͨ��[USBInterface](arkts-basicservices-usbmanager-usbinterface-i.md#USBInterface)��ȡ��<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��������������Endpoint���͵��ȡ�<br/>&gt;<br/>&gt; Э�����ʱ����type�����������ԡ�<br/> |
| [USBInterface](arkts-basicservices-usbmanager-usbinterface-i.md) | һ��[USBConfiguration](arkts-basicservices-usbmanager-usbconfiguration-i.md#USBConfiguration)�п��Ժ��ж��USBInterface��ÿ��USBInterface�ṩһ�����ܡ�<br/> |
| <!--DelRow-->[USBPort](arkts-basicservices-usbmanager-usbport-i-sys.md) | USB�豸�˿ڡ�<br/> |
| <!--DelRow-->[USBPortStatus](arkts-basicservices-usbmanager-usbportstatus-i-sys.md) | USB�豸�˿ڽ�ɫ��Ϣ��<br/> |
| [UsbDataTransferParams](arkts-basicservices-usbmanager-usbdatatransferparams-i.md) | ��Ϊͨ��USB���ݴ���ӿڣ��ͻ�����Ҫ�����������еĲ��������Է���������<br/> |
| [UsbIsoPacketDescriptor](arkts-basicservices-usbmanager-usbisopacketdescriptor-i.md) | ʵʱ����ģʽ�ص����صķְ���Ϣ��<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[DataRoleType](arkts-basicservices-usbmanager-dataroletype-e-sys.md) | Enumerates data role types.<br/> |
| <!--DelRow-->[FunctionType](arkts-basicservices-usbmanager-functiontype-e-sys.md) | Enumerates USB device function types.<br/> |
| <!--DelRow-->[PortModeType](arkts-basicservices-usbmanager-portmodetype-e-sys.md) | Enumerates USB port mode types.<br/> |
| <!--DelRow-->[PowerRoleType](arkts-basicservices-usbmanager-powerroletype-e-sys.md) | Enumerates power role types.<br/> |
| [USBControlRequestType](arkts-basicservices-usbmanager-usbcontrolrequesttype-e.md) | Enumerates control request types.<br/> |
| [USBRequestDirection](arkts-basicservices-usbmanager-usbrequestdirection-e.md) | Enumerates request directions.<br/> |
| [USBRequestTargetType](arkts-basicservices-usbmanager-usbrequesttargettype-e.md) | Enumerates request target types.<br/> |
| [UsbEndpointTransferType](arkts-basicservices-usbmanager-usbendpointtransfertype-e.md) | Enumerates USB transfer types.<br/> |
| [UsbTransferFlags](arkts-basicservices-usbmanager-usbtransferflags-e.md) | Enumerates USB transfer flags.<br/> |
| [UsbTransferStatus](arkts-basicservices-usbmanager-usbtransferstatus-e.md) | Enumerates the status code returned after data processing is complete.<br/> |

