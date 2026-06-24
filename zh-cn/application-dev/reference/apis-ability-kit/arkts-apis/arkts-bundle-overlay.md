# @ohos.bundle.overlay

��ģ���ṩoverlay����Ӧ�õ�[OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md#OverlayModuleInfo)��Ϣ��ѯ�Լ�����ʹ�ܵ�������

overlay����Ӧ��ָӦ���а�����overlay��Դ����overlay��Դ�����
[overlay����](../../../../quick-start/resource-categories-and-access.md#overlay����)��

> **˵����**
>
> ��ģ��ӿڽ�������stageģ�ͣ��ҽ�������[��̬overlay](../../../../quick-start/resource-categories-and-access.md#��̬overlay���÷�ʽ)��

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Overlay

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getOverlayModuleInfo](arkts-ability-overlay-getoverlaymoduleinfo-f.md#getOverlayModuleInfo-1) | ��ȡ��ǰӦ����overlay����module��OverlayModuleInfo��Ϣ��ʹ��callback�첽�ص���<br/> |
| [getOverlayModuleInfo](arkts-ability-overlay-getoverlaymoduleinfo-f.md#getOverlayModuleInfo-2) | ��ȡ��ǰӦ����overlay����module��OverlayModuleInfo��Ϣ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getOverlayModuleInfoByBundleName-1) | ��ȡָ��Ӧ��������module��OverlayModuleInfo��Ϣ��ʹ��callback�첽�ص���<br/><br/>ָ��Ӧ���ǵ��÷�����ʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getOverlayModuleInfoByBundleName-2) | ��ȡָ��Ӧ����ָ��module��OverlayModuleInfo��Ϣ��ʹ��callback�첽�ص���<br/><br/>ָ��Ӧ���ǵ��÷�����ʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getOverlayModuleInfoByBundleName-3) | ��ȡָ��Ӧ����ָ��module��OverlayModuleInfo��Ϣ��ʹ��promise�첽�ص���<br/><br/>ָ��Ӧ���ǵ��÷�����ʱ����ҪȨ�ޡ�<br/> |
| [getTargetOverlayModuleInfos](arkts-ability-overlay-gettargetoverlaymoduleinfos-f.md#getTargetOverlayModuleInfos-1) | ��ȡָ����Ŀ��module��������OverlayModuleInfo��overlay������moduleһ����Ϊ�豸�ϴ��ڵķ�overlay������module�ṩ���ǵ���Դ�ļ������з�overlay������module������Ŀ��<br/>module��ʹ��callback�첽�ص���<br/> |
| [getTargetOverlayModuleInfos](arkts-ability-overlay-gettargetoverlaymoduleinfos-f.md#getTargetOverlayModuleInfos-2) | ��ȡָ����Ŀ��module��������OverlayModuleInfo��overlay������moduleһ����Ϊ�豸�ϴ��ڵķ�overlay������module�ṩ���ǵ���Դ�ļ������з�overlay������module������Ŀ��<br/>module��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#getTargetOverlayModuleInfosByBundleName-1) | ��ȡָ��Ӧ��������module����������OverlayModuleInfo��Ϣ��ʹ��callback�첽�ص���<br/><br/>ָ��Ӧ���ǵ��÷�����ʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#getTargetOverlayModuleInfosByBundleName-2) | ��ȡָ��Ӧ����ָ��module����������OverlayModuleInfo��Ϣ��ʹ��callback�첽�ص���<br/><br/>ָ��Ӧ���ǵ��÷�����ʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#getTargetOverlayModuleInfosByBundleName-3) | ��ȡָ��Ӧ����ָ��module����������OverlayModuleInfo��Ϣ��ʹ��promise�첽�ص���<br/><br/>ָ��Ӧ���ǵ��÷�����ʱ����ҪȨ�ޡ�<br/> |
| [setOverlayEnabled](arkts-ability-overlay-setoverlayenabled-f.md#setOverlayEnabled-1) | ���õ�ǰӦ����overlay module�Ľ���ʹ��״̬��ʹ��callback�첽�ص���<br/> |
| [setOverlayEnabled](arkts-ability-overlay-setoverlayenabled-f.md#setOverlayEnabled-2) | ���õ�ǰӦ����overlay����module�Ľ���ʹ��״̬��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setOverlayEnabledByBundleName](arkts-ability-overlay-setoverlayenabledbybundlename-f-sys.md#setOverlayEnabledByBundleName-1) | ����ָ��Ӧ�õ�overlay module�Ľ���ʹ��״̬��ʹ��callback�첽�ص���<br/><br/>ָ��Ӧ���ǵ��÷�����ʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[setOverlayEnabledByBundleName](arkts-ability-overlay-setoverlayenabledbybundlename-f-sys.md#setOverlayEnabledByBundleName-2) | ����ָ��Ӧ�õ�overlay module�Ľ���ʹ��״̬��ʹ��Promise�첽�ص���<br/><br/>ָ��Ӧ���ǵ��÷�����ʱ����ҪȨ�ޡ�<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OverlayModuleInfo](arkts-ability-overlay-overlaymoduleinfo-t.md) | OverlayModuleInfo��Ϣ��<br/> |

