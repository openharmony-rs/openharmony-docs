# 线程安全容器使用指导 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

线程安全容器用于在多个线程间并发读写集合数据。ArkTS-Sta提供[ConcurrentHashMap (并发哈希表)](../reference/apis-arkts/arkts-sta-concurrenthashmap.md)和[ConcurrentSet (并发集合)](../reference/apis-arkts/arkts-sta-concurrentset.md)，分别适用于键值缓存、索引表、去重集合或访问标记集合等场景。

| 能力 | 适用场景 | 使用要点 |
| -------- | -------- | -------- |
| ConcurrentHashMap | 多线程并发读写键值数据。 | key和value不能为null或undefined；适合缓存、索引或状态表。 |
| ConcurrentSet | 多线程并发维护唯一元素集合。 | 元素不能为null或undefined；适合去重、访问标记或任务ID集合。 |

线程安全容器保证容器内部操作的并发安全。如果一次业务更新需要同时修改多个容器，或需要维护容器与其他字段之间的一致性，应使用[锁机制使用指导（Mutex/RWLock/AsyncLock） (ArkTS-Sta)](arkts-sta-locks-guide.md)保护这组操作。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 使用ConcurrentHashMap共享键值数据

ConcurrentHashMap适合多个TaskPool任务并发写入或读取键值数据。下面示例中，两个任务分别写入不同用户的分数，宿主线程在任务完成后读取结果。

```ts
// ArkTS-Sta示例
function putConcurrentGuideScore(scores: containers.ConcurrentHashMap<int, int>, userId: int, score: int): void {
  scores.set(userId, score);
}

function readConcurrentGuideScore(scores: containers.ConcurrentHashMap<int, int>, userId: int): int {
  let score: int | undefined = scores.get(userId);
  if (score == undefined) {
    return -1;
  }
  return score;
}

async function runConcurrentHashMapTask(): Promise<void> {
  let scores: containers.ConcurrentHashMap<int, int> = new containers.ConcurrentHashMap<int, int>();

  await Promise.all<Any>([
    taskpool.execute(putConcurrentGuideScore, scores, 1001, 90),
    taskpool.execute(putConcurrentGuideScore, scores, 1002, 95)
  ]);

  let score = (await taskpool.execute(readConcurrentGuideScore, scores, 1001)) as int;
  console.info("user score: " + score); // user score: 90
}
```

如果多个线程写入同一个key，最终值取决于实际写入顺序。需要按业务版本号、时间戳或条件更新时，应在应用层设计冲突处理策略，或使用锁保护读取、判断、写入这一组操作。

## 使用ConcurrentHashMap删除缓存

ConcurrentHashMap支持remove和delete。remove返回被删除的value；delete返回是否删除成功。只需要判断删除是否发生时，可使用delete。

```ts
// ArkTS-Sta示例
function removeConcurrentGuideCache(cache: containers.ConcurrentHashMap<int, string>, key: int): boolean {
  return cache.delete(key);
}

async function runConcurrentHashMapDelete(): Promise<void> {
  let cache: containers.ConcurrentHashMap<int, string> = new containers.ConcurrentHashMap<int, string>();
  cache.set(1, "cached");

  let removed = (await taskpool.execute(removeConcurrentGuideCache, cache, 1)) as boolean;
  console.info("cache removed: " + removed); // cache removed: true
  console.info("cache exists: " + cache.has(1)); // cache exists: false
}
```

遍历ConcurrentHashMap时，其他线程可能仍在更新容器。遍历结果适合用于统计、调试或弱一致性展示；如果业务要求遍历期间数据保持完全不变，应使用锁或拷贝快照。

## 使用ConcurrentSet维护唯一元素

ConcurrentSet适合在多线程中维护唯一元素集合。例如多个任务并发上报已处理的ID，ConcurrentSet会自动保持元素唯一。

```ts
// ArkTS-Sta示例
function addConcurrentGuideVisited(visited: containers.ConcurrentSet<int>, id: int): void {
  visited.add(id);
}

async function runConcurrentSetTask(): Promise<void> {
  let visited: containers.ConcurrentSet<int> = new containers.ConcurrentSet<int>();

  await Promise.all<Any>([
    taskpool.execute(addConcurrentGuideVisited, visited, 100),
    taskpool.execute(addConcurrentGuideVisited, visited, 200),
    taskpool.execute(addConcurrentGuideVisited, visited, 100)
  ]);

  console.info("has visited: " + visited.has(100)); // has visited: true
  console.info("has missing: " + visited.has(300)); // has missing: false
}
```

ConcurrentSet适合表达“是否出现过”、“是否已处理”或“是否已订阅”等集合语义。如果还需要为每个元素保存附加信息，应使用ConcurrentHashMap。

## 使用ConcurrentSet删除元素

ConcurrentSet支持delete删除指定元素，并返回是否删除成功。

```ts
// ArkTS-Sta示例
function deleteConcurrentGuideVisited(visited: containers.ConcurrentSet<int>, id: int): boolean {
  return visited.delete(id);
}

async function runConcurrentSetDelete(): Promise<void> {
  let visited: containers.ConcurrentSet<int> = new containers.ConcurrentSet<int>();
  visited.add(10);

  let deleted = (await taskpool.execute(deleteConcurrentGuideVisited, visited, 10)) as boolean;
  console.info("visited deleted: " + deleted); // visited deleted: true
  console.info("visited exists: " + visited.has(10)); // visited exists: false
}
```

## 使用建议

- 多线程并发读写键值数据时，优先使用ConcurrentHashMap，而不是普通Map配合零散同步逻辑。
- 多线程并发维护唯一元素集合时，优先使用ConcurrentSet。
- key、value和集合元素不能为null或undefined。
- 单次容器操作由容器保证并发安全；跨多个操作的业务一致性需要额外使用锁。
- 遍历过程中如果有其他线程修改容器，遍历结果不应作为强一致快照使用。

相关API说明请参见[ConcurrentHashMap (并发哈希表)](../reference/apis-arkts/arkts-sta-concurrenthashmap.md)和[ConcurrentSet (并发集合)](../reference/apis-arkts/arkts-sta-concurrentset.md)。
