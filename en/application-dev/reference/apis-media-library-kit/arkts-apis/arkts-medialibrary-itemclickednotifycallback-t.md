# ItemClickedNotifyCallback

```TypeScript
export type ItemClickedNotifyCallback = (itemInfo: ItemInfo, clickType: ClickType) => void
```

Callback to be invoked when an item in a **PhotoPickerComponent** is clicked.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| itemInfo | [ItemInfo](arkts-medialibrary-file-photopickercomponent-iteminfo-c.md) | Yes | Type of the clicked item, which can be a thumbnail item or a camera item. |
| clickType | [ClickType](arkts-medialibrary-file-photopickercomponent-clicktype-e.md) | Yes | Enumerates the click operation types. |

**Examples**

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

const DOMAIN = 0x0000;
const TAG: string = 'clickedNotifyDemo';

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
    // When an item is clicked, the code checks whether the corresponding URI is valid. An invalid URI is ignored.
    // Then, the code checks whether the URI already exists in clickedUris. If not, it creates a record and sets the isSelected property to true.
    // If yes, the code updates the isSelected property of the record to true.
    // After the data is saved, clicking the setClickResult button will call addData(SET_ITEM_CLICK_RESULT) to set the corresponding item to the selected state.
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
        // Obtain parameters from the index.ets page.
        this.isOnClickedNotify = params.isOnClickedNotify;
        this.pickerOptions.maxPhotoSelectNumber = 500;
    }

    // Obtain the URIs from this.clickedUris, which will be used when pickerController.addData() is called to set the item to be selected.
    getClickedUris(): ClickResult[] {
        let uris: ClickResultEx[] = [];
        this.clickedUris.forEach((uri, index) => {
            uris.push(uri)
        })
        return uris;
    }

    build() {
        Column() {
            Row() {
                // Call the photo picker component.
                PhotoPickerComponent({
                    pickerOptions: this.pickerOptions,
                    pickerController: this.pickerController,
                    onItemClicked: this.isOnClicked ? this.onClicked : undefined,
                    onItemClickedNotify: this.isOnClickedNotify ? this.onClickedNotify : undefined,
                    onSelect: (uri: string) => {},
                    onDeselect: (uri: string) => {}
                })
            }.height('50%')

            Row() {
                Column() {
                    Text('Selected assets')
                    ForEach(this.getClickedUris(), (uri: ClickResult) => {
                        Row() {
                            // You can remove or add a selection.
                            Checkbox({ name: "OnClick" })
                                .select(uri.isSelected)
                                .onChange((checked: boolean) => {
                                    let clickResult = this.clickedUris.get(uri.uri);
                                    if (!clickResult) {
                                        clickResult = {
                                            uri: uri.uri,
                                            isSelected: checked
                                        };
                                    } else {
                                        clickResult.isSelected = checked;
                                    }
                                    if (uri.uri !== 'abnormal') {
                                        this.clickedUris.set(uri.uri, clickResult);
                                    }
                                }).margin({ right: 5 })
                            Text(uri.uri.slice(-30)).margin({right: 5}).width(150)
                            // Remove the selected item from this.clickeduris.
                            Button('Delete').onClick(() => {
                                this.clickedUris.delete(uri.uri);
                            })
                            // The following code is an example of an exception scenario. When an abnormal URI is passed, the item selected by Picker does not take effect.
                            Button('Abnormal').onClick(() => {
                                let clickResult = this.clickedUris.get(uri.uri);
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
                // Send URI (SET_ITEM_CLICK_RESULT).
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
