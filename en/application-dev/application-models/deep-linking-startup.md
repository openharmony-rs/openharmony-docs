# Using Deep Linking for Application Redirection

In Deep Linking, the system, based on the passed-in URI, searches for the application that meets the conditions from the locally installed applications and starts that application. If multiple applications are matched, a dialog box is displayed for users to select one of them.

## Working Principles

Deep Linking searches for an application based on the URI matching rules in implicit Want mechanism and starts the matching application. For details about the URI matching rules of implicit Want, see [Matching Rules of uri](explicit-implicit-want-mappings.md#matching-rules-of-uri).


## Procedure for the Target Application

### Configuring the module.json5 File

To be accessed by other applications, an application must configure the [skills](../quick-start/module-configuration-file.md#skills) field of the [module.json5 file](../quick-start/module-configuration-file.md).

> **NOTE**
> 
> By default, the **skills** field contains a **skill** object, which is used to identify the application entry. Application redirection links should not be configured in this object. Instead, separate **skill** objects should be used. If there are multiple redirection scenarios, create different **skill** objects under **skills**. Otherwise, the configuration does not take effect.
> 
> In Deep Linking, the **scheme** value can be customized to any string that does not contain special characters and does not start with **ohos**. It is generally recommended to avoid using **https**, **http**, or **file** to prevent the default system browser from being launched.


A configuration example is as follows:

```json
{
  "module": {
    // ...
    "abilities": [
      {
        // ...
        "skills": [
          {
            "entities": [
              "entity.system.home"
            ],
            "actions": [
              "ohos.want.action.home"
            ]
          },
          {
            "actions": [
              // actions cannot be empty. Otherwise, matching the target application fails.
              "ohos.want.action.viewData"
            ],
            "uris": [
              {
                // scheme is mandatory and can be customized. The following uses link as an example. Replace it with the actual scheme.
                "scheme": "link",
                // host is mandatory. Configure the domain name to be matched.
                "host": "www.example.com"
              }
            ]
          } // Add a skill object for redirection. If there are multiple redirection scenarios, create multiple skill objects.
        ]
      }
    ]
  }
}
```

### Obtaining and Parsing the Link Passed by the Caller

In the **onCreate()** or **onNewWant()** lifecycle callback of the UIAbility of the target application, obtain and parse the Link passed by the caller.

```ts
// EntryAbility.ets is used as an example.
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { url } from '@kit.ArkTS';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    // Obtain the input link information from want.
    // For example, the input URL is link://www.example.com/programs?action=showall.
    let uri = want?.uri;
    if (uri) {
      // Parse the query parameter from the link. You can perform subsequent processing based on service requirements.
      let urlObject = url.URL.parseURL(want?.uri);
      let action = urlObject.params.get('action');
      // For example, if action is set to showall, all programs are displayed.
      if (action === "showall") {
         // ...
      }
    }
  }
}
```

## Implementing Application Redirection (Required for the Caller Application)

The following uses three cases to describe how to use [openLink()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#openlink12) and [startAbility()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability) to implement application redirection and how to implement application redirection in the [Web component](../reference/apis-arkweb/arkts-basic-components-web.md).

### Using openLink to Implement Application Redirection

Pass in the URL of the target application into **link** of [openLink()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#openlink12), and set **appLinkingOnly** in the **options** field to **false**.


The sample code is as follows:

```ts
import { common, OpenLinkOptions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[UIAbilityComponentsOpenLink]';
const DOMAIN_NUMBER: number = 0xFF00;

@Entry
@Component
struct Index {
  build() {
    Button('start link', { type: ButtonType.Capsule, stateEffect: true })
      .width('87%')
      .height('5%')
      .margin({ bottom: '12vp' })
      .onClick(() => {
        let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
        let link: string = "link://www.example.com";
        let openLinkOptions: OpenLinkOptions = {
          appLinkingOnly: false
        };

        try {
          context.openLink(link, openLinkOptions)
            .then(() => {
              hilog.info(DOMAIN_NUMBER, TAG, 'open link success.');
            }).catch((err: BusinessError) => {
              hilog.error(DOMAIN_NUMBER, TAG, `open link failed. Code is ${err.code}, message is ${err.message}`);
            });
        } catch (paramError) {
          hilog.error(DOMAIN_NUMBER, TAG, `Failed to start link. Code is ${paramError.code}, message is ${paramError.message}`);
        }
      })
  }
}
```

### Using startAbility() to Implement Application Redirection

Pass in the target application's link into **want** of [startAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability), which then uses [implicit Want](explicit-implicit-want-mappings.md#matching-rules-of-implicit-want) to trigger application redirection. In addition, you must pass in the **action** and **entity** fields to be matched.


The sample code is as follows:

```ts
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[UIAbilityComponentsOpenLink]';
const DOMAIN_NUMBER: number = 0xFF00;

@Entry
@Component
struct Index {
  build() {
    Button('start ability', { type: ButtonType.Capsule, stateEffect: true })
      .width('87%')
      .height('5%')
      .margin({ bottom: '12vp' })
      .onClick(() => {
        let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
        let want: Want = {
          uri: "link://www.example.com"
        };

        try {
          context.startAbility(want).then(() => {
            hilog.info(DOMAIN_NUMBER, TAG, 'start ability success.');
          }).catch((err: BusinessError) => {
            hilog.error(DOMAIN_NUMBER, TAG, `start ability failed. Code is ${err.code}, message is ${err.message}`);
          });
        } catch (paramError) {
          hilog.error(DOMAIN_NUMBER, TAG, `Failed to start ability. Code is ${paramError.code}, message is ${paramError.message}`);
        }
      })
  }
}
```

### Using the Web Component to Implement Application Redirection

To implement application redirection from a **Web** component in Deep Linking mode, process the defined event in the [onLoadIntercept](../reference/apis-arkweb/arkts-basic-components-web-events.md#onloadintercept10) callback.

The sample code is as follows:

```ts
// index.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Web({ src: $rawfile('index.html'), controller: this.controller })
        .onLoadIntercept((event) => {
          const url: string = event.data.getRequestUrl();
          if (url === 'link://www.example.com') {
            (this.getUIContext().getHostContext() as common.UIAbilityContext).openLink(url)
              .then(() => {
                console.log('openLink success');
              }).catch((err: BusinessError) => {
                console.error('openLink failed, err:' + JSON.stringify(err));
              });
            return true;
          }
          // If true is returned, the loading is blocked. Otherwise, the loading is allowed.
          return false;
        })
    }
  }
}
```

Frontend page code:
```html
// index.html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
</head>
<body>
<h1>Hello World</h1>
<!--Method 1: Bind window.open to implement redirection.-->;
<button class="doOpenLink" onclick="doOpenLink()">Redirect to application 1</button>
<!--Method 2: Use a hyperlink for redirection.-->;
<a href="link://www.example.com">Redirect to application 2</a>
</body>
</html>
<script>
    function doOpenLink() {
        window.open("link://www.example.com")
    }
</script>
```

<!--no_check-->