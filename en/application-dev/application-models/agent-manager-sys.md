# Using the Agent Service Provided by the AgentExtensionAbility Component (System Applications Only)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1630992de2f5af1dcca3ca27d11e23e0321182c9 translatedAt=2026-05-30T07:46:15.993Z pushedAt=2026-06-01T09:29:18.078Z -->

## Overview

Starting from API version 24, system applications can use the [connectAgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentManager-sys.md#agentmanagerconnectagentextensionability) method in agentManager to connect to the [AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md) component implemented by other applications and use the agent service it provides. System applications and agents can perform bidirectional communication and bidirectional security authentication.

> **NOTE**
>
> In this document, the connected [AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md) is referred to as the server, and the component that connects to the [AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md) is referred to as the client.

## Overview of the Interaction Mechanism Between the Client and Server

The interaction process between the client and server is shown in the following figure:



1. Establishing a connection

    The client can connect to the server's [AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md) by calling the [connectAgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentManager-sys.md#agentmanagerconnectagentextensionability) method in agentManager (specifying the target service to connect to in the [Want](../reference/apis-ability-kit/js-apis-app-ability-want.md) object).

    After a connection is successfully established, the server's [onConnect()](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md#onconnect) method is triggered, and in this method, the server receives the [Want](../reference/apis-ability-kit/js-apis-app-ability-want.md) object passed by the client and the client's [AgentHostProxy](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md) object.

2. Sending and Receiving Data

    The client connects to the server by calling the [connectAgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentManager-sys.md#agentmanagerconnectagentextensionability) method and receives the returned [AgentProxy](../reference/apis-ability-kit/js-apis-inner-application-agentProxy-sys.md) object. The client can use the [sendData()](../reference/apis-ability-kit/js-apis-inner-application-agentProxy-sys.md#senddata) method of this [AgentProxy](../reference/apis-ability-kit/js-apis-inner-application-agentProxy-sys.md) object to send data to the server.

    The server can receive the data sent by the client and the [AgentHostProxy](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md) object in the [onData()](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md#ondata) method, and can send data to the client through the [sendData()](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md#senddata) method of [AgentHostProxy](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md).

    The client receives the data sent by the server through the [onData()](../reference/apis-ability-kit/js-apis-inner-application-agentExtensionConnectCallback-sys.md#ondata) method in [AgentExtensionConnectCallback](../reference/apis-ability-kit/js-apis-inner-application-agentExtensionConnectCallback-sys.md).

3. Security Authentication (Optional)

    The client connects to the server by calling the [connectAgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentManager-sys.md#agentmanagerconnectagentextensionability) method and receives the returned [AgentProxy](../reference/apis-ability-kit/js-apis-inner-application-agentProxy-sys.md) object. The client can use the [authorize()](../reference/apis-ability-kit/js-apis-inner-application-agentProxy-sys.md#authorize) method of this [AgentProxy](../reference/apis-ability-kit/js-apis-inner-application-agentProxy-sys.md) object to send a security authentication request to the server.

    The server can receive the security authentication request sent by the client and the [AgentHostProxy](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md) object in the [onAuth()](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md#onauth) method, and can send a security authentication request to the client through the [authorize()](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md#authorize) method of [AgentHostProxy](../reference/apis-ability-kit/js-apis-inner-application-agentHostProxy.md).

    The client receives the security authentication request sent by the server through the [onAuth()](../reference/apis-ability-kit/js-apis-inner-application-agentExtensionConnectCallback-sys.md#onauth) method of [AgentExtensionConnectCallback](../reference/apis-ability-kit/js-apis-inner-application-agentExtensionConnectCallback-sys.md).

4. Disconnecting

    When the client connects to the server by calling the [connectAgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentManager-sys.md#agentmanagerconnectagentextensionability) method, it can save the [AgentProxy](../reference/apis-ability-kit/js-apis-inner-application-agentProxy-sys.md) object returned by the server. The client can disconnect from the server by calling the [disconnectAgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentManager-sys.md#agentmanagerdisconnectagentextensionability) method using the saved [AgentProxy](../reference/apis-ability-kit/js-apis-inner-application-agentProxy-sys.md) object.

## Connecting to and Disconnecting from AgentExtensionAbility

- Use the [connectAgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentManager-sys.md#agentmanagerconnectagentextensionability) method to establish a connection with [AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md).

    <!-- @[agent_manager_one](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ConnectAgentExtension/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    import { common, Want, agentManager } from '@kit.AbilityKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    
    @Entry
    @Component
    struct Index {
      comProxy: common.AgentProxy | null = null;
      connectCallback: common.AgentExtensionConnectCallback = {
        onData: (data: string) => {
          console.info(`onData, data: ${data}.`);
        },
        onAuth: (handShakeData: string): void => {
          console.info(`onData, data: ${handShakeData}.`);
        },
        onDisconnect: () => {
          console.info(`onDisconnect.`);
          this.comProxy = null;
        }
      }
    
      build() {
        Column() {
          Row() {
            // Creating a Connection Button
            Button('connect ability')
              .enabled(true)
              .onClick(() => {
                let connectWant: Want = {
                  bundleName: 'com.sample.agentextensionability',
                  abilityName: 'AgentExtAbility',
                };
                let agentId: string = 'weather_assistant_001';
                try {
                  // Connecting to AgentExtensionAbility
                  agentManager.connectAgentExtensionAbility(connectWant, agentId, this.connectCallback)
                    .then((proxy: common.AgentProxy) => {
                      this.comProxy = proxy;
                      // ...
                    })
                    .catch((err: BusinessError) => {
                      console.error(`connectAgentExtensionAbility failed, err code: ${err.code}, err msg: ${err.message}.`);
                    });
                } catch (err) {
                  let code = (err as BusinessError).code;
                  let msg = (err as BusinessError).message;
                  console.error(`connectAgentExtensionAbility failed, err code: ${code}, err msg: ${msg}.`);
                }
              })
            // ...
          }
        }
      }
    }
    ```

- Use the [disconnectAgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentManager-sys.md#agentmanagerdisconnectagentextensionability) method to disconnect from [AgentExtensionAbility](../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md).

    <!-- @[agent_manager_two](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ConnectAgentExtension/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    import { common, Want, agentManager } from '@kit.AbilityKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    
    @Entry
    @Component
    struct Index {
      comProxy: common.AgentProxy | null = null;
      connectCallback: common.AgentExtensionConnectCallback = {
        onData: (data: string) => {
          console.info(`onData, data: ${data}.`);
        },
        onAuth: (handShakeData: string): void => {
          console.info(`onData, data: ${handShakeData}.`);
        },
        onDisconnect: () => {
          console.info(`onDisconnect.`);
          this.comProxy = null;
        }
      }
    
      build() {
        Column() {
          Row() {
            // ...
            // Create a disconnect button
            Button('disconnect ability')
              .enabled(true)
              .onClick(() => {
                try{
                  // this.agentProxy is the proxy object saved during connection
                  agentManager.disconnectAgentExtensionAbility(this.comProxy).then(() => {
                    console.info(`disconnectAgentExtensionAbility success.`);
                  }).catch((error: BusinessError) => {
                    console.error(`disconnectAgentExtensionAbility failed, err code: ${error.code}, err msg: ${error.message}.`);
                  });
                } catch (err) {
                  let code = (err as BusinessError).code;
                  let msg = (err as BusinessError).message;
                  console.error(`connectAgentExtensionAbility failed, err code: ${code}, err msg: ${msg}.`);
                }
              })
          }
        }
      }
    }
    ```

## Two-way communication between client and server

- Client sends and receives data

    <!-- @[agent_manager_three](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ConnectAgentExtension/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    import { common, Want, agentManager } from '@kit.AbilityKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    
    @Entry
    @Component
    struct Index {
      comProxy: common.AgentProxy | null = null;
      connectCallback: common.AgentExtensionConnectCallback = {
        onData: (data: string) => {
          console.info(`onData, data: ${data}.`);
        },
        onAuth: (handShakeData: string): void => {
          console.info(`onData, data: ${handShakeData}.`);
        },
        onDisconnect: () => {
          console.info(`onDisconnect.`);
          this.comProxy = null;
        }
      }
    
      build() {
        Column() {
          Row() {
            // Create a connect button
            Button('connect ability')
              .enabled(true)
              .onClick(() => {
                let connectWant: Want = {
                  bundleName: 'com.sample.agentextensionability',
                  abilityName: 'AgentExtAbility',
                };
                let agentId: string = 'weather_assistant_001';
                try {
                  // Connecting to AgentExtensionAbility
                  agentManager.connectAgentExtensionAbility(connectWant, agentId, this.connectCallback)
                    .then((proxy: common.AgentProxy) => {
                      this.comProxy = proxy;
                      let data = 'test data';
                      try {
                        this.comProxy.sendData(data);
                      } catch (err) {
                        let code = (err as BusinessError).code;
                        let msg = (err as BusinessError).message;
                        console.error(`sendData failed, err code: ${code}, err msg: ${msg}.`);
                      }
                      // ...
                    })
                    .catch((err: BusinessError) => {
                      console.error(`connectAgentExtensionAbility failed, err code: ${err.code}, err msg: ${err.message}.`);
                    });
                } catch (err) {
                  let code = (err as BusinessError).code;
                  let msg = (err as BusinessError).message;
                  console.error(`connectAgentExtensionAbility failed, err code: ${code}, err msg: ${msg}.`);
                }
              })
            // ...
          }
        }
      }
    }
    ```

- Server sends and receives data

  For details, see [Using AgentExtensionAbility to Send and Receive Data](agent-extension-ability.md#using-agentextensionability-to-send-and-receive-data).

## Two-Way Security Authentication Between Client and Server

- Client processes and sends security authentication requests

    <!-- @[agent_manager_four](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/ConnectAgentExtension/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    import { common, Want, agentManager } from '@kit.AbilityKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    
    @Entry
    @Component
    struct Index {
      comProxy: common.AgentProxy | null = null;
      connectCallback: common.AgentExtensionConnectCallback = {
        onData: (data: string) => {
          console.info(`onData, data: ${data}.`);
        },
        onAuth: (handShakeData: string): void => {
          console.info(`onData, data: ${handShakeData}.`);
        },
        onDisconnect: () => {
          console.info(`onDisconnect.`);
          this.comProxy = null;
        }
      }
    
      build() {
        Column() {
          Row() {
            // Create Connection Button
            Button('connect ability')
              .enabled(true)
              .onClick(() => {
                let connectWant: Want = {
                  bundleName: 'com.sample.agentextensionability',
                  abilityName: 'AgentExtAbility',
                };
                let agentId: string = 'weather_assistant_001';
                try {
                  // Connecting to AgentExtensionAbility
                  agentManager.connectAgentExtensionAbility(connectWant, agentId, this.connectCallback)
                    .then((proxy: common.AgentProxy) => {
                      this.comProxy = proxy;
                      // ...
                      let authorizeData = 'authorize data';
                      try {
                        this.comProxy.authorize(authorizeData);
                      } catch (err) {
                        let code = (err as BusinessError).code;
                        let msg = (err as BusinessError).message;
                        console.error(`sendData failed, err code: ${code}, err msg: ${msg}.`);
                      }
                    })
                    .catch((err: BusinessError) => {
                      console.error(`connectAgentExtensionAbility failed, err code: ${err.code}, err msg: ${err.message}.`);
                    });
                } catch (err) {
                  let code = (err as BusinessError).code;
                  let msg = (err as BusinessError).message;
                  console.error(`connectAgentExtensionAbility failed, err code: ${code}, err msg: ${msg}.`);
                }
              })
            // ...
          }
        }
      }
    }
    ```

- Server processes and sends security authentication requests

  For details, see [Using AgentExtensionAbility to Receive and Send Security Authentication Requests](agent-extension-ability.md#using-agentextensionability-to-receive-and-send-security-authentication-requests).