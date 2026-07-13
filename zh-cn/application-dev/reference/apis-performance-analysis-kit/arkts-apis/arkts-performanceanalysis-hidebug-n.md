# hidebug

ΪӦ���ṩ���ֵ��ԡ����ŵķ��������������߶�λ����ƿ�����Ż�Ӧ�����ܡ���Ҫ���ܰ������ڴ����ݷ�����CPUʹ���ʼ�ء�trace�ɼ���profiler�ɼ���VM�ѿ���ת�������ڸ�ģ��Ľӿڴ��ȽϺķ����ܣ��ӿڵ��ý�Ϊ��ʱ���һ���HiDebugģ�鶨�壬��ģ���ڵĽӿڽ�������Ӧ�õ��ԡ����Ž׶�ʹ�á�����Ҫ����������ʹ��ʱ������������������õĽӿڶ�Ӧ�����ܵ�Ӱ�졣

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [tags](arkts-performanceanalysis-tags-n.md) | ֧��traceʹ�ó����ı�ǩ���û���ͨ��hitraceץȡָ����ǩ��trace���ݡ�&gt; **ע��**&gt;&gt; ���±�ǩʵ��ֵ��ϵͳ���壬������汾�����������ı䣬Ϊ������������ּ��������⣬��������Ӧֱ��ʹ�ñ�ǩ���ƶ��Ǳ�ǩ��ֵ�� |

### 函数

| 名称 | 说明 |
| --- | --- |
| [getNativeHeapSize](arkts-performanceanalysis-getnativeheapsize-f.md#getnativeheapsize-1) | ��ȡ�ڴ������ͳ�ƵĽ��̳��е���ͨ����ռ�õ����ֽ����� |
| [getNativeHeapAllocatedSize](arkts-performanceanalysis-getnativeheapallocatedsize-f.md#getnativeheapallocatedsize-1) | ��ȡ�ڴ������ͳ�ƵĽ��̳��е���ʹ�õ���ͨ����ռ�õ����ֽ����� |
| [getNativeHeapFreeSize](arkts-performanceanalysis-getnativeheapfreesize-f.md#getnativeheapfreesize-1) | ��ȡ�ڴ������ͳ�ƵĽ��̳��еĿ��е���ͨ����ռ�õ����ֽ����� |
| [getVss](arkts-performanceanalysis-getvss-f.md#getvss-1) | ��ȡӦ�ý���ռ�õ������ڴ��С���ӿ�ʵ�ַ�ʽ����ȡ/proc/{pid}/statm�ڵ��е�sizeֵ���ڴ�ҳ������vss = size * ҳ��С��4KB/ҳ���� |
| [getPss](arkts-performanceanalysis-getpss-f.md#getpss-1) | ��ȡӦ�ý���ʵ��ʹ�õ������ڴ��С���ӿ�ʵ�ַ�ʽ����ȡ/proc/{pid}/smaps_rollup�ڵ��е�Pss��SwapPssֵ����͡�&gt; **ע��**&gt;&gt; ����/proc/{pid}/smaps_rollup�Ķ�ȡ��ʱ�ϳ������鲻Ҫ�����߳���ʹ�øýӿڣ���ͨ��@ohos.taskpool��@ohos.worker�����첽�߳��Ա���Ӧ�ó��ֿ��١� |
| [getSharedDirty](arkts-performanceanalysis-getshareddirty-f.md#getshareddirty-1) | ��ȡ���̵Ĺ������ڴ��С���ӿ�ʵ�ַ�ʽ����ȡ/proc/{pid}/smaps_rollup�ڵ��е�Shared_Dirtyֵ��&gt; **ע��**&gt;&gt; ����/proc/{pid}/smaps_rollup�Ķ�ȡ��ʱ�ϳ������鲻Ҫ�����߳���ʹ�øýӿڣ���ͨ��@ohos.taskpool��@ohos.worker�����첽�߳��Ա���Ӧ�ó��ֿ��١� |
| [getPrivateDirty](arkts-performanceanalysis-getprivatedirty-f.md#getprivatedirty-1) | ��ȡ���̵�˽�����ڴ��С����ȡ/proc/{pid}/smaps_rollup�е�Private_Dirtyֵ��&gt; **ע��**&gt;&gt; ����/proc/{pid}/smaps_rollup�Ķ�ȡ��ʱ�ϳ������鲻Ҫ�����߳���ʹ�øýӿڣ���ͨ��@ohos.taskpool��@ohos.worker�����첽�߳��Ա���Ӧ�ó��ֿ��١� |
| [getCpuUsage](arkts-performanceanalysis-getcpuusage-f.md#getcpuusage-1) | ��ȡ���̵�CPUʹ���ʡ�&gt; **ע��**&gt;&gt; ���ڸýӿ��漰�����ͨ�ţ���ʱ�ϳ���Ϊ�˱��������������⣬���鲻Ҫ�����߳���ֱ�ӵ��øýӿڡ� |
| [startProfiling](arkts-performanceanalysis-startprofiling-f.md#startprofiling-1) | ���������Profiling�������٣�`startProfiling(filename: string)`�����ĵ�����Ҫ��`stopProfiling()`�����ĵ���һһ��Ӧ���ȿ�����رգ�������ظ��������ظ��رյĵ��÷�ʽ�������ӿڵ����쳣�� |
| [stopProfiling](arkts-performanceanalysis-stopprofiling-f.md#stopprofiling-1) | ֹͣ�����Profiling�������٣�`stopProfiling()`�����ĵ�����Ҫ��`startProfiling(filename: string)`�����ĵ���һһ��Ӧ���ȿ�����رգ�������ظ��������ظ��رյĵ��÷�ʽ�������ӿڵ����쳣�� |
| [dumpHeapData](arkts-performanceanalysis-dumpheapdata-f.md#dumpheapdata-1) | �����������ת��������`filename.heapsnapshot`�ļ��� |
| [startJsCpuProfiling](arkts-performanceanalysis-startjscpuprofiling-f.md#startjscpuprofiling-1) | ���������Profiling�������٣�`startJsCpuProfiling(filename: string)`�����ĵ�����Ҫ��`stopJsCpuProfiling()`�����ĵ���һһ��Ӧ���ȿ�����رգ�������ظ��������ظ��رյĵ��÷�ʽ�������ӿڵ����쳣�� |
| [stopJsCpuProfiling](arkts-performanceanalysis-stopjscpuprofiling-f.md#stopjscpuprofiling-1) | ֹͣ�����Profiling�������٣�`stopJsCpuProfiling()`�����ĵ�����Ҫ��`startJsCpuProfiling(filename: string)`�����ĵ���һһ��Ӧ���ȿ�����رգ�������ظ��������ظ��رյĵ��÷�ʽ�������ӿڵ����쳣�� |
| [dumpJsHeapData](arkts-performanceanalysis-dumpjsheapdata-f.md#dumpjsheapdata-1) | �����������ת����&gt; **ע��**&gt;&gt; ����������ѵ��������ʱ���Ҹýӿ�Ϊͬ���ӿڣ����鲻Ҫ���ϼܰ汾�е��øýӿڣ��Ա���Ӧ�ö�����Ӱ���û����顣 |
| [dumpJsHeapData](arkts-performanceanalysis-dumpjsheapdata-f.md#dumpjsheapdata-2) | �����������ת����֧�����nodeId���档&gt; **ע��**&gt;&gt; ����������ѵ��������ʱ���Ҹýӿ�Ϊͬ���ӿڣ����鲻Ҫ���ϼܰ汾�е��øýӿڣ��Ա���Ӧ�ö�����Ӱ���û����顣 |
| [getServiceDump](arkts-performanceanalysis-getservicedump-f.md#getservicedump-1) | ��ȡϵͳ������Ϣ�� |
| [getSystemCpuUsage](arkts-performanceanalysis-getsystemcpuusage-f.md#getsystemcpuusage-1) | ��ȡϵͳ��CPU��Դռ�������&gt; **ע��**&gt;&gt; ���ڸýӿ��漰�����ͨ�ţ���ʱ�ϳ���Ϊ�˱��������������⣬���鲻Ҫ�����߳���ֱ�ӵ��øýӿڡ� |
| [getAppThreadCpuUsage](arkts-performanceanalysis-getappthreadcpuusage-f.md#getappthreadcpuusage-1) | ��ȡӦ���߳�CPUʹ�������&gt; **ע��**&gt;&gt; ���ڸýӿ��漰�����ͨ�ţ���ʱ�ϳ���Ϊ�˱��������������⣬���鲻Ҫ�����߳���ֱ�ӵ��øýӿڡ� |
| [getSystemMemInfo](arkts-performanceanalysis-getsystemmeminfo-f.md#getsystemmeminfo-1) | ��ȡϵͳ�ڴ���Ϣ����ȡ/proc/meminfo�ڵ�����ݡ� |
| [getAppNativeMemInfo](arkts-performanceanalysis-getappnativememinfo-f.md#getappnativememinfo-1) | ��ȡӦ�ý����ڴ���Ϣ����ȡ/proc/{pid}/smaps_rollup��/proc/{pid}/statm�ڵ�����ݡ�&gt; **ע��**&gt;&gt; ���ڶ�ȡ/proc/{pid}/smaps_rollup��ʱ�ϳ����Ƽ�ʹ���첽�ӿ�hidebug.getAppNativeMemInfoAsync���Ա���Ӧ�ö�֡�򿨶١�&gt;&gt; �Ƽ�ʹ��hidebug.getRssInfo�ӿڻ�ȡӦ�õ�rssʹ����Ϣ�� |
| [getAppMemoryLimit](arkts-performanceanalysis-getappmemorylimit-f.md#getappmemorylimit-1) | ��ȡӦ�ó�����̵��ڴ����ơ� |
| [getAppVMMemoryInfo](arkts-performanceanalysis-getappvmmemoryinfo-f.md#getappvmmemoryinfo-1) | ��ȡVM�ڴ������Ϣ�� |
| [getAppVMObjectUsedSize](arkts-performanceanalysis-getappvmobjectusedsize-f.md#getappvmobjectusedsize-1) | ��ȡ��ǰ�������ArkTS������ռ�õ��ڴ��С�� |
| [getAppNativeMemInfoAsync](arkts-performanceanalysis-getappnativememinfoasync-f.md#getappnativememinfoasync-1) | ��ȡ/proc/{pid}/smaps_rollup��/proc/{pid}/statm�ڵ�������Ի�ȡӦ�ý����ڴ���Ϣ��ʹ��Promise�첽�ص��� |
| [getAppNativeMemInfoWithCache](arkts-performanceanalysis-getappnativememinfowithcache-f.md#getappnativememinfowithcache-1) | ��ȡӦ�ý����ڴ���Ϣ����`getAppNativeMemInfo`�ӿ���ȣ��ýӿ�ʹ���˻�����ƣ���������ܡ��������Ч��Ϊ5���ӡ�&gt; **ע��**&gt;&gt; ���ڶ�ȡ /proc/{pid}/smaps_rollup �ȽϺ�ʱ�����鲻�����߳���ʹ�øýӿڡ�����ͨ��@ohos.taskpool��@ohos.worker�����첽�̣߳��Ա���Ӧ�ÿ��١� |
| [startAppTraceCapture](arkts-performanceanalysis-startapptracecapture-f.md#startapptracecapture-1) | �ýӿڲ�����hitrace���ܣ������߿�ͨ���ýӿ����ָ����Χ��trace�Զ����ɼ������ڸýӿ���trace�ɼ����������ĵ���������Ҫ�ɼ��ķ�Χ������أ����鿪������ʹ�øýӿ�ǰ��ͨ��hitrace����ץȡӦ�õ�trace��־������ɸѡ������trace�ɼ��Ĺؼ���Χ������߸ýӿ����ܡ�`startAppTraceCapture()`�����ĵ�����Ҫ��`stopAppTraceCapture()`�����ĵ���һһ��Ӧ���ظ�����trace�ɼ������½ӿڵ����쳣������trace�ɼ������л����Ľ϶����ܣ�������Ӧ����ɲɼ���ʱ�رա�Ӧ�õ���startAppTraceCapture�ӿ������ɼ�trace�����ɼ���trace��С������limitSize��ϵͳ���Զ�����stopAppTraceCapture�ӿ�ֹͣ�ɼ������limitSize��С���ò���������������trace���ݲ��㣬�޷�������Ϸ���������Ҫ�󿪷��߸���ʵ�����������limitSize��С������������limitSize = Ԥ��trace�ɼ�ʱ�� * trace��λ������Ԥ��trace�ɼ�ʱ���������߸��ݷ����Ĺ��ϳ������о�������λ�롣trace��λ������Ӧ��ÿ�������trace��С��ϵͳ�Ƽ�ֵΪ300KB/s�����鿪���߲�������Ӧ�õ�ʵ��ֵ����λKB/s��trace��λ����ʵ�ⷽ����limitSize����Ϊ���ֵ500M������startAppTraceCapture�ӿڣ���Ӧ���ϲ���N��󣬵���stopAppTraceCaptureֹͣ�ɼ���Ȼ��鿴trace��СS��KB������ôtrace��λ���� = S/N��KB/s���� |
| [stopAppTraceCapture](arkts-performanceanalysis-stopapptracecapture-f.md#stopapptracecapture-1) | ֹͣӦ��trace�ɼ�������ǰ�����ȵ���`startAppTraceCapture()`������ʼ�ɼ����ر�ǰδ�������ظ��رջᵼ�½ӿ��쳣������startAppTraceCapture�ӿڣ����û�к�������limitSize����������trace�Ĵ�С���ڴ����limitSize��С��ϵͳ�ڲ����Զ�����stopAppTraceCapture���ٴ��ֶ�����stopAppTraceCapture�ͻ��׳�������11400105�� |
| [getGwpAsanGrayscaleState](arkts-performanceanalysis-getgwpasangrayscalestate-f.md#getgwpasangrayscalestate-1) | ��ȡ��ǰGWP-ASanʣ��ʹ�������� |
| [requestTrace](arkts-performanceanalysis-requesttrace-f.md#requesttrace-1) | ��ȡ��ǰ���̵�trace��Ϣ������Ӧ��tag��ͼ�񴰿�tag��cpu���Ⱥ�binder�ں���Ϣ��ʹ��Promise�첽�ص����ɼ�trace���ص�.sys�ļ���Ŀ¼�����洢3�ݣ��������ڵ���3��ʱ�ٴε��ýӿڻ��׳�������11400120�� |
| [getVMRuntimeStats](arkts-performanceanalysis-getvmruntimestats-f.md#getvmruntimestats-1) | ��ȡϵͳGCͳ����Ϣ�� |
| [getVMRuntimeStat](arkts-performanceanalysis-getvmruntimestat-f.md#getvmruntimestat-1) | ���ݲ�����ȡָ����ϵͳGCͳ����Ϣ�� |
| [setAppResourceLimit](arkts-performanceanalysis-setappresourcelimit-f.md#setappresourcelimit-1) | ����Ӧ�õ��ļ��������������߳�������JS�ڴ��Native�ڴ���Դ���ơ���ҪӦ�ó������ڹ����ڴ�й©���ϡ�&gt; **ע��**&gt;&gt; �������еĿ�����ѡ����ڿ�����ѡ���б����ҵ�"ϵͳ��Դй©��־"�����ã������豸��ӿ���Ч�� |
| [isDebugState](arkts-performanceanalysis-isdebugstate-f.md#isdebugstate-1) | ��ȡӦ�ý��̵ĵ���״̬�� |
| [getGraphicsMemory](arkts-performanceanalysis-getgraphicsmemory-f.md#getgraphicsmemory-1) | ��ȡӦ���Դ��ܴ�С��gl + graph����ʹ��Promise�첽�ص��� |
| [getGraphicsMemorySync](arkts-performanceanalysis-getgraphicsmemorysync-f.md#getgraphicsmemorysync-1) | ʹ��ͬ����ʽ��ȡӦ���Դ��ܴ�С��gl + graph����&gt; **ע��**&gt;&gt; ���ڸýӿ��漰��ο����ͨ�ţ����ʱ���ܴﵽ�뼶��Ϊ�˱��������������⣬���鲻Ҫ�����̵߳��øýӿڣ��Ƽ�ʹ���첽�ӿ�`getGraphicsMemory`�� |
| [getGraphicsMemorySummary](arkts-performanceanalysis-getgraphicsmemorysummary-f.md#getgraphicsmemorysummary-1) | ��ȡӦ���Դ����ݣ�ʹ��Promise�����첽�ص��� |
| [setJsRawHeapTrimLevel](arkts-performanceanalysis-setjsrawheaptrimlevel-f.md#setjsrawheaptrimlevel-1) | ���õ�ǰ����ת�������ԭʼ�ѿ��յĲü�����ʹ�øýӿڲ��������TRIM_LEVEL_2��������Ч���ٶѿ��յ��ļ���С��&gt; **ע��**&gt;&gt; Ĭ�ϲü�������TRIM_LEVEL_1�����������TRIM_LEVEL_2�ü�����ʹ��API version 20֮���rawheap-translator���߲��ܽ�.rawheap�ļ�ת��Ϊ.heapsnapshot�ļ���������ܵ���ת��ʧ�ܡ�&gt;&gt; �ýӿ�Ӱ��dumpJsRawHeapData�Ľ���� |
| [dumpJsRawHeapData](arkts-performanceanalysis-dumpjsrawheapdata-f.md#dumpjsrawheapdata-1) | Ϊ��ǰ�߳�ת���������ԭʼ�ѿ��գ������ɵ�rawheap��ʽ�ļ���ʹ��Promise�첽�ص���ɡ����ļ���ͨ��rawheap-translator����ת��Ϊheapsnapshot��ʽ�ļ����н�����&gt; **ע��**&gt;&gt; ϵͳͨ���ýӿ�ת����ջ����Ĵ�����Դ������ϸ������˵���Ƶ�ʺʹ��������������ɵ��ļ���������ɾ����&gt;&gt; �����ڿ�����ģʽ�µ��øýӿڣ����������������ƣ������õĿ�����ѡ��ش򿪲������豸�󼴿���Ч�� |
| [dumpJsRawHeapData](arkts-performanceanalysis-dumpjsrawheapdata-f.md#dumpjsrawheapdata-2) | Ϊ��ǰ�߳�ת���������ԭʼ�ѿ��գ���֧�����nodeId���档���ɵ��ļ�Ϊrawheap��ʽ��ʹ��Promise�첽�ص���ɡ����ļ���ͨ��rawheap-translator����ת��Ϊheapsnapshot��ʽ�ļ����н�����&gt; **ע��**&gt;&gt; ϵͳͨ���ýӿ�ת����ջ����Ĵ�����Դ������ϸ������˵���Ƶ�ʺʹ��������������ɵ��ļ���������ɾ����&gt;&gt; �����ڿ�����ģʽ�µ��øýӿڣ����������������ƣ������õĿ�����ѡ��ش򿪲������豸�󼴿���Ч�� |
| [dumpJsRawHeapData](arkts-performanceanalysis-dumpjsrawheapdata-f.md#dumpjsrawheapdata-3) | Ϊ��ǰ�̻߳����������������������ԭʼ�ѿ��գ���֧�����nodeId���棬���ɵ��ļ�Ϊrawheap��ʽ��ʹ��Promise�첽�ص����ļ���ͨ��rawheap-translator����ת��Ϊheapsnapshot��ʽ�ļ����н�����&gt; **ע��**&gt;&gt; ϵͳͨ���ýӿ�ת�����ջ����Ĵ�����Դ������ϸ������˵���Ƶ�ʺʹ��������������ɵ��ļ���������ɾ����&gt;&gt; �����ڿ�����ģʽ�µ��øýӿڣ����������������ƣ������õĿ�����ѡ��ش򿪲������豸�󼴿���Ч�� |
| [enableGwpAsanGrayscale](arkts-performanceanalysis-enablegwpasangrayscale-f.md#enablegwpasangrayscale-1) | ʹ��GWP-ASan�����ڼ����ڴ�ʹ���еķǷ���Ϊ���ýӿ���Ҫ���ڶ�̬���ò�����GWP-ASan��������Ӧ���Զ����GWP-ASan�����ԡ�������Ӧ��������������Ч�� |
| [disableGwpAsanGrayscale](arkts-performanceanalysis-disablegwpasangrayscale-f.md#disablegwpasangrayscale-1) | ֹͣʹ��GWP-ASan�����øýӿڽ�ȡ���Զ������ã��ָ�Ĭ�ϲ���GwpAsanOptions�� |
| [getGwpAsanGrayscaleState](arkts-performanceanalysis-getgwpasangrayscalestate-f.md#getgwpasangrayscalestate-2) | ��ȡ��ǰGWP-ASanʣ��ʹ�������� |
| [setProcDumpInSharedOOM](arkts-performanceanalysis-setprocdumpinsharedoom-f.md#setprocdumpinsharedoom-1) | ��ת���Ķѿ������̼߳���Ϊ���̼���&gt; **ע��**&gt;&gt; Ҫ��ת�����̼��Ķѿ��գ����øýӿڲ�����true������OOMʱ��������SharedHeap OOM����������ȱһ���ɡ�&gt;&gt; �ýӿڲ�Ӱ������������ת���Ķѿ������ݡ��磺����Ӱ��dumpJsRawHeapData�Ľ����&gt;&gt; �ýӿ���Ӧ�õ����������ڿɱ���ε��ã��������һ�ε��õ�ִ�н������Ч�� |
| [getRssInfo](arkts-performanceanalysis-getrssinfo-f.md#getrssinfo-1) | ��ȡӦ�ó�����̵������ڴ�ʹ����Ϣ����ȡ/proc/{pid}/status�ڵ�����ݡ�&gt; **ע��**&gt;&gt; ��ȡ/proc/{pid}/status��ʱ�̣ܶ���hidebug.getAppNativeMemInfo�ӿ��л�ȡ��`rss`ֵ��ȴ���һ�������ýӿڸ���������Ϊ����Ӧ�ö�֡�򿨶��Ƽ�ʹ�øýӿڡ� |
| [enableGwpAsanGrayscale](arkts-performanceanalysis-enablegwpasangrayscale-f.md#enablegwpasangrayscale-2) | ʹ��GWP-ASan�����ڼ����ڴ�ʹ���еķǷ���Ϊ�� |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ThreadCpuUsage](arkts-performanceanalysis-threadcpuusage-i.md) | �̵߳�CPUʹ������� |
| [NativeMemInfo](arkts-performanceanalysis-nativememinfo-i.md) | ����Ӧ�ý��̵��ڴ���Ϣ�� |
| [MemoryLimit](arkts-performanceanalysis-memorylimit-i.md) | Ӧ�ý����ڴ����ơ� |
| [VMMemoryInfo](arkts-performanceanalysis-vmmemoryinfo-i.md) | VM�ڴ���Ϣ�� |
| [RequestTraceConfig](arkts-performanceanalysis-requesttraceconfig-i.md) | �ṩtrace�ɼ��Ĳ���ѡ� |
| [GraphicsMemorySummary](arkts-performanceanalysis-graphicsmemorysummary-i.md) | ����Ӧ���Դ����ݣ�����gl��graph���֡� |
| [GwpAsanOptions](arkts-performanceanalysis-gwpasanoptions-i.md) | GWP-ASan����������������Ƿ�ʹ�ܡ�����Ƶ�ʣ��Լ�������Ĳ������ |
| [RssInfo](arkts-performanceanalysis-rssinfo-i.md) | ����Ӧ�ý��̵������ڴ���Ϣ�� |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SystemMemInfo](arkts-performanceanalysis-systemmeminfo-i.md) | ����ϵͳ�ڴ���Ϣ���������ڴ桢�����ڴ�Ϳ����ڴ档 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [TraceFlag](arkts-performanceanalysis-traceflag-e.md) | �����ɼ�trace�̵߳����ͣ��������̺߳������̡߳� |
| [JsRawHeapTrimLevel](arkts-performanceanalysis-jsrawheaptrimlevel-e.md) | ת���ѿ��յĲü������ö�١�TRIM_LEVEL_2���TRIM_LEVEL_1���ü�ʱ���������������ֵΪ6�롣ʹ��TRIM_LEVEL_1ʱ������ﵽ����ֵ���л���TRIM_LEVEL_2ʱ���ü�ʱ����ܻᳬ��6�룬����APP_FREEZE�������¼���������Ӧ�ñ�ϵͳ��ֹ����ʱ������TRIM_LEVEL_1������вü����Ƽ�����ʹ��TRIM_LEVEL_1ȷ��Ӧ���ȶ���������Ҫ�����ײü�ʱ����TRIM_LEVEL_2�� |

### 类型

| 名称 | 说明 |
| --- | --- |
| [GcStats](arkts-performanceanalysis-gcstats-t.md) | �������ڴ洢GCͳ����Ϣ�ļ�ֵ�ԡ������Ͳ�֧�ֶ��̲߳��������Ӧ���д��ڶ��߳�ͬʱ���ʣ������������ |

