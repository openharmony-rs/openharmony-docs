# ItemClickedNotifyCallback

```TypeScript
export type ItemClickedNotifyCallback = (itemInfo: ItemInfo, clickType: ClickType) => void
```

用户在图片选择器组件中点击宫格产生的回调事件。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-export type ItemClickedNotifyCallback = (itemInfo: ItemInfo, clickType: ClickType) => void--><!--Device-unnamed-export type ItemClickedNotifyCallback = (itemInfo: ItemInfo, clickType: ClickType) => void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemInfo | [ItemInfo](arkts-medialibrary-file-photopickercomponent-iteminfo-c.md) | 是 | 被点击的宫格类型。包括缩略图宫格和相机宫格。 |
| clickType | [ClickType](arkts-medialibrary-file-photopickercomponent-clicktype-e.md) | 是 | 点击操作的类型。 |

**示例**

```TypeScript
import {
  ClickType,
  DataType,
  ItemInfo,
  PhotoPickerComponent,
  PickerController,
  PickerOptions,
} from '@kit.MediaLibraryKit';
import { ClickResult, ItemClickedNotifyCallback } from '@ohos.file.PhotoPickerComponent';

interface Checks {
  isOnClicked: boolean;
  isOnClickedNotify: boolean;
}

export interface ClickResultEx {
  uri: string,
  isSelected: boolean,
}

@Entry
@Component
struct PickerPage {
  @State pickerController: PickerController = new PickerController();
  private pickerOptions: PickerOptions = new PickerOptions();
  @State currentUri: string = '';
  @State currentState: number = 0;
  @State clickedUris: Map<string, ClickResultEx> = new Map();
  private isOnClicked: boolean = false;
  private isOnClickedNotify: boolean = false;
  onClicked: (itemInfo: ItemInfo, clickType: ClickType) => boolean = (itemInfo: ItemInfo, clickType: ClickType) => {
    return true;
  };
  // 当一个宫格被点击时，代码会验证该宫格对应URI是否有效，如无效，则忽略。
  // 然后，会检查clickedUris中是否已存在该URI的记录。如没有，则创建一条记录并将isSelected属性设置为true。
  // 如果记录存在，则将该记录的isSelected属性更新为true。
  // 数据保存完成后点击“setClickResult”按钮，会调用addData(SET_ITEM_CLICK_RESULT)将对应宫格设置为选中状态。
  onClickedNotify: ItemClickedNotifyCallback = (itemInfo: ItemInfo, clickType: ClickType) => {
    if (!itemInfo.uri) {
      return;
    }

    let clickResult = this.clickedUris.get(itemInfo.uri);
    if (!clickResult) {
      clickResult = {
        uri: itemInfo.uri,
        isSelected: true,
      };
    } else {
      clickResult.isSelected = true;
    }
    this.clickedUris.set(itemInfo.uri, clickResult);
  };

  aboutToAppear(): void {
    let params = this.getUIContext().getRouter().getParams() as Checks;

    this.pickerOptions.isSlidingSelectionSupported = true;
    this.pickerOptions.isSearchSupported = false;
    this.isOnClicked = params.isOnClicked;
    // 从index.ets页面获取参数。
    this.isOnClickedNotify = params.isOnClickedNotify;
    this.pickerOptions.maxPhotoSelectNumber = 500;
  }

  // 从this.clickedUris获取这些URI，后续在调用pickerController.addData()设置宫格item选中时使用。
  getClickedUris(): ClickResultEx[] {
    let clickResultEx: ClickResultEx[] = [];
    this.clickedUris.forEach((clickResult: ClickResultEx, uri: string) => {
      clickResultEx.push(clickResult)
    })
    return clickResultEx;
  }

  build() {
    Column() {
      Row() {
        // 照片选择器组件调用。
        PhotoPickerComponent({
          pickerOptions: this.pickerOptions,
          pickerController: this.pickerController,
          onItemClicked: this.isOnClicked ? this.onClicked : undefined,
          onItemClickedNotify: this.isOnClickedNotify ? this.onClickedNotify : undefined,
          onSelect: (uri: string) => {
          },
          onDeselect: (uri: string) => {
          }
        })
      }.height('50%')

      Row() {
        Column() {
          Text('Selected assets')
          ForEach(this.getClickedUris(), (res: ClickResultEx) => {
            Row() {
              // 能够移除选择或添加选择。
              Checkbox({ name: 'OnClick' })
                .select(res.isSelected)
                .onChange((checked: boolean) => {
                  let clickResult = this.clickedUris.get(res.uri);
                  if (!clickResult) {
                    clickResult = {
                      uri: res.uri,
                      isSelected: checked
                    };
                  } else {
                    clickResult.isSelected = checked;
                  }
                  if (res.uri !== 'abnormal') {
                    this.clickedUris.set(res.uri, clickResult);
                  }
                }).margin({ right: 5 })
              Text(res.uri.slice(-30)).margin({ right: 5 }).width(150)
              // 从this.clickeduris中移除选择项。
              Button('Delete').onClick(() => {
                this.clickedUris.delete(res.uri);
              })
              // 此处代码为异常场景样例，当传入异常URI时，picker宫格选中不生效。
              Button('Abnormal').onClick(() => {
                let clickResult = this.clickedUris.get(res.uri);
                if (clickResult) {
                  let oldClickUri = clickResult.uri;
                  clickResult.uri = 'abnormal'
                  this.clickedUris.set(oldClickUri, clickResult)
                }
              })
            }.width('100%')
          })
        }
      }.height('20%')

      Row() {
        // 发送URI(SET_ITEM_CLICK_RESULT)。
        Button('Set ClickResult')
          .onClick(() => {
            this.pickerController.addData(DataType.SET_ITEM_CLICK_RESULT, this.getClickedUris())
          })
      }.height('10%')
    }
    .height('100%')
    .width('100%')
  }
}
```
