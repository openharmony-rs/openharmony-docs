| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：taskpool；<br>API声明：function execute\<A extends Array\<Object>, R>(func: (...args: A) => R \| Promise\<R>, ...args: A): Promise\<R>;<br>差异内容：function execute\<A extends Array\<Object>, R>(func: (...args: A) => R \| Promise\<R>, ...args: A): Promise\<R>;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：function execute\<A extends Array\<Object>, R>(task: GenericsTask\<A, R>, priority?: Priority): Promise\<R>;<br>差异内容：function execute\<A extends Array\<Object>, R>(task: GenericsTask\<A, R>, priority?: Priority): Promise\<R>;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：function executeDelayed\<A extends Array\<Object>, R>(delayTime: number, task: GenericsTask\<A, R>, priority?: Priority): Promise\<R>;<br>差异内容：function executeDelayed\<A extends Array\<Object>, R>(delayTime: number, task: GenericsTask\<A, R>, priority?: Priority): Promise\<R>;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：function executePeriodically\<A extends Array\<Object>, R>(period: number, task: GenericsTask\<A, R>, priority?: Priority): void;<br>差异内容：function executePeriodically\<A extends Array\<Object>, R>(period: number, task: GenericsTask\<A, R>, priority?: Priority): void;|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：taskpool；<br>API声明：class GenericsTask<br>差异内容：class GenericsTask|api/@ohos.taskpool.d.ts|
|新增API|NA|类名：ParseReturnType；<br>API声明：MAP = 1<br>差异内容：MAP = 1|arkts/@arkts.utils.d.ets|
