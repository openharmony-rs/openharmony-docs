| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: eSIM;<br>API declaration: export interface AccessRule<br>DIfferences: export interface AccessRule|api/@ohos.telephony.esim.d.ts|
|New API |NA|Class name: AccessRule;<br>API declaration: certificateHashHexStr: string;<br>DIfferences: certificateHashHexStr: string;|api/@ohos.telephony.esim.d.ts|
|New API |NA|Class name: AccessRule;<br>API declaration: packageName: string;<br>DIfferences: packageName: string;|api/@ohos.telephony.esim.d.ts|
|New API |NA|Class name: AccessRule;<br>API declaration: accessType: number;<br>DIfferences: accessType: number;|api/@ohos.telephony.esim.d.ts|
|New API |NA|Class name: eSIM;<br>API declaration: export interface DownloadableProfile<br>DIfferences: export interface DownloadableProfile|api/@ohos.telephony.esim.d.ts|
|New API |NA|Class name: DownloadableProfile;<br>API declaration: activationCode: string;<br>DIfferences: activationCode: string;|api/@ohos.telephony.esim.d.ts|
|New API |NA|Class name: DownloadableProfile;<br>API declaration: confirmationCode?: string;<br>DIfferences: confirmationCode?: string;|api/@ohos.telephony.esim.d.ts|
|New API |NA|Class name: DownloadableProfile;<br>API declaration: carrierName?: string;<br>DIfferences: carrierName?: string;|api/@ohos.telephony.esim.d.ts|
|New API |NA|Class name: DownloadableProfile;<br>API declaration: accessRules?: Array\<AccessRule>;<br>DIfferences: accessRules?: Array\<AccessRule>;|api/@ohos.telephony.esim.d.ts|
|New API |NA|Class name: data;<br>API declaration: function queryAllApns(): Promise\<Array\<ApnInfo>>;<br>DIfferences: function queryAllApns(): Promise\<Array\<ApnInfo>>;|api/@ohos.telephony.data.d.ts|
|New API |NA|Class name: data;<br>API declaration: function getActiveApnName(): Promise\<string>;<br>DIfferences: function getActiveApnName(): Promise\<string>;|api/@ohos.telephony.data.d.ts|
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
|New API |NA|Class name: sim;<br>API declaration: function getSimLabel(slotId: number, callback: AsyncCallback\<SimLabel>): void;<br>DIfferences: function getSimLabel(slotId: number, callback: AsyncCallback\<SimLabel>): void;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getSimLabel(slotId: number): Promise\<SimLabel>;<br>DIfferences: function getSimLabel(slotId: number): Promise\<SimLabel>;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: function getSimLabelSync(slotId: number): SimLabel;<br>DIfferences: function getSimLabelSync(slotId: number): SimLabel;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: export enum SimType<br>DIfferences: export enum SimType|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: SimType;<br>API declaration: PSIM = 0<br>DIfferences: PSIM = 0|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: SimType;<br>API declaration: ESIM = 1<br>DIfferences: ESIM = 1|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: sim;<br>API declaration: export interface SimLabel<br>DIfferences: export interface SimLabel|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: SimLabel;<br>API declaration: simType: SimType;<br>DIfferences: simType: SimType;|api/@ohos.telephony.sim.d.ts|
|New API |NA|Class name: SimLabel;<br>API declaration: index: number;<br>DIfferences: index: number;|api/@ohos.telephony.sim.d.ts|
|Initial version change|Class name: global;<br>API declaration: declare namespace eSIM<br>DIfferences: 14|Class name: global;<br>API declaration: declare namespace eSIM<br>DIfferences: 18|api/@ohos.telephony.esim.d.ts|
|Initial version change|Class name: eSIM;<br>API declaration: function isSupported(slotId: number): boolean;<br>DIfferences: 14|Class name: eSIM;<br>API declaration: function isSupported(slotId: number): boolean;<br>DIfferences: 18|api/@ohos.telephony.esim.d.ts|
|Initial version change|Class name: eSIM;<br>API declaration: function addProfile(profile: DownloadableProfile): Promise\<boolean>;<br>DIfferences: 14|Class name: eSIM;<br>API declaration: function addProfile(profile: DownloadableProfile): Promise\<boolean>;<br>DIfferences: 18|api/@ohos.telephony.esim.d.ts|
