# 获取最近访问列表场景 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

最近访问列表常用于书架、文档、搜索记录等场景。每次用户打开一个条目后，将该条目更新为最近访问；当列表超过容量时，移除最久未访问的条目。

动态ArkTS文档使用SendableLruCache、@Sendable和共享模块实现跨线程最近访问列表。ArkTS-Sta不使用@Sendable表达共享对象，且SendableLruCache不是本文采用的静态基线。ArkTS-Sta可以使用[LRUCache](../reference/apis-arkts/js-apis-util.md#lrucache9)保存最近访问记录，并使用[Mutex (互斥锁)](../reference/apis-arkts/arkts-sta-mutex.md)保护多线程访问。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。
> - util.LRUCache.keys()在ArkTS-Sta中返回从最近最少访问到最近访问的键列表。若界面需要按“最近访问优先”展示，需要将结果反向处理。

## 封装最近访问缓存

以下示例以书架为例，使用util.LRUCache<string, string>保存图书标题到页面名称的映射，并用Mutex保护get、put和keys等组合操作。

```ts
// ArkTS-Sta示例
// RecentBookCache.ets
import { util } from '@kit.ArkTS'

export class RecentBookCache {
  private lock: Mutex = new Mutex();
  private books: util.LRUCache<string, string> = new util.LRUCache<string, string>(4);

  constructor() {
    this.books.put("第一本书", "Book1");
    this.books.put("第二本书", "Book2");
    this.books.put("第三本书", "Book3");
    this.books.put("第四本书", "Book4");
  }

  public visit(title: string): string {
    this.lock.lock();
    try {
      let page: string | undefined = this.books.get(title);
      if (page === undefined) {
        return "";
      }

      this.books.put(title, page);
      return page;
    } finally {
      this.lock.unlock();
    }
  }

  public recentTitles(): Array<string> {
    this.lock.lock();
    try {
      let keys: Array<string> = this.books.keys();
      let result: Array<string> = [];

      for (let index: int = keys.length - 1; index >= 0; index--) {
        result.push(keys[index]);
      }

      return result;
    } finally {
      this.lock.unlock();
    }
  }
}

export let recentBookCache: RecentBookCache = new RecentBookCache();
```

## 在TaskPool任务中更新访问记录

用户打开图书时，可以将最近访问记录更新操作放到TaskPool中执行。TaskPool任务只访问共享缓存，不操作ArkUI组件和页面状态。

```ts
// ArkTS-Sta示例
// RecentBookTask.ets
import { recentBookCache } from './RecentBookCache'

export function updateRecentBook(title: string): string {
  return recentBookCache.visit(title);
}
```

## 展示最近访问列表

页面显示最近访问图书列表。点击图书时，使用TaskPool更新最近访问顺序，再刷新UI状态并跳转到对应页面。

```ts
// ArkTS-Sta示例
// Index.ets
import { Entry, Text, Column, Component, Button, ClickEvent, ForEach } from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import { recentBookCache } from './RecentBookCache'
import { updateRecentBook } from './RecentBookTask'

@Entry
@Component
struct Index {
  @State title: string = "书架";
  @State recentBooks: Array<string> = new Array<string>();

  aboutToAppear(): void {
    this.refreshRecentBooks();
  }

  private refreshRecentBooks(): void {
    this.recentBooks = recentBookCache.recentTitles();
  }

  private async openBook(bookTitle: string): Promise<void> {
    let page: string = (await taskpool.execute(updateRecentBook, bookTitle)) as string;
    if (page.length == 0) {
      console.info("book not found: " + bookTitle); // book not found: 书名
      return;
    }

    this.refreshRecentBooks();
    this.getUIContext().getRouter().pushUrl({ url: "pages/" + page });
  }

  build() {
    Column(undefined) {
      Text(this.title).fontSize(32)

      ForEach(this.recentBooks, (bookTitle: string) => {
        Button(bookTitle)
          .fontSize(20)
          .onClick((e: ClickEvent) => {
            this.openBook(bookTitle);
          })
      }, (bookTitle: string): string => {
        return bookTitle;
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

## 定义图书页面

为每本图书定义对应页面，并在src/main/resources/base/profile/main_pages.json中注册页面路径。以下仅展示Book1.ets，其他图书页面可按相同方式创建。

```ts
// ArkTS-Sta示例
// Book1.ets
import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component'

@Entry
@Component
struct Book1 {
  build() {
    Column(undefined) {
      Text("第一本书的内容")
        .fontSize(24)

      Button("返回")
        .fontSize(20)
        .onClick((e: ClickEvent) => {
          this.getUIContext().getRouter().pushUrl({ url: "pages/Index" });
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

```json
// src/main/resources/base/profile/main_pages.json
{
  "src": [
    "pages/Index",
    "pages/Book1",
    "pages/Book2",
    "pages/Book3",
    "pages/Book4"
  ]
}
```

## 使用建议

- ArkTS-Sta中不要直接保留动态示例里的@Sendable、use shared和SendableLruCache写法。静态对象默认可共享，重点是明确同步边界。
- util.LRUCache用于维护容量和访问顺序，但多个线程同时访问同一个缓存实例时，应使用Mutex、AsyncLock等同步机制保护组合操作。
- util.LRUCache.keys()返回从最近最少访问到最近访问的顺序；如果页面要展示最近访问优先的列表，需要反向处理。
- TaskPool任务中不要访问ArkUI组件、路由对象或@State状态变量。后台任务只更新共享缓存并返回普通数据，宿主线程负责刷新UI和页面跳转。
- 最近访问列表如果需要跨应用重启保留，应在缓存之外持久化到首选项、数据库或文件中。LRU缓存适合进程内快速访问，不等同于持久化存储。
