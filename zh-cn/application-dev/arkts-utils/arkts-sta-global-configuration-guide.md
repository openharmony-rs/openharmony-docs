# 全局配置项功能场景 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

全局配置项通常指同一应用进程内需要被多个业务模块共享的运行时状态，例如登录状态、当前用户、网络开关、功能开关等。ArkTS-Sta可以通过模块级导出的单例对象保存这类配置，并由[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)任务或[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)任务在线程间共享。

ArkTS-Sta采用共享内存模型，普通对象可以被TaskPool任务和宿主线程共享，不需要使用动态ArkTS中的"use shared"和@Sendable。但全局配置项通常是可变状态，如果宿主线程和后台任务可能同时读写，需要使用锁、原子类型或并发容器保证数据一致性。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。
> - 本文中的全局配置项是进程内运行时状态，不是系统配置，也不是持久化配置。跨进程、跨应用或应用重启后仍需保留的配置，应使用Preferences、数据库等持久化能力。

## 定义全局配置项

以下示例定义一个全局配置对象。配置对象内部使用AsyncLock保护登录状态和Wi-Fi状态，读操作使用共享锁，写操作使用独占锁。

```ts
// ArkTS-Sta示例
// Config.ets
export class AppConfig {
  private lock: AsyncLock = new AsyncLock();
  private isLogin: boolean = false;
  private loginUser: string = "";
  private wifiOn: boolean = false;

  async login(user: string): Promise<void> {
    await this.lock.lockAsync<void>(() => {
      this.isLogin = true;
      this.loginUser = user;
    }, AsyncLockMode.EXCLUSIVE);
  }

  async logout(): Promise<void> {
    await this.lock.lockAsync<void>(() => {
      this.isLogin = false;
      this.loginUser = "";
    }, AsyncLockMode.EXCLUSIVE);
  }

  async getIsLogin(): Promise<boolean> {
    return await this.lock.lockAsync<boolean>(() => {
      return this.isLogin;
    }, AsyncLockMode.SHARED);
  }

  async getUser(): Promise<string> {
    return await this.lock.lockAsync<string>(() => {
      return this.loginUser;
    }, AsyncLockMode.SHARED);
  }

  async setWifiState(state: boolean): Promise<void> {
    await this.lock.lockAsync<void>(() => {
      this.wifiOn = state;
    }, AsyncLockMode.EXCLUSIVE);
  }

  async isWifiOn(): Promise<boolean> {
    return await this.lock.lockAsync<boolean>(() => {
      return this.wifiOn;
    }, AsyncLockMode.SHARED);
  }
}

export let config: AppConfig = new AppConfig();
```

## 在TaskPool任务中读取配置

TaskPool任务可以直接导入模块级单例对象，读取配置后执行业务逻辑。以下示例表示只有在Wi-Fi打开且用户已登录时才允许下载。

```ts
// ArkTS-Sta示例
// DownloadTask.ets
import { config } from './Config'

export async function download(): Promise<boolean> {
  if (!await config.isWifiOn()) {
    console.info("wifi is off"); // wifi is off
    return false;
  }

  if (!await config.getIsLogin()) {
    console.info("not login"); // not login
    return false;
  }

  let user: string = await config.getUser();
  console.info("User[" + user + "] start download ..."); // User[zhangsan] start download ...
  return true;
}
```

## 在宿主线程修改配置

宿主线程可以修改配置状态，并使用TaskPool执行后台任务。由于配置对象内部已经使用AsyncLock保护，宿主线程和TaskPool任务可以通过同一套方法访问配置。

```ts
// ArkTS-Sta示例
// Index.ets
import {
  Entry,
  Text,
  Column,
  Component,
  Button,
  TextInput,
  Toggle,
  ToggleType,
  ClickEvent
} from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import { config } from './Config'
import { download } from './DownloadTask'

@Entry
@Component
struct Index {
  @State message: string = "not login";
  @State wifiState: string = "wifi off";
  @State downloadResult: string = "";
  input: string = "";

  login(): void {
    config.getIsLogin().then((isLogin: boolean) => {
      if (!isLogin && this.input.length > 0) {
        config.login(this.input).then(() => {
          this.message = "login: " + this.input;
        });
      }
    });
  }

  logout(): void {
    config.getIsLogin().then((isLogin: boolean) => {
      if (isLogin) {
        config.logout().then(() => {
          this.message = "not login";
        });
      }
    });
  }

  updateWifiState(isOn: boolean): void {
    config.setWifiState(isOn).then(() => {
      this.wifiState = isOn ? "wifi on" : "wifi off";
    });
  }

  startDownload(): void {
    taskpool.execute(download).then((ret: Any) => {
      let result: boolean = ret as boolean;
      this.downloadResult = result ? "download success" : "download fail";
      console.info(this.downloadResult); // download success（满足下载条件时）；download fail（不满足下载条件时）
    });
  }

  build() {
    Column(undefined) {
      Text(this.message).fontSize(20)
      TextInput({ placeholder: "请输入用户名" })
        .onChange((value: string) => {
          this.input = value;
        })
      Button("login")
        .onClick((e: ClickEvent) => {
          this.login();
        })
      Button("logout")
        .onClick((e: ClickEvent) => {
          this.logout();
        })
      Text(this.wifiState).fontSize(20)
      Toggle({ type: ToggleType.Switch })
        .onChange((isOn: boolean) => {
          this.updateWifiState(isOn);
        })
      Button("download")
        .onClick((e: ClickEvent) => {
          this.startDownload();
        })
      Text(this.downloadResult).fontSize(20)
    }
    .height('100%')
    .width('100%')
  }
}
```

## 使用建议

- 模块级单例适合保存进程内运行时配置，不适合保存跨进程或持久化配置。
- 全局配置项为可变对象时，应统一封装读写方法，不建议直接暴露字段给多个线程读写。
- 读多写少的配置可使用AsyncLock共享锁/独占锁模式，或使用[RWLock (读写锁)](../reference/apis-arkts/arkts-sta-rwlock.md)保护同步临界区。
- 单个布尔值、计数器等简单状态可以使用[AtomicBoolean](../reference/apis-arkts/arkts-sta-atomics.md#atomicboolean)、[AtomicInt](../reference/apis-arkts/arkts-sta-atomics.md#atomicint)等原子类型。
- 配置项较多且以键值方式访问时，可使用[ConcurrentHashMap (并发哈希表)](../reference/apis-arkts/arkts-sta-concurrenthashmap.md)管理配置数据。
- 不要在全局配置对象中保存UI组件、页面上下文等只能在宿主线程使用的对象。
