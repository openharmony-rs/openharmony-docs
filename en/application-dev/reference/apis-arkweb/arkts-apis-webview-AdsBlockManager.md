# Class (AdsBlockManager)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5bd67952550947311c46c7276be4f0642b76503e translatedAt=2026-08-07T04:44:33.927Z pushedAt=2026-08-07T07:07:40.474Z -->

AdsBlockManager is a class in the ArkWeb framework used to manage the ad filtering feature of Web components. It provides capabilities such as setting ad filtering rules, managing domain AllowedList/DisallowedList, and controlling filtering policies. All Web components in each app share a single AdsBlockManager static class. Developers can use this class to inject ad filtering configuration files that conform to the universal EasyList syntax into Web components and flexibly control the ad filtering status for specific websites.

The core mechanism of AdsBlockManager is based on a two-tier AllowedList/DisallowedList strategy using domain suffix matching: the DisallowedList is used to disable ad filtering for specific websites, while the AllowedList has a higher priority and can re-enable ad filtering for certain subdomains within the scope of the DisallowedList. After successful internal parsing, ad filtering rules are persistently stored and do not need to be set again after an app restart. However, they are not persistent and must be reconfigured after an app restart.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - The sample effect is subject to the actual device.
>
> - Static methods must be used on the user interface (UI) thread.

## Modules to Import

```ts
import { webview } from '@kit.ArkWeb';
```

## setAdsBlockRules<sup>12+</sup>

static setAdsBlockRules(rulesFile: string, replace: boolean): void

Sets a custom ad filtering configuration file that conforms to the universal EasyList syntax in the Web components.

> **NOTE**
>
> - The ad filtering rules set by this API will be persistently stored after successful internal parsing; you do not need to set them again after the app is restarted.
>
> - Starting from API version 18, calling this API on a device that does not support the ad filtering feature will throw an 801 exception.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type  | Mandatory| Description                              |
| ---------- | ------ | ---- | -------------------------------- |
| rulesFile | string | Yes | Path to the rule file that complies with EasyList syntax. The app must have read permission on this file. |
| replace   | boolean | Yes  | Whether to replace the built-in default rules. The value **true** indicates that the built-in default rules will be forcibly replaced; **false** indicates that the custom rules will work alongside the built-in default rules.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                 |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
|  801 | Capability not supported.  <br/>Applicable Version: 18+ |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { picker, fileUri } from '@kit.CoreFileKit';

// Demonstrate clicking a button to open an EasyList rule file through filepicker and set it to the Web component.
@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Row() {
      Flex() {
        Button({ type: ButtonType.Capsule }) {
          Text("setAdsBlockRules")
        }
        .onClick(() => {
          try {
            let documentSelectionOptions: ESObject = new picker.DocumentSelectOptions();
            let documentPicker: ESObject = new picker.DocumentViewPicker();
            documentPicker.select(documentSelectionOptions).then((documentSelectResult: ESObject) => {
              if (documentSelectResult && documentSelectResult.length > 0) {
                let fileRealPath = new fileUri.FileUri(documentSelectResult[0]);
                console.info('DocumentViewPicker.select successfully, uri: ' + fileRealPath);
                webview.AdsBlockManager.setAdsBlockRules(fileRealPath.path, true);
              }
            })
          } catch (err) {
            console.error(`DocumentViewPicker.select failed, Error code: ${err.code}, message: ${err.message}`);
          }
        })
      }
    }
  }
}
```

## addAdsBlockDisallowedList<sup>12+</sup>

static addAdsBlockDisallowedList(domainSuffixes: Array\<string\>): void

Adds an array of domain names to the disallowed list of this **AdsBlockManager** object. When the ad blocking feature is enabled, ad blocking for these websites will be disabled.

> **NOTE**
>
> - The domain names set by this API are not persistent; they need to be set again after the app is restarted.
>
> - The ad filtering feature uses suffix matching to determine whether the domainSuffix matches the URL of the current site. For example, if the website opened in the current Web component is https://www.example.com and the DisallowedList contains 'example.com' or 'www.example.com', the suffix match succeeds, ad filtering will be disabled for this website, and ad filtering will also be disabled when accessing 'https://m.example.com'.
>
> - Starting from API version 18, calling this API on a device that does not support the ad filtering feature will throw an 801 exception.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type  | Mandatory| Description                              |
| ---------- | ------ | ---- | -------------------------------- |
| domainSuffixes | Array\<string\> | Yes  | Array of domain names, for example, ['example.com', 'abcd.efg.com'].|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                 |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
|  801 | Capability not supported.  <br/>Applicable version: 18+ |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

// This example demonstrates how to click a button to add an array of domain names to the disallowed list.
@Entry
@Component
struct WebComponent {
  main_url: string = 'https://www.example.com';
  text_input_controller: TextInputController = new TextInputController();
  controller: webview.WebviewController = new webview.WebviewController();
  @State input_text: string = 'https://www.example.com';

  build() {
    Column() {
      Row() {
        Flex() {
          TextInput({ text: this.input_text, placeholder: this.main_url, controller: this.text_input_controller})
            .id("input_url")
            .height(40)
            .margin(5)
            .borderColor(Color.Blue)
            .onChange((value: string) => {
              this.input_text = value;
            })

          Button({type: ButtonType.Capsule}) { Text("Go") }
          .onClick(() => {
            this.controller.loadUrl(this.input_text);
          })

          Button({type: ButtonType.Capsule}) { Text("addAdsBlockDisallowedList") }
          .onClick(() => {
            let arrDomainSuffixes = new Array<string>();
            arrDomainSuffixes.push('example.com');
            arrDomainSuffixes.push('abcdefg.cn');
            webview.AdsBlockManager.addAdsBlockDisallowedList(arrDomainSuffixes);
          })
        }
      }
      Web({ src: this.main_url, controller: this.controller })
        .onControllerAttached(()=>{
          this.controller.enableAdsBlock(true);
        })
    }
  }
}
```

## removeAdsBlockDisallowedList<sup>12+</sup>

static removeAdsBlockDisallowedList(domainSuffixes: Array\<string\>): void

Removes an array of domain names from the disallowed list of this **AdsBlockManager** object.

> **NOTE**
>
> - The DisallowedList of AdsBlockManager is not persistent; it needs to be set again after the app is restarted. Removing an entry that does not exist does not trigger an exception.
>
> - Starting from API version 18, calling this API on a device that does not support the ad filtering feature will throw an 801 exception.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type  | Mandatory| Description                              |
| ---------- | ------ | ---- | -------------------------------- |
| domainSuffixes | Array\<string\> | Yes  | Array of domain names, for example, ['example.com', 'abcd.efg.com'].|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                 |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported. <br/>Applicable Version: 18+ |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

// This example demonstrates how to click a button to remove an array of domain names from the disallowed list.
@Entry
@Component
struct WebComponent {
  main_url: string = 'https://www.example.com';
  text_input_controller: TextInputController = new TextInputController();
  controller: webview.WebviewController = new webview.WebviewController();
  @State input_text: string = 'https://www.example.com';

  build() {
    Column() {
      Row() {
        Flex() {
          TextInput({ text: this.input_text, placeholder: this.main_url, controller: this.text_input_controller})
            .id("input_url")
            .height(40)
            .margin(5)
            .borderColor(Color.Blue)
            .onChange((value: string) => {
              this.input_text = value;
            })

          Button({type: ButtonType.Capsule}) { Text("Go") }
          .onClick(() => {
            this.controller.loadUrl(this.input_text);
          })

          Button({type: ButtonType.Capsule}) { Text("removeAdsBlockDisallowedList") }
          .onClick(() => {
            let arrDomainSuffixes = new Array<string>();
            arrDomainSuffixes.push('example.com');
            arrDomainSuffixes.push('abcdefg.cn');
            webview.AdsBlockManager.removeAdsBlockDisallowedList(arrDomainSuffixes);
          })
        }
      }
      Web({ src: this.main_url, controller: this.controller })
        .onControllerAttached(()=>{
          this.controller.enableAdsBlock(true);
        })
    }
  }
}
```

## clearAdsBlockDisallowedList<sup>12+</sup>

static clearAdsBlockDisallowedList(): void

Clears the disallowed list of this **AdsBlockManager** object.

> **NOTE**
>
> - The DisallowedList of AdsBlockManager is not persistent; it needs to be set again after the app is restarted.
>
> - Starting from API version 18, calling this API on a device that does not support the ad filtering feature will throw an 801 exception.

**System capability**: SystemCapability.Web.Webview.Core

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                 |
| -------- | ----------------------- |
| 801 | Capability not supported. <br/>Applicable Version: 18+ |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct WebComponent {
  main_url: string = 'https://www.example.com';
  text_input_controller: TextInputController = new TextInputController();
  controller: webview.WebviewController = new webview.WebviewController();
  @State input_text: string = 'https://www.example.com';

  build() {
    Column() {
      Row() {
        Flex() {
          TextInput({ text: this.input_text, placeholder: this.main_url, controller: this.text_input_controller})
            .id("input_url")
            .height(40)
            .margin(5)
            .borderColor(Color.Blue)
            .onChange((value: string) => {
              this.input_text = value;
            })

          Button({type: ButtonType.Capsule}) { Text("Go") }
          .onClick(() => {
            this.controller.loadUrl(this.input_text);
          })

          Button({type: ButtonType.Capsule}) { Text("clearAdsBlockDisallowedList") }
          .onClick(() => {
            webview.AdsBlockManager.clearAdsBlockDisallowedList();
          })
        }
      }
      Web({ src: this.main_url, controller: this.controller })
        .onControllerAttached(()=>{
          this.controller.enableAdsBlock(true);
        })
    }
  }
}
```

## addAdsBlockAllowedList<sup>12+</sup>

static addAdsBlockAllowedList(domainSuffixes: Array\<string\>): void

Adds an array of domain names to the AllowedList of this AdsBlockManager object. This API is typically used to re-enable ad filtering for certain websites in the DisallowedList.

> **NOTE**
>
> - The domain names set by this API are not persistent; they need to be set again after the app is restarted.
>
> - The AllowedList has a higher priority than the DisallowedList. For example, if ['example.com'] is configured in the DisallowedList, ad filtering is disabled for all web pages under the example.com domain. To enable ad filtering for 'news.example.com', you can use addAdsBlockAllowedList(['news.example.com']).
>
> - Starting from API version 18, calling this API on a device that does not support the ad filtering feature will throw an 801 exception.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type  | Mandatory| Description                              |
| ---------- | ------ | ---- | -------------------------------- |
| domainSuffixes | Array\<string\> | Yes  | Array of domain names, for example, ['example.com', 'abcd.efg.com'].|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                 |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
|  801 | Capability not supported.  <br/>Applicable Version: 18+ |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

// This example demonstrates how to click a button to add an array of domain names to the disallowed list.
@Entry
@Component
struct WebComponent {
  main_url: string = 'https://www.example.com';
  text_input_controller: TextInputController = new TextInputController();
  controller: webview.WebviewController = new webview.WebviewController();
  @State input_text: string = 'https://www.example.com';

  build() {
    Column() {
      Row() {
        Flex() {
          TextInput({ text: this.input_text, placeholder: this.main_url, controller: this.text_input_controller})
            .id("input_url")
            .height(40)
            .margin(5)
            .borderColor(Color.Blue)
            .onChange((value: string) => {
              this.input_text = value;
            })

          Button({type: ButtonType.Capsule}) { Text("Go") }
          .onClick(() => {
            this.controller.loadUrl(this.input_text);
          })

          Button({type: ButtonType.Capsule}) { Text("addAdsBlockAllowedList") }
          .onClick(() => {
            // Demonstrate the AllowedList priority: first disable all subdomains of example.com, then re-enable news.example.com.
            let arrDisallowDomainSuffixes = new Array<string>();
            arrDisallowDomainSuffixes.push('example.com');
            webview.AdsBlockManager.addAdsBlockDisallowedList(arrDisallowDomainSuffixes);

            let arrAllowedDomainSuffixes = new Array<string>();
            arrAllowedDomainSuffixes.push('news.example.com');
            webview.AdsBlockManager.addAdsBlockAllowedList(arrAllowedDomainSuffixes);
          })
        }
      }
      Web({ src: this.main_url, controller: this.controller })
        .onControllerAttached(()=>{
          this.controller.enableAdsBlock(true);
        })
    }
  }
}
```

## removeAdsBlockAllowedList<sup>12+</sup>

static removeAdsBlockAllowedList(domainSuffixes: Array\<string\>): void

Removes an array of domain names from the allowed list of this **AdsBlockManager** object.

> **NOTE**
>
> - The AllowedList of AdsBlockManager is not persistent; it needs to be set again after the app is restarted. Removing an entry that does not exist does not trigger an exception.
>
> - Starting from API version 18, calling this API on a device that does not support the ad filtering feature will throw an 801 exception.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name    | Type  | Mandatory| Description                              |
| ---------- | ------ | ---- | -------------------------------- |
| domainSuffixes | Array\<string\> | Yes  | Array of domain names, for example, ['example.com', 'abcd.efg.com'].|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                 |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
|  801 | Capability not supported.  <br/>Applicable Version: 18+ |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

// Demonstrate deleting a domain element from the AllowedList of AdsBlockManager via a button click.
@Entry
@Component
struct WebComponent {
  main_url: string = 'https://www.example.com';
  text_input_controller: TextInputController = new TextInputController();
  controller: webview.WebviewController = new webview.WebviewController();
  @State input_text: string = 'https://www.example.com';

  build() {
    Column() {
      Row() {
        Flex() {
          TextInput({ text: this.input_text, placeholder: this.main_url, controller: this.text_input_controller})
            .id("input_url")
            .height(40)
            .margin(5)
            .borderColor(Color.Blue)
            .onChange((value: string) => {
              this.input_text = value;
            })

          Button({type: ButtonType.Capsule}) { Text("Go") }
          .onClick(() => {
            this.controller.loadUrl(this.input_text);
          })

          Button({type: ButtonType.Capsule}) { Text("removeAdsBlockAllowedList") }
          .onClick(() => {
            let arrDomainSuffixes = new Array<string>();
            arrDomainSuffixes.push('example.com');
            arrDomainSuffixes.push('abcdefg.cn');
            webview.AdsBlockManager.removeAdsBlockAllowedList(arrDomainSuffixes);
          })
        }
      }
      Web({ src: this.main_url, controller: this.controller })
        .onControllerAttached(()=>{
          this.controller.enableAdsBlock(true);
        })
    }
  }
}
```

## clearAdsBlockAllowedList<sup>12+</sup>

static clearAdsBlockAllowedList(): void

Clears the allowed list of this **AdsBlockManager** object.

> **NOTE**
>
> - The AllowedList of AdsBlockManager is not persistent; it needs to be set again after the app is restarted.
>
> - Starting from API version 18, calling this API on a device that does not support the ad filtering feature will throw an 801 exception.

**System capability**: SystemCapability.Web.Webview.Core

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                 |
| -------- | ----------------------- |
|  801 | Capability not supported.  <br/>Applicable Version: 18+ |

**Example**

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct WebComponent {
  main_url: string = 'https://www.example.com';
  text_input_controller: TextInputController = new TextInputController();
  controller: webview.WebviewController = new webview.WebviewController();
  @State input_text: string = 'https://www.example.com';


  build() {
    Column() {
      Row() {
        Flex() {
          TextInput({ text: this.input_text, placeholder: this.main_url, controller: this.text_input_controller})
            .id("input_url")
            .height(40)
            .margin(5)
            .borderColor(Color.Blue)
            .onChange((value: string) => {
              this.input_text = value;
            })

          Button({type: ButtonType.Capsule}) { Text("Go") }
          .onClick(() => {
            this.controller.loadUrl(this.input_text);
          })

          Button({type: ButtonType.Capsule}) { Text("clearAdsBlockAllowedList") }
          .onClick(() => {
            webview.AdsBlockManager.clearAdsBlockAllowedList();
          })
        }
      }
      Web({ src: this.main_url, controller: this.controller })
      .onControllerAttached(()=>{
        this.controller.enableAdsBlock(true);
      })
    }
  }
}
```