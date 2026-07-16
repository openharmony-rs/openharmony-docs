# 媒体会话控制方
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

从API版本23开始，支持应用通过AVSession Kit获取媒体会话的播放信息和控制媒体会话的播放暂停等，实现对系统中的音视频应用进行统一的播放控制。该文档介绍媒体会话控制方接口能力及开发基本流程，包括获取媒体会话提供方的元数据，播放状态信息等，也可向媒体会话提供方发送命令及事件，控制媒体会话提供方的播放、暂停等。

## 基本概念

- [媒体会话提供方](using-avsession-developer.md)：音视频应用在实现音视频功能的同时，需要作为媒体会话提供方接入媒体会话，并响应媒体会话控制方下发的播控命令。

- 媒体会话描述符（AVSessionDescriptor）：描述媒体会话的相关信息，包含标识媒体会话的ID（sessionId），媒体会话的类型type（音频Audio/视频Video），媒体会话自定义名称（sessionTag），媒体会话所属应用的信息（elementName）、是否为置顶会话（isTopSession）等。

- 媒体会话控制器（AVSessionController）：会话控制器，可用于查看会话ID，向会话发送命令及事件，获取会话元数据、播放状态信息等操作。

- 置顶会话（TopSession）：系统中优先级最高的媒体会话，例如当前处于正在播放状态的会话。

## 接口说明

媒体会话控制方使用的关键接口包括两类：

1. 获取媒体会话描述符及媒体会话控制器，监听媒体会话的创建及销毁：通过AVSessionManager来调用，例如接口`AVSessionManager.createController(sessionId)`。
2. 获取媒体会话的元数据、播放状态信息等，监听媒体会话的元数据、播放状态变化等：通过AVSessionController对象来调用，例如接口`controller.getAVPlaybackState()`。

异步的JavaScript接口返回值有callback和promise两种返回形式。promise和callback只是返回值方式不一样，功能相同。

更多API说明请参见@ohos.multimedia.avsession (媒体会话管理)的[模块描述](../../reference/apis-avsession-kit/arkts-apis-avsession.md)。

## 开发步骤

应用作为媒体会话控制方接入的基本步骤如下所示：

1. 应用申请受限开放权限[ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC](../../security/AccessToken/restricted-permissions.md#ohospermissionmanage_media_resources_for_public)。当前仅少量符合特殊场景的应用可在通过审批后，使用受限权限，其申请方式请参考：[申请使用受限权限](../../security/AccessToken/declare-permissions-in-acl.md)。

2. 监听媒体会话的创建、销毁以及当前最新播放的媒体会话变更，并创建媒体会话对应的AVSessionController，从而对系统中的音视频应用进行统一的播放控制。

    ```TypeScript
    import { avSession } from '@kit.AVSessionKit';

    @Entry
    @Component
    struct Index {
        private controller: avSession.AVSessionController | undefined = undefined;
        private metadata: avSession.AVMetadata | undefined = undefined;
        private canPlay: boolean = false;  // 媒体会话是否支持播放。
        private canPause: boolean = false;  // 媒体会话是否支持暂停。

        aboutToAppear(): void {
            this.getAVSessionDescriptorsInfo();
            this.getControllerInfo();
            this.listenControllerInfo();
            this.getAVSessionValidCommands();
            this.listenAVSessionDestroy();
        }

        getAVSessionDescriptorsInfo() {
            try {
                // 获取所有设置过媒体信息且注册过控制回调的会话的描述符信息。
                avSession.getAllSessionDescriptors().then((descriptors: avSession.AVSessionDescriptor[]) => {
                    console.info(`Succeeded in getting all session descriptors, length: ${descriptors.length}`);
                });

                // 注册会话创建事件监听。
                avSession.onSessionCreate((descriptor: avSession.AVSessionDescriptor) => {
                    console.info(`on sessionCreate: sessionTag: ${descriptor.sessionTag}`);
                });

                // 注册最新播放会话变更监听。
                avSession.onTopSessionChange((descriptor: avSession.AVSessionDescriptor) => {
                    console.info(`on topSessionChange: sessionTag: ${descriptor.sessionTag}`);
                    // 创建每个会话对应的AVSessionController。
                    avSession.createController(descriptor.sessionId).then((controller: avSession.AVSessionController) => {
                        this.controller = controller;
                    });
                });
            } catch (error) {
                if (error) {
                    console.error(`avSession Error: Code: ${error.code}, message: ${error.message}`);
                }
            }
        }
    }
    ```

3. 获取媒体会话提供方传递的当前播放曲目及播放状态等。

    ```TypeScript
    getControllerInfo() {
        this.controller?.getAVMetadata((error: BusinessError, metadata: avSession.AVMetadata) => {
            if (error) {
                console.error(`Failed to get AV metadata, code: ${error.code}, message: ${error.message}`);
                return;
            }
            console.info(`Succeeded in getting AV metadata, assetId: ${metadata.assetId}`);
            this.metadata = metadata;
        });
    }
    ```

4. 监听媒体会话提供方的媒体信息变化及会话其他事件，从而应用可以根据回调及时刷新播放的曲目及播放状态。

    ```TypeScript
    listenControllerInfo() {
        try {
            this.controller?.on('metadataChange', 'all', (metadata: avSession.AVMetadata) => {
                console.info(`get metadata: ${metadata.title}`);
                this.metadata = metadata;
            });
        } catch (error) {
            if (error) {
                console.error(`metadataChange Error: Code: ${error.code}, message: ${error.message}`);
            }
        }
    }
    ```

5. 获取会话支持的有效命令，从而应用可以感知媒体会话提供方支持的命令。

    ```TypeScript
    getAVSessionValidCommands() {
        this.controller?.getValidCommands((error: BusinessError, validCommands: avSession.AVControlCommandType[]) => {
            if (error) {
                console.error(`Failed to get valid commands, code: ${error.code}, message: ${error.message}`);
                return;
            }
            console.info(`Succeeded in getting valid commands, size: ${validCommands.length}`);
            this.canPlay = !!validCommands['play'];
            this.canPause = !!validCommands['pause'];
        });
    }
    ```

6. 控制媒体会话行为，例如发送用户对当前曲目的操作（播放/暂停/上一首/下一首等）命令。

    ```TypeScript
    build() {
        Column() {
            Text(this.metadata?.title || '标题')

            Text('播放')
                .onClick(async () => {
                    if (this.canPlay) {
                        let command: avSession.AVControlCommand = {
                            command: 'play', // 播放指令。
                        }
                        await this.controller?.sendControlCommand(command);
                    }
                })

            Text('暂停')
                .onClick(async () => {
                    if (this.canPause) {
                        let command: avSession.AVControlCommand = {
                            command: 'pause', // 暂停指令。
                        }
                        await this.controller?.sendControlCommand(command);
                    }
                })
        }
        .width('100%')
        .height('100%')
    }
    ```

7. 媒体会话退出时，媒体会话控制方应及时取消监听，并释放资源。

    ```TypeScript
    listenAVSessionDestroy() {
        try {
            // 注册会话销毁监听。
            this.controller?.on('sessionDestroy', () => {
                console.info(`on sessionDestroy: SUCCESS`);
                this.controller?.destroy(() => { // 销毁当前控制器，销毁后当前控制器不可再用。
                    console.info('Succeeded in destroying.');
                });
            });
        } catch (error) {
            if (error) {
                console.error(`destroy Error: Code: ${error.code}, message: ${error.message}`);
            }
        }
    }

    aboutToDisappear(): void {
        avSession.offSessionCreate();
        avSession.offTopSessionChange();
    }
    ```