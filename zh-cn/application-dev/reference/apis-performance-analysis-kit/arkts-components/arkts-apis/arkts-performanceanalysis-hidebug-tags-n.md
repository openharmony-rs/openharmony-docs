# tags

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## 汇总

### 常量

| 名称 | 说明 |
| --- | --- |
| [ABILITY_MANAGER](arkts-performanceanalysis-tags-con.md#ability_manager) | 能力管理标签，hitrace命令行工具对应tagName:ability。 |
| [ARKUI](arkts-performanceanalysis-tags-con.md#arkui) | ArkUI开发框架标签，hitrace命令行工具对应tagName:ace。 |
| [ARK](arkts-performanceanalysis-tags-con.md#ark) | JSVM虚拟机标签，hitrace命令行工具对应tagName:ark。 |
| [BLUETOOTH](arkts-performanceanalysis-tags-con.md#bluetooth) | 蓝牙标签，hitrace命令行工具对应tagName:bluetooth。 |
| [COMMON_LIBRARY](arkts-performanceanalysis-tags-con.md#common_library) | 公共库子系统标签，hitrace命令行工具对应tagName:commonlibrary。 |
| [DISTRIBUTED_HARDWARE_DEVICE_MANAGER](arkts-performanceanalysis-tags-con.md#distributed_hardware_device_manager) | 分布式硬件设备管理标签，hitrace命令行工具对应tagName:devicemanager。 |
| [DISTRIBUTED_AUDIO](arkts-performanceanalysis-tags-con.md#distributed_audio) | 分布式音频标签，hitrace命令行工具对应tagName:daudio。 |
| [DISTRIBUTED_CAMERA](arkts-performanceanalysis-tags-con.md#distributed_camera) | 分布式相机标签，hitrace命令行工具对应tagName:dcamera。 |
| [DISTRIBUTED_DATA](arkts-performanceanalysis-tags-con.md#distributed_data) | 分布式数据管理模块标签，hitrace命令行工具对应tagName:distributeddatamgr。 |
| [DISTRIBUTED_HARDWARE_FRAMEWORK](arkts-performanceanalysis-tags-con.md#distributed_hardware_framework) | 分布式硬件框架标签，hitrace命令行工具对应tagName:dhfwk。 |
| [DISTRIBUTED_INPUT](arkts-performanceanalysis-tags-con.md#distributed_input) | 分布式输入标签，hitrace命令行工具对应tagName:dinput。 |
| [DISTRIBUTED_SCREEN](arkts-performanceanalysis-tags-con.md#distributed_screen) | 分布式屏幕标签，hitrace命令行工具对应tagName:dscreen。 |
| [DISTRIBUTED_SCHEDULER](arkts-performanceanalysis-tags-con.md#distributed_scheduler) | 分布式调度器标签，hitrace命令行工具对应tagName:dsched。 |
| [FFRT](arkts-performanceanalysis-tags-con.md#ffrt) | FFRT任务标签，hitrace命令行工具对应tagName:ffrt。 |
| [FILE_MANAGEMENT](arkts-performanceanalysis-tags-con.md#file_management) | 文件管理系统标签，hitrace命令行工具对应tagName:filemanagement。 |
| [GLOBAL_RESOURCE_MANAGER](arkts-performanceanalysis-tags-con.md#global_resource_manager) | 全局资源管理标签，hitrace命令行工具对应tagName:gresource。 |
| [GRAPHICS](arkts-performanceanalysis-tags-con.md#graphics) | 图形模块标签，hitrace命令行工具对应tagName:graphic。 |
| [HDF](arkts-performanceanalysis-tags-con.md#hdf) | HDF子系统标签，hitrace命令行工具对应tagName:hdf。 |
| [MISC](arkts-performanceanalysis-tags-con.md#misc) | MISC模块标签，hitrace命令行工具对应tagName:misc。 |
| [MULTIMODAL_INPUT](arkts-performanceanalysis-tags-con.md#multimodal_input) | 多模态输入模块标签，hitrace命令行工具对应tagName:multimodalinput。 |
| [NET](arkts-performanceanalysis-tags-con.md#net) | 网络标签，hitrace命令行工具对应tagName:net。 |
| [NOTIFICATION](arkts-performanceanalysis-tags-con.md#notification) | 通知模块标签，hitrace命令行工具对应tagName:notification。 |
| [NWEB](arkts-performanceanalysis-tags-con.md#nweb) | Nweb标签，hitrace命令行工具对应tagName:nweb。 |
| [OHOS](arkts-performanceanalysis-tags-con.md#ohos) | OHOS通用标签，hitrace命令行工具对应tagName:ohos。 |
| [POWER_MANAGER](arkts-performanceanalysis-tags-con.md#power_manager) | 电源管理标签，hitrace命令行工具对应tagName:power。 |
| [RPC](arkts-performanceanalysis-tags-con.md#rpc) | RPC标签，hitrace命令行工具对应tagName:rpc。 |
| [SAMGR](arkts-performanceanalysis-tags-con.md#samgr) | 系统能力管理标签，hitrace命令行工具对应tagName:samgr。 |
| [WINDOW_MANAGER](arkts-performanceanalysis-tags-con.md#window_manager) | 窗口管理标签，hitrace命令行工具对应tagName:window。 |
| [AUDIO](arkts-performanceanalysis-tags-con.md#audio) | 音频模块标签，hitrace命令行工具对应tagName:zaudio。 |
| [CAMERA](arkts-performanceanalysis-tags-con.md#camera) | 相机模块标签，hitrace命令行工具对应tagName:zcamera。 |
| [IMAGE](arkts-performanceanalysis-tags-con.md#image) | 图片模块标签，hitrace命令行工具对应tagName:zimage。 |
| [MEDIA](arkts-performanceanalysis-tags-con.md#media) | 媒体模块标签，hitrace命令行工具对应tagName:zmedia。 |
