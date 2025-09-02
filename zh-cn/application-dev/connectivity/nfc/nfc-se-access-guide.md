# 安全单元访问开发指南

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @amunra03-->
<!--Designer: @wenxiaolin-->
<!--Tester: @zs_111-->

## 简介
安全单元（SecureElement，简称SE），电子设备上可能存在一个或多个安全单元，比如有eSE(Embedded SE)和SIM卡。能够充当安全单元的SIM卡，要求具备NFC功能。

## 场景介绍
应用程序可以通过接口访问安全单元，比如往安全单元里面写入数据，实现在电子设备上模拟一张NFC卡片的目的。该卡片数据可能存储在eSE安全单元，或在SIM卡安全单元上。安全单元上一般会预置有访问控制规则，应用程序需要具备对应的权限，也就是通过安全单元的访问控制权限校验之后，才能正常访问安全单元。

## 接口说明
完整的JS API说明以及实例代码请参考：[安全单元接口](../../reference/apis-connectivity-kit/js-apis-secureElement.md)。
实现安全单元的访问，可能使用到下面的接口。

| 接口名                             | 功能描述                                                                       |
| ---------------------------------- | ------------------------------------------------------------------------------ |
| createService(): Promise\<SEService>                    | 建立一个可用于连接到系统中所有可用SE的新连接。                                                               |
| getReaders(): Reader[]                      | 返回可用SE Reader的数组，包含该设备上支持的所有的安全单元。                                                                |
| openSession(): Session                 | 在SE Reader实例上创建连接会话，返回Session实例。                                                                |
| openLogicalChannel(aid: number[]): Promise\<Channel>                  | 打开逻辑通道，返回逻辑Channel实例对象。                                                                |
| transmit(command: number[]): Promise\<number[]> | 向SE发送APDU数据                                                                |
| close(): void | 关闭Channel。                                                            |


## 主要场景开发步骤

### 应用程序访问安全单元
1. import需要的安全单元模块。
2. 判断设备是否支持安全单元能力。
3. 访问安全单元，实现数据的读取或写入。
   
```ts
import { omapi } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

let seService : omapi.SEService;
let seReaders : omapi.Reader[];
let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];
let p2 : number = 0x00;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');

    // 判断设备是否支持安全单元能力
    if (!canIUse("SystemCapability.Communication.SecureElement")) {
      hilog.error(0x0000, 'testTag', 'secure element unavailable.');
      return;
    }
    hilog.info(0x0000, 'testTag', 'secure element available.');
    this.omaTest();
  }

  private async omaTest () {
    // 获取 service
    await omapi.createService().then((data) => {
      if (data == undefined || !data.isConnected()) {
        hilog.error(0x0000, 'testTag', 'secure element service disconnected.');
        return;
      }
      seService = data;
      hilog.info(0x0000, 'testTag', 'secure element service connected.');
    }).catch((error: BusinessError) => {
      hilog.error(0x0000, 'testTag', 'createService error %{public}s', JSON.stringify(error));
      return;
    });

    // 获取 readers
    try {
      seReaders = seService.getReaders();
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'getReaders error %{public}s', JSON.stringify(error));
    }
    if (seReaders == undefined || seReaders.length == 0) {
      hilog.error(0x0000, 'testTag', 'no valid reader found.');
      seService.shutdown();
      return;
    }
    let reader: (omapi.Reader | undefined);
    for (let i = 0; i < seReaders.length; ++i) {
      let r = seReaders[i];
      if (r.getName().includes("SIM")) {
        reader = r;
        break;
      }
    }
    if (reader == undefined) {
      hilog.error(0x0000, 'testTag', 'no valid sim reader.');
      return;
    }
    hilog.info(0x0000, 'testTag', 'reader is %{public}s', reader?.getName());

    // 获取 session
    try {
      seSession = reader?.openSession() as omapi.Session;
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'openSession error %{public}s', JSON.stringify(error));
    }
    if (seSession == undefined) {
      hilog.error(0x0000, 'testTag', 'seSession invalid.');
      seService.shutdown();
      return;
    }

    // 获取 channel
    try {
      // change the aid value for open logical channel
      // 修改为打开逻辑通道的应用的aid值
      seChannel = await seSession.openLogicalChannel(aidArray, p2);
    } catch (exception) {
      hilog.error(0x0000, 'testTag', 'openLogicalChannel exception %{public}s', JSON.stringify(exception));
    }

    if (seChannel == undefined) {
      hilog.error(0x0000, 'testTag', 'seChannel invalid.');
      return;
    }

    // 发送数据
    let cmdData = [0x01, 0x02, 0x03, 0x04]; // 请更改为正确的data
    try {
      let response: number[] = await seChannel.transmit(cmdData)
      hilog.info(0x0000, 'testTag', 'seChannel.transmit() response = %{public}s.', JSON.stringify(response));
    } catch (exception) {
      hilog.error(0x0000, 'testTag', 'seChannel.transmit() exception = %{public}s.', JSON.stringify(exception));
    }

    // 关闭通道，必须确保通道最终关闭
    try {
      seChannel.close();
    } catch (exception) {
      hilog.error(0x0000, 'testTag', 'seChannel.close() exception = %{public}s.', JSON.stringify(exception));
    }

  }
}

```