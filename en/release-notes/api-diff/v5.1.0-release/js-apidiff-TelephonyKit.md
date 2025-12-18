| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
| Deleted API|Class name: data;<br>API declaration: function queryAllApns(): Promise\<Array\<ApnInfo>>;<br>DIfferences: function queryAllApns(): Promise\<Array\<ApnInfo>>;|NA|api/@ohos.telephony.data.d.ts|
| Deleted API|Class name: data;<br>API declaration: function getActiveApnName(): Promise\<string>;<br>DIfferences: function getActiveApnName(): Promise\<string>;|NA|api/@ohos.telephony.data.d.ts|
| Deleted API|Class name: data;<br>API declaration: function queryApnIds(apnInfo: ApnInfo): Promise\<Array\<number>>;<br>DIfferences: function queryApnIds(apnInfo: ApnInfo): Promise\<Array\<number>>;|NA|api/@ohos.telephony.data.d.ts|
| Deleted API|Class name: data;<br>API declaration: function setPreferredApn(apnId: number): Promise\<boolean>;<br>DIfferences: function setPreferredApn(apnId: number): Promise\<boolean>;|NA|api/@ohos.telephony.data.d.ts|
| Deleted API|Class name: data;<br>API declaration: interface ApnInfo<br>DIfferences: interface ApnInfo|NA|api/@ohos.telephony.data.d.ts|
| Deleted API|Class name: ApnInfo;<br>API declaration: apnName: string;<br>DIfferences: apnName: string;|NA|api/@ohos.telephony.data.d.ts|
| Deleted API|Class name: ApnInfo;<br>API declaration: apn: string;<br>DIfferences: apn: string;|NA|api/@ohos.telephony.data.d.ts|
| Deleted API|Class name: ApnInfo;<br>API declaration: mcc: string;<br>DIfferences: mcc: string;|NA|api/@ohos.telephony.data.d.ts|
| Deleted API|Class name: ApnInfo;<br>API declaration: mnc: string;<br>DIfferences: mnc: string;|NA|api/@ohos.telephony.data.d.ts|
| Deleted API|Class name: ApnInfo;<br>API declaration: user?: string;<br>DIfferences: user?: string;|NA|api/@ohos.telephony.data.d.ts|
| Deleted API|Class name: ApnInfo;<br>API declaration: type?: string;<br>DIfferences: type?: string;|NA|api/@ohos.telephony.data.d.ts|
| Deleted API|Class name: ApnInfo;<br>API declaration: proxy?: string;<br>DIfferences: proxy?: string;|NA|api/@ohos.telephony.data.d.ts|
| Deleted API|Class name: ApnInfo;<br>API declaration: mmsproxy?: string;<br>DIfferences: mmsproxy?: string;|NA|api/@ohos.telephony.data.d.ts|
| Deleted API|Class name: eSIM;<br>API declaration: export interface AccessRule<br>DIfferences: export interface AccessRule|NA|api/@ohos.telephony.esim.d.ts|
| Deleted API|Class name: AccessRule;<br>API declaration: certificateHashHexStr: string;<br>DIfferences: certificateHashHexStr: string;|NA|api/@ohos.telephony.esim.d.ts|
| Deleted API|Class name: AccessRule;<br>API declaration: packageName: string;<br>DIfferences: packageName: string;|NA|api/@ohos.telephony.esim.d.ts|
| Deleted API|Class name: AccessRule;<br>API declaration: accessType: number;<br>DIfferences: accessType: number;|NA|api/@ohos.telephony.esim.d.ts|
| Deleted API|Class name: eSIM;<br>API declaration: export interface DownloadableProfile<br>DIfferences: export interface DownloadableProfile|NA|api/@ohos.telephony.esim.d.ts|
| Deleted API|Class name: DownloadableProfile;<br>API declaration: activationCode: string;<br>DIfferences: activationCode: string;|NA|api/@ohos.telephony.esim.d.ts|
| Deleted API|Class name: DownloadableProfile;<br>API declaration: confirmationCode?: string;<br>DIfferences: confirmationCode?: string;|NA|api/@ohos.telephony.esim.d.ts|
| Deleted API|Class name: DownloadableProfile;<br>API declaration: carrierName?: string;<br>DIfferences: carrierName?: string;|NA|api/@ohos.telephony.esim.d.ts|
| Deleted API|Class name: DownloadableProfile;<br>API declaration: accessRules?: Array\<AccessRule>;<br>DIfferences: accessRules?: Array\<AccessRule>;|NA|api/@ohos.telephony.esim.d.ts|
| Deleted API|Class name: radio;<br>API declaration: function getRadioTechSync(slotId: number): NetworkRadioTech;<br>DIfferences: function getRadioTechSync(slotId: number): NetworkRadioTech;|NA|api/@ohos.telephony.radio.d.ts|
| Deleted API|Class name: sim;<br>API declaration: function getSimLabel(slotId: number, callback: AsyncCallback\<SimLabel>): void;<br>DIfferences: function getSimLabel(slotId: number, callback: AsyncCallback\<SimLabel>): void;|NA|api/@ohos.telephony.sim.d.ts|
| Deleted API|Class name: sim;<br>API declaration: function getSimLabel(slotId: number): Promise\<SimLabel>;<br>DIfferences: function getSimLabel(slotId: number): Promise\<SimLabel>;|NA|api/@ohos.telephony.sim.d.ts|
| Deleted API|Class name: sim;<br>API declaration: function getSimLabelSync(slotId: number): SimLabel;<br>DIfferences: function getSimLabelSync(slotId: number): SimLabel;|NA|api/@ohos.telephony.sim.d.ts|
| Deleted API|Class name: sim;<br>API declaration: export enum SimType<br>DIfferences: export enum SimType|NA|api/@ohos.telephony.sim.d.ts|
| Deleted API|Class name: SimType;<br>API declaration: PSIM = 0<br>DIfferences: PSIM = 0|NA|api/@ohos.telephony.sim.d.ts|
| Deleted API|Class name: SimType;<br>API declaration: ESIM = 1<br>DIfferences: ESIM = 1|NA|api/@ohos.telephony.sim.d.ts|
| Deleted API|Class name: sim;<br>API declaration: export interface SimLabel<br>DIfferences: export interface SimLabel|NA|api/@ohos.telephony.sim.d.ts|
| Deleted API|Class name: SimLabel;<br>API declaration: simType: SimType;<br>DIfferences: simType: SimType;|NA|api/@ohos.telephony.sim.d.ts|
| Deleted API|Class name: SimLabel;<br>API declaration: index: number;<br>DIfferences: index: number;|NA|api/@ohos.telephony.sim.d.ts|
|Initial version change|Class name: global;<br>API declaration: declare namespace eSIM<br>DIfferences: 18|Class name: global;<br>API declaration: declare namespace eSIM<br>DIfferences: 14|api/@ohos.telephony.esim.d.ts|
|Initial version change|Class name: eSIM;<br>API declaration: function isSupported(slotId: number): boolean;<br>DIfferences: 18|Class name: eSIM;<br>API declaration: function isSupported(slotId: number): boolean;<br>DIfferences: 14|api/@ohos.telephony.esim.d.ts|
|Initial version change|Class name: eSIM;<br>API declaration: function addProfile(profile: DownloadableProfile): Promise\<boolean>;<br>DIfferences: 18|Class name: eSIM;<br>API declaration: function addProfile(profile: DownloadableProfile): Promise\<boolean>;<br>DIfferences: 14|api/@ohos.telephony.esim.d.ts|
