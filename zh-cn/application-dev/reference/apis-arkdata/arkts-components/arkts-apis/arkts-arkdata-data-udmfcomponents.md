# @ohos.data.UdmfComponents(内容卡片)

## 导入模块

```TypeScript
import { ContentFormCard, FormType } from '@kit.ArkData';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ContentFormCard](arkts-arkdata-data-udmfcomponents-contentformcard-s.md) | 内容卡片控件，用于在应用内展示标题、描述、内容图片、应用信息等。适用于内容分发、社交动态、消息通知等场景。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [FormType](arkts-arkdata-data-udmfcomponents-formtype-e.md) | 内容卡片类型枚举，提供了大、中、小三种尺寸。 |

## 示例

```TypeScript
// 导入所需模块
import { uniformDataStruct } from '@kit.ArkData'

@Entry
@Component
struct Index {
  // 定义内容卡片数据
  @State contentForm: uniformDataStruct.ContentForm = {
    uniformDataType: 'general.content-form',
    title: ''
  };
  // 控制卡片显示状态
  @State startToShow: boolean = false;

  // 组件即将显示时初始化数据
  aboutToAppear(): void {
    this.initData();
  }

  // 初始化内容卡片数据
  async initData() {
    // 获取应用上下文
    let context = this.getUIContext().getHostContext();
    if (!context) {
      return;
    }
    try {
      // 加载应用图标和缩略图资源
      let appIcon = await context.resourceManager.getMediaContent($r('app.media.startIcon').id);
      let thumbImage = await context.resourceManager.getMediaContent($r('app.media.foreground').id);
      // 构建内容卡片数据对象
      this.contentForm = {
        uniformDataType: 'general.content-form',
        title: 'Content form title',
        thumbData: appIcon,
        description: 'Content form description',
        appIcon: thumbImage,
        appName: 'com.test.demo'
      };
    } catch (err) {
      console.error(`Init data error`);
    }
  }

  // 构建UI界面
  build() {
    Column() {
      // 显示按钮，点击后展示内容卡片
      Button('show card')
        .onClick(() => {
          this.startToShow = true;
        })
      // 条件渲染内容卡片组件
      if (this.startToShow) {
        ContentFormCard({
          contentFormData: this.contentForm,
          formType: FormType.TYPE_SMALL,
          formWidth: 110,
          formHeight: 50,
          // 点击卡片的回调函数
          handleOnClick: () => {
            console.info(`Clicked card`);
          }
        })
      }
    }
  }
}
```
