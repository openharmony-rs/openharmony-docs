# tags

֧��traceʹ�ó����ı�ǩ���û���ͨ��hitraceץȡָ����ǩ��trace���ݡ�

> **ע��**  
>  
> ���±�ǩʵ��ֵ��ϵͳ���壬������汾�����������ı䣬Ϊ������������ּ��������⣬��������Ӧֱ��ʹ�ñ�ǩ���ƶ��Ǳ�ǩ��ֵ��

**起始版本：** 12

<!--Device-hidebug-namespace tags--><!--Device-hidebug-namespace tags-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## 汇总

### 常量

| 名称 | 说明 |
| --- | --- |
| [ABILITY_MANAGER](arkts-performanceanalysis-tags-con.md#ability_manager) | ����������ǩ��hitrace�����й��߶�ӦtagName:ability�� |
| [ARKUI](arkts-performanceanalysis-tags-con.md#arkui) | ArkUI������ܱ�ǩ��hitrace�����й��߶�ӦtagName:ace�� |
| [ARK](arkts-performanceanalysis-tags-con.md#ark) | JSVM�������ǩ��hitrace�����й��߶�ӦtagName:ark�� |
| [BLUETOOTH](arkts-performanceanalysis-tags-con.md#bluetooth) | ������ǩ��hitrace�����й��߶�ӦtagName:bluetooth�� |
| [COMMON_LIBRARY](arkts-performanceanalysis-tags-con.md#common_library) | ��������ϵͳ��ǩ��hitrace�����й��߶�ӦtagName:commonlibrary�� |
| [DISTRIBUTED_HARDWARE_DEVICE_MANAGER](arkts-performanceanalysis-tags-con.md#distributed_hardware_device_manager) | �ֲ�ʽӲ���豸������ǩ��hitrace�����й��߶�ӦtagName:devicemanager�� |
| [DISTRIBUTED_AUDIO](arkts-performanceanalysis-tags-con.md#distributed_audio) | �ֲ�ʽ��Ƶ��ǩ��hitrace�����й��߶�ӦtagName:daudio�� |
| [DISTRIBUTED_CAMERA](arkts-performanceanalysis-tags-con.md#distributed_camera) | �ֲ�ʽ�����ǩ��hitrace�����й��߶�ӦtagName:dcamera�� |
| [DISTRIBUTED_DATA](arkts-performanceanalysis-tags-con.md#distributed_data) | �ֲ�ʽ���ݹ���ģ���ǩ��hitrace�����й��߶�ӦtagName:distributeddatamgr�� |
| [DISTRIBUTED_HARDWARE_FRAMEWORK](arkts-performanceanalysis-tags-con.md#distributed_hardware_framework) | �ֲ�ʽӲ����ܱ�ǩ��hitrace�����й��߶�ӦtagName:dhfwk�� |
| [DISTRIBUTED_INPUT](arkts-performanceanalysis-tags-con.md#distributed_input) | �ֲ�ʽ�����ǩ��hitrace�����й��߶�ӦtagName:dinput�� |
| [DISTRIBUTED_SCREEN](arkts-performanceanalysis-tags-con.md#distributed_screen) | �ֲ�ʽ��Ļ��ǩ��hitrace�����й��߶�ӦtagName:dscreen�� |
| [DISTRIBUTED_SCHEDULER](arkts-performanceanalysis-tags-con.md#distributed_scheduler) | �ֲ�ʽ��������ǩ��hitrace�����й��߶�ӦtagName:dsched�� |
| [FFRT](arkts-performanceanalysis-tags-con.md#ffrt) | FFRT�����ǩ��hitrace�����й��߶�ӦtagName:ffrt�� |
| [FILE_MANAGEMENT](arkts-performanceanalysis-tags-con.md#file_management) | �ļ�����ϵͳ��ǩ��hitrace�����й��߶�ӦtagName:filemanagement�� |
| [GLOBAL_RESOURCE_MANAGER](arkts-performanceanalysis-tags-con.md#global_resource_manager) | ȫ����Դ������ǩ��hitrace�����й��߶�ӦtagName:gresource�� |
| [GRAPHICS](arkts-performanceanalysis-tags-con.md#graphics) | ͼ��ģ���ǩ��hitrace�����й��߶�ӦtagName:graphic�� |
| [HDF](arkts-performanceanalysis-tags-con.md#hdf) | HDF��ϵͳ��ǩ��hitrace�����й��߶�ӦtagName:hdf�� |
| [MISC](arkts-performanceanalysis-tags-con.md#misc) | MISCģ���ǩ��hitrace�����й��߶�ӦtagName:misc�� |
| [MULTIMODAL_INPUT](arkts-performanceanalysis-tags-con.md#multimodal_input) | ��ģ̬����ģ���ǩ��hitrace�����й��߶�ӦtagName:multimodalinput�� |
| [NET](arkts-performanceanalysis-tags-con.md#net) | �����ǩ��hitrace�����й��߶�ӦtagName:net�� |
| [NOTIFICATION](arkts-performanceanalysis-tags-con.md#notification) | ֪ͨģ���ǩ��hitrace�����й��߶�ӦtagName:notification�� |
| [NWEB](arkts-performanceanalysis-tags-con.md#nweb) | Nweb��ǩ��hitrace�����й��߶�ӦtagName:nweb�� |
| [OHOS](arkts-performanceanalysis-tags-con.md#ohos) | OHOSͨ�ñ�ǩ��hitrace�����й��߶�ӦtagName:ohos�� |
| [POWER_MANAGER](arkts-performanceanalysis-tags-con.md#power_manager) | ��Դ������ǩ��hitrace�����й��߶�ӦtagName:power�� |
| [RPC](arkts-performanceanalysis-tags-con.md#rpc) | RPC��ǩ��hitrace�����й��߶�ӦtagName:rpc�� |
| [SAMGR](arkts-performanceanalysis-tags-con.md#samgr) | ϵͳ����������ǩ��hitrace�����й��߶�ӦtagName:samgr�� |
| [WINDOW_MANAGER](arkts-performanceanalysis-tags-con.md#window_manager) | ���ڹ�����ǩ��hitrace�����й��߶�ӦtagName:window�� |
| [AUDIO](arkts-performanceanalysis-tags-con.md#audio) | ��Ƶģ���ǩ��hitrace�����й��߶�ӦtagName:zaudio�� |
| [CAMERA](arkts-performanceanalysis-tags-con.md#camera) | ���ģ���ǩ��hitrace�����й��߶�ӦtagName:zcamera�� |
| [IMAGE](arkts-performanceanalysis-tags-con.md#image) | ͼƬģ���ǩ��hitrace�����й��߶�ӦtagName:zimage�� |
| [MEDIA](arkts-performanceanalysis-tags-con.md#media) | ý��ģ���ǩ��hitrace�����й��߶�ӦtagName:zmedia�� |

