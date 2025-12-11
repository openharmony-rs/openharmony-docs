| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: eSIM;<br>API declaration: export interface DownloadableProfile<br>DIfferences: export interface DownloadableProfile|api/@ohos.telephony.esim.d.ts|
|New API |NA|Class name: DownloadableProfile;<br>API declaration: activationCode: string;<br>DIfferences: activationCode: string;|api/@ohos.telephony.esim.d.ts|
|New API |NA|Class name: DownloadableProfile;<br>API declaration: confirmationCode?: string;<br>DIfferences: confirmationCode?: string;|api/@ohos.telephony.esim.d.ts|
|New API |NA|Class name: DownloadableProfile;<br>API declaration: carrierName?: string;<br>DIfferences: carrierName?: string;|api/@ohos.telephony.esim.d.ts|
|New API |NA|Class name: DownloadableProfile;<br>API declaration: accessRules?: Array\<AccessRule>;<br>DIfferences: accessRules?: Array\<AccessRule>;|api/@ohos.telephony.esim.d.ts|
|New API |NA|Class name: data;<br>API declaration: function queryAllApns(): Promise\<Array\<ApnInfo>>;<br>DIfferences: function queryAllApns(): Promise\<Array\<ApnInfo>>;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: function queryApnIds(apnInfo: ApnInfo): Promise\<Array\<number>>;<br>DIfferences: function queryApnIds(apnInfo: ApnInfo): Promise\<Array\<number>>;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: function setPreferredApn(apnId: number): Promise\<boolean>;<br>DIfferences: function setPreferredApn(apnId: number): Promise\<boolean>;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: interface ApnInfo<br>DIfferences: interface ApnInfo|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: ApnInfo;<br>API declaration: apnName: string;<br>DIfferences: apnName: string;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: ApnInfo;<br>API declaration: apn: string;<br>DIfferences: apn: string;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: ApnInfo;<br>API declaration: mcc: string;<br>DIfferences: mcc: string;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: ApnInfo;<br>API declaration: mnc: string;<br>DIfferences: mnc: string;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: ApnInfo;<br>API declaration: user?: string;<br>DIfferences: user?: string;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: ApnInfo;<br>API declaration: type?: string;<br>DIfferences: type?: string;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: ApnInfo;<br>API declaration: proxy?: string;<br>DIfferences: proxy?: string;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: ApnInfo;<br>API declaration: mmsproxy?: string;<br>DIfferences: mmsproxy?: string;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: radio;<br>API declaration: function getRadioTechSync(slotId: number): NetworkRadioTech;<br>DIfferences: function getRadioTechSync(slotId: number): NetworkRadioTech;|api/@ohos.telephony.radio.d.ts|
|Initial version change|Class name: global;<br>API declaration: declare namespace eSIM<br>DIfferences: 14|Class name: global;<br>API declaration: declare namespace eSIM<br>DIfferences: 18|api/@ohos.telephony.esim.d.ts|
|Initial version change|Class name: eSIM;<br>API declaration: function isSupported(slotId: number): boolean;<br>DIfferences: 14|Class name: eSIM;<br>API declaration: function isSupported(slotId: number): boolean;<br>DIfferences: 18|api/@ohos.telephony.esim.d.ts|
|Initial version change|Class name: eSIM;<br>API declaration: function addProfile(profile: DownloadableProfile): Promise\<boolean>;<br>DIfferences: 14|Class name: eSIM;<br>API declaration: function addProfile(profile: DownloadableProfile): Promise\<boolean>;<br>DIfferences: 18|api/@ohos.telephony.esim.d.ts|
