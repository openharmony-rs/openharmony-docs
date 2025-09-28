# Using startAbilityByType to Start an Email Application

<!--Kit: Ability Kit-->
<!--Subsystem: AGC-->
<!--Owner: @liusu23-->
<!--Designer: @xukeke-->
<!--Tester: @lusq-->
<!--Adviser: @huipeizi-->

This topic describes how to open the vertical domain panel of email applications.
> **NOTE**
> 
> If the parameter from the initiating application is a mailto string, you are advised to [use mailto to start an email application](start-email-apps-by-mailto.md). Upon receiving the mailto string, the email application parses the string to fill in details like the sender, recipient, and email body.

## Parameters on the Email Application Panel

If the **type** field in **startAbilityByType** is set to **mail**, **wantParam** contains the following properties.

| Name                               | Type                                                        | Mandatory| Description                                                        |
| ------------------------------------- | ------------------------------------------------------------ | ------ | ------------------------------------------------------------ |
| email                                 | string[ ]                                                    | No  | Email address of the recipient. Multiple email addresses, separated by commas (,), are supported.                      |
| cc                                    | string[ ]                                                    | No  | Email address of the CC recipient. Multiple email addresses, separated by commas (,), are supported.                      |
| bcc                                   | string[ ]                                                    | No  | Email address of the BCC recipient. Multiple email addresses, separated by commas (,), are supported.                      |
| subject                               | string                                                       | No  | Email subject.                                                    |
| body                                  | string                                                       | No  | Email body.                                                    |
| ability.params.stream                 | string[ ]                                                    | No  | Email attachments (URI list of the attachments).                               |
| ability.want.params.uriPermissionFlag | [wantConstant.Flags](../reference/apis-ability-kit/js-apis-app-ability-wantConstant.md#flags) | No  | At least the read permission must be granted on the email attachments. This parameter is mandatory when **ability.params.stream** is specified.|
| sceneType                             | number                                                       | No  | Intent scene, which indicates the purpose of the current request. 1: Send an email. The default value is **1**.                             |

> **NOTE**
>
> * Parameters of the string type displayed in the vertical domain panel of email applications must be encoded using **encodeURI**.
> 
> * For parameters of the string[] type displayed in the vertical domain panel of email applications, all elements in the array must be encoded using **encodeURI**.

## Developing a Caller Application
1. Import the module.
    ```ts
    import { common, wantConstant } from '@kit.AbilityKit';
    ```
2. Construct parameters and call the **startAbilityByType** API.

    ```ts
    @Entry
    @Component
    struct Index {
        @State hideAbility: string = 'hideAbility'

        build() {
            Row() {
                Column() {
                    Text(this.hideAbility)
                        .fontSize(30)
                        .fontWeight(FontWeight.Bold)
                        .onClick(() => {
                            let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
                            let wantParam: Record<string, Object> = {
                                'sceneType': 1,
                                'email': [encodeURI('xxx@example.com'), encodeURI('xxx@example.com')], // Email address of the recipient. Multiple values are separated by commas (,). The array content is URL encoded using encodeURI().
                                'cc': [encodeURI('xxx@example.com'), encodeURI('xxx@example.com')], // Email address of the CC recipient. Multiple values are separated by commas (,). The array content is URL encoded using encodeURI().
                                'bcc': [encodeURI('xxx@example.com'), encodeURI('xxx@example.com')], // Email address of the BCC recipient. Multiple values are separated by commas (,). The array content is URL encoded using encodeURI().
                                'subject': encodeURI('Email subject'), // Email subject. The content is URL encoded using encodeURI().
                                'body': encodeURI('Email body'), // Email body. The content is URL encoded using encodeURI().
                                'ability.params.stream':[encodeURI('attachment uri1'), encodeURI('attachment uri2')], // Attachment URIs. Multiple values are separated by commas (,). The array content is URL encoded using encodeURI().
                                'ability.want.params.uriPermissionFlag': wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION
                            };
                            let abilityStartCallback: common.AbilityStartCallback = {
                                onError: (code: number, name: string, message: string) => {
                                    console.error(`onError code ${code} name: ${name} message: ${message}`);
                                },
                                onResult: (result) => {
                                    console.info(`onResult result: ${JSON.stringify(result)}`);
                                }
                            }

                            context.startAbilityByType("mail", wantParam, abilityStartCallback,
                                (err) => {
                                    if (err) {
                                        console.error(`startAbilityByType fail, err: ${JSON.stringify(err)}`);
                                    } else {
                                        console.info(`success`);
                                    }
                                });
                        });
                }
                .width('100%')
            }
            .height('100%')
        }
    }
    ```
    Effect
    
    ![Effect example](./figures/start-mail-panel.png)

## Developing a Target Application

1. Add the [linkFeature](../quick-start/module-configuration-file.md#skills) attribute to **module.json5** and declare the features supported. In this way, the system can find the applications that support a specific feature from all the applications installed on the device.

    | Value          | Description                     |
    | --------------| ------------------------- |
    | ComposeMail   | The application supports email writing.	|

    ```json
    {
      "abilities": [
          {
          "skills": [
              {
              "uris": [
                  {
                  "scheme": "mailto", // It is for reference only. Ensure that the declared URI can be started by external systems.
                  "host": "",
                  "path": "",
                  "linkFeature": "ComposeMail" // Declare that the application supports email writing.
                  }
                ]
              }
          ]
          }
      ]
    }
    ```
    
2. Parse and process the parameters transferred from the panel.

    ```ts
    UIAbility.onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void
    ```

    The **want.parameters** parameter contains the following parameters, which may be slightly different from the ones passed in by the caller.

    | Name | Type     | Mandatory| Description                                  |
    | ------- | --------- | ---- | -------------------------------------- |
    | email   | string[ ] | No  | Email address of the recipient. Multiple email addresses, separated by commas (,), are supported.|
    | cc      | string[ ] | No  | Email address of the CC recipient. Multiple email addresses, separated by commas (,), are supported.|
    | bcc     | string[ ] | No  | Email address of the BCC recipient. Multiple email addresses, separated by commas (,), are supported.|
    | subject | string    | No  | Email subject.                              |
    | body    | string    | No  | Email body.                              |
    | stream  | string[ ] | No  | Email attachments (URI list of the attachments).     |
    
    > **NOTE**
    > 
    > * Parameters of the string type received by the target application must be decoded using **decodeURI**.
    > 
    > * For parameters of the string[] type received by the target application, all elements in the array must be decoded using **decodeURI**.

**Sample Code**

```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';

const TAG = 'MailTarget1.EntryAbility'

export default class EntryAbility extends UIAbility {
    windowStage: window.WindowStage | null = null;

    email: string[] | undefined;
    cc: string[] | undefined;
    bcc: string[] | undefined;
    subject: string | undefined;
    body: string | undefined;
    stream: string[] | undefined;
    
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        hilog.info(0x0000, TAG, `onCreate, want=${JSON.stringify(want)}`);
        super.onCreate(want, launchParam);
        this.parseWant(want);
    }

    onNewWant(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        hilog.info(0x0000, TAG, `onNewWant, want=${JSON.stringify(want)}`);
        super.onNewWant(want, launchParam);
        this.parseWant(want);
        if (!this.windowStage) {
            hilog.error(0x0000, TAG, 'windowStage is null');
            this.context.terminateSelf();
            return;
        }
        this.loadPage(this.windowStage);
    }

    private parseWant(want: Want): void {
        this.email = this.decodeStringArr(want.parameters?.email as string[]);
        this.cc = this.decodeStringArr(want.parameters?.cc as string[]);
        this.bcc = this.decodeStringArr(want.parameters?.bcc as string[]);
        this.subject = decodeURI(want.parameters?.subject as string); // Use decodeURI() to decode the URL of the email subject. Other fields are processed in the same way.
        this.body = decodeURI(want.parameters?.body as string); // Use decodeURI() to decode the URL of the email body. Other fields are processed in the same way.
        this.stream = this.decodeStringArr(want.parameters?.stream as string[]);
    }

    // Use decodeURI() to decode the content in the string array.
    private decodeStringArr(source: string[] | undefined): string[] {
        let target: string[] = [];
        source?.forEach(e => {
            target.push(decodeURI(e));
        })
        return target;
    }

    private loadPage(windowStage: window.WindowStage): void {
        const storage: LocalStorage = new LocalStorage({
            "email": this.email,
            "cc": this.cc,
            "bcc": this.bcc,
            "subject": this.subject,
            "body": this.body,
            "stream": this.stream
        } as Record<string, Object>);

        windowStage.loadContent('pages/ComposeMailPage', storage);

    }

    onDestroy(): void {
        hilog.info(0x0000, TAG, `onDestroy`);
    }

    onWindowStageCreate(windowStage: window.WindowStage): void {
        hilog.info(0x0000, TAG, `onWindowStageCreate`);
        this.windowStage = windowStage;
        this.loadPage(this.windowStage);
    }

    onWindowStageDestroy(): void {
        hilog.info(0x0000, TAG, `onWindowStageDestroy`);
    }

    onForeground(): void {
        hilog.info(0x0000, TAG, `onForeground`);
    }

    onBackground(): void {
        hilog.info(0x0000, TAG, `onBackground`);
    }
}
```
