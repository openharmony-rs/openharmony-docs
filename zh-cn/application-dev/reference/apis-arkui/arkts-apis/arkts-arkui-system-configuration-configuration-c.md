# Configuration

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite

## 导入模块

```TypeScript
import { Configuration, LocaleResponse } from '@kit.ArkUI';
```

## getLocale

```TypeScript
static getLocale(): LocaleResponse
```

获取应用当前的语言和地区。默认与系统的语言和地区同步。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LocaleResponse](arkts-arkui-system-configuration-localeresponse-i.md) | 应用当前Locale相关信息。 |

**示例**

ArkTS示例：

```TypeScript
export default {    
  getLocale() {        
    const localeInfo = Configuration.getLocale();        
    console.info(localeInfo.language);    
  }
}
```

JS示例：

```TypeScript
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

```TypeScript
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

```TypeScript
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
