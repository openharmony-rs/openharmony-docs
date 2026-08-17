# SyncPrimitives(定义ArkTS的同步原语)

/*
 Copyright (c) 2026 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /


## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Mutex](arkts-na-syncprimitives-mutex-c.md) | 互斥锁，提供对共享资源的独占访问。同一时刻仅允许一个线程持有该锁。 |
| [RWLock](arkts-na-syncprimitives-rwlock-c.md) | 读写锁，允许多个线程并发读取共享资源，但写线程需要独占访问。 |
| [ReadLock](arkts-na-syncprimitives-readlock-c.md) | 读锁，允许多个线程并发读取共享资源。 |
| [WriteLock](arkts-na-syncprimitives-writelock-c.md) | 写锁，提供对共享资源的独占写入。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Lock](arkts-na-syncprimitives-lock-i.md) | 表示可获取和释放的锁接口。 |

