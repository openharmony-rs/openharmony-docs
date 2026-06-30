# 原子类型使用指导 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

原子类型用于在线程间安全读写单个共享值或对象引用。ArkTS-Sta支持AtomicInt、AtomicLong、AtomicBoolean和AtomicReference等[Atomics (实例化原子类型接口)](../reference/apis-arkts/arkts-sta-atomics.md)，适合计数器、状态标志或一次性状态迁移等场景。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 适用场景

原子类型适用于以下场景：

- 多个线程共同更新单个计数器。
- 一个线程设置状态标志，其他线程读取状态。
- 使用compareAndSwap实现只允许一次成功的状态迁移。

原子类型只保证单个原子对象上的操作安全。如果需要同时维护多个字段之间的一致性，应使用[锁机制使用指导（Mutex/RWLock/AsyncLock） (ArkTS-Sta)](arkts-sta-locks-guide.md)或并发容器。

## 使用AtomicInt统计任务完成数

AtomicInt可用于多个任务并发更新同一个计数器。fetchAdd会以原子方式增加当前值，并返回更新前的旧值。

```ts
// ArkTS-Sta示例
function finishAtomicGuideWork(doneCount: AtomicInt): void {
  doneCount.fetchAdd(1);
}

async function runAtomicCounter(): Promise<void> {
  let doneCount: AtomicInt = new AtomicInt(0);

  await Promise.all<Any>([
    taskpool.execute(finishAtomicGuideWork, doneCount),
    taskpool.execute(finishAtomicGuideWork, doneCount),
    taskpool.execute(finishAtomicGuideWork, doneCount)
  ]);

  console.info("done count: " + doneCount.load()); // done count: 3
}
```

对于AtomicLong、AtomicShort、AtomicByte、AtomicFloat和AtomicDouble，也可以使用fetchAdd执行同类型数值的原子加法。

## 使用AtomicBoolean控制任务状态

AtomicBoolean适合表达运行中、已取消、已完成等布尔状态。下面示例中，任务读取AtomicBoolean决定是否继续处理。

```ts
// ArkTS-Sta示例
function loopAtomicGuideUntilStopped(running: AtomicBoolean): int {
  let count: int = 0;
  while (running.load() && count < 3) {
    count++;
  }
  return count;
}

async function runAtomicFlag(): Promise<void> {
  let running: AtomicBoolean = new AtomicBoolean(true);
  let result = (await taskpool.execute(loopAtomicGuideUntilStopped, running)) as int;

  running.store(false);
  console.info("loop count: " + result); // loop count: 3
}
```

实际业务中，AtomicBoolean常与长时任务配合使用。宿主线程更新标志位后，任务函数应在循环或分批处理过程中定期读取标志位，并在状态变化后主动退出。

## 使用compareAndSwap更新状态

compareAndSwap适合实现“只允许一个任务成功”的状态迁移。当前值等于expected时，compareAndSwap会写入新值；无论是否写入成功，都会返回更新前的旧值。

```ts
// ArkTS-Sta示例
const STATE_INIT: int = 0;
const STATE_RUNNING: int = 1;

function startAtomicGuideOnce(state: AtomicInt): boolean {
  let oldState: int = state.compareAndSwap(STATE_INIT, STATE_RUNNING);
  return oldState == STATE_INIT;
}

async function runCompareAndSwap(): Promise<void> {
  let state: AtomicInt = new AtomicInt(STATE_INIT);

  let result1 = (await taskpool.execute(startAtomicGuideOnce, state)) as boolean;
  let result2 = (await taskpool.execute(startAtomicGuideOnce, state)) as boolean;

  console.info("start result1: " + result1); // start result1: true
  console.info("start result2: " + result2); // start result2: false
}
```

## 使用AtomicReference共享对象引用

AtomicReference用于原子读写对象引用。compareAndSwap比较的是引用是否相同，而不是对象字段内容是否相等。

```ts
// ArkTS-Sta示例
class RuntimeConfig {
  name: string;

  constructor(name: string) {
    this.name = name;
  }
}

function replaceAtomicGuideConfig(ref: AtomicReference<RuntimeConfig>, oldConfig: RuntimeConfig, newConfig: RuntimeConfig): boolean {
  let previous: RuntimeConfig = ref.compareAndSwap(oldConfig, newConfig);
  return previous == oldConfig;
}

async function runAtomicReference(): Promise<void> {
  let oldConfig: RuntimeConfig = new RuntimeConfig("old");
  let newConfig: RuntimeConfig = new RuntimeConfig("new");
  let ref: AtomicReference<RuntimeConfig> = new AtomicReference<RuntimeConfig>(oldConfig);

  let changed = (await taskpool.execute(replaceAtomicGuideConfig, ref, oldConfig, newConfig)) as boolean;
  console.info("config changed: " + changed); // config changed: true
  console.info("config name: " + ref.load().name); // config name: new
}
```

如果需要对数值执行原子加减或数值比较交换，应使用AtomicInt、AtomicLong等数值原子类型，不要使用AtomicReference包装数值对象。

## 使用建议

- 单个计数器、标志位或引用替换优先使用原子类型。
- 需要保持多个字段一致时，使用[锁机制使用指导（Mutex/RWLock/AsyncLock） (ArkTS-Sta)](arkts-sta-locks-guide.md)保护一组操作。
- 原子操作不替代业务层状态设计，复杂状态迁移应明确状态值和转换条件。
- 高频集合读写优先使用并发容器，不要用多个原子变量手动拼接集合一致性。

原子类型的完整接口说明请参见[Atomics模块描述](../reference/apis-arkts/arkts-sta-atomics-overview.md)和[Atomics (实例化原子类型接口)](../reference/apis-arkts/arkts-sta-atomics.md)。
