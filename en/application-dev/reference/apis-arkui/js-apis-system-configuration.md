# @system.configuration (Application Configuration)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
> **NOTE**
> - The APIs of this module are deprecated since API version 7. You are advised to use [@ohos.i18n](../apis-localization-kit/js-apis-i18n.md) and [@ohos.intl](../apis-localization-kit/js-apis-intl.md) instead.
>
> 
> - The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import


```ts
import Configuration from '@system.configuration';
```


## configuration.getLocale

static getLocale(): LocaleResponse

Obtains the current locale of the application, which is the same as the system locale.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Lite

**Return value**
| Type           | Description           |
| -------------- | ------------- |
| LocaleResponse | Current locale information.|

**Example**

ArkTS example:
  ```
  export default {    
    getLocale() {        
      const localeInfo = configuration.getLocale();        
      console.info(localeInfo.language);    
    }
  }
  ```

JS example:
```xml
<!-- xxx.hml -->
<div class="container">
    <text class="title" style="font-size: {{fontSize}}; color: {{fontColor}};">
        configuration.getLocale example
    </text>
    <div class="section">
        <text class="section-title">Language Settings:</text>
        <div class="info-item">
            <text class="value">{{language}}</text>
        </div>
    </div>
    <div class="section">
        <text class="section-title">Region Settings:</text>
        <div class="info-item">
            <text class="value">{{countryOrRegion}}</text>
        </div>
    </div>
    <div class="section">
        <text class="section-title">Layout direction:</text>
        <div class="info-item">
            <text class="value">{{dir}}</text>
        </div>
    </div>
    <input type="button" value="Refresh configuration" style="width: 350px; height: 50px; margin: 5px;" onclick="getLocaleInfo"></input>
</div>

```

```css
/* xxx.css */
.container {
    display: flex;
    flex-direction: column;
    align-items: center;
    left: 0px;
    top: 0px;
    width: 454px;
    height: 454px;
    background-color: #000000;
}
.title {
    font-size: 24px;
    text-align: center;
    width: 320px;
    height: 100px;
    margin-top: 40px;
    color: #ffffff;
}
.section {
    width: 400px;
    height: 60px;
    padding: 15px;
    background-color: #1a1a1a;
    border-radius: 10px;
}
.section-title {
    font-size: 24px;
    color: #007dff;
    height: 35px;
    margin-bottom: 10px;
}
.info-item {
    width: 100%;
    height: 35px;
}
.label {
    font-size: 24px;
    height: 40px;
    color: #aaaaaa;
}
.value {
    font-size: 24px;
    height: 40px;
    color: #ffffff;
}
```

```js
// xxx.js
import configuration from '@system.configuration';

export default {
    data: {
        fontSize: '28px',
        fontColor: '#ffffff',
        language: '',
        countryOrRegion: '',
        dir: '',
        displayLanguage: '',
        displayRegion: '',
        displayDir: ''
    },
    onInit() {
        this.getLocaleInfo();
    },
    getLocaleInfo() {
        try {
            const localeInfo = configuration.getLocale();
            console.info('configuration.getLocale success');
            console.info('language: ' + localeInfo.language);
            console.info('countryOrRegion: ' + localeInfo.countryOrRegion);
            console.info('dir: ' + localeInfo.dir);
            
            this.language = localeInfo.language || 'Unknown';
            this.countryOrRegion = localeInfo.countryOrRegion || 'Unknown';
            this.dir = localeInfo.dir || 'Unknown';
            
            this.displayLanguage = this.getDisplayLanguage(this.language);
            this.displayRegion = this.getDisplayRegion(this.countryOrRegion);
            this.displayDir = this.getDisplayDirection(this.dir);
        } catch (error) {
            console.error('configuration.getLocale failed: ' + error.message);
            this.language = 'Failed';
            this.countryOrRegion = 'Failed';
            this.dir = 'Failed';
            this.displayLanguage = 'Failed';
            this.displayRegion = 'Failed';
            this.displayDir = 'Failed';
        }
    },
    getDisplayLanguage(language) {
        const map = {
            'zh': 'Chinese',
            'en': 'English',
            'ja': 'Japanese',
            'ko': 'Korean'
        };
        return map[language] || language;
    },
    getDisplayRegion(region) {
        const map = {
            'CN': 'China',
            'US': 'United States',
            'JP': 'Japan',
            'KR': 'South Korea'
        };
        return map[region] || region;
    },
    getDisplayDirection(dir) {
        if (dir === 'ltr') {
            return 'Left to Right';
        } else if (dir === 'rtl') {
            return 'Right to Left';
        }
        return dir;
    }
}
```

## LocaleResponse

Defines attributes of the current locale.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Lite

| Name  | Type  | Readable  | Writable  | Description                                      |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| language | string | Yes   | No   | Language, for example, **zh**.|
| countryOrRegion | string | Yes   | No   | Country or region, for example, **CN**.|
| dir | string | Yes   | No   | Text layout direction. Available values are as follows:<br>- **ltr**: from left to right<br>- **rtl**: from right to left|
