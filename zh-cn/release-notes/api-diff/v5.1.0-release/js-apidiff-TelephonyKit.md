| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|删除API|类名：data；<br>API声明：function queryAllApns(): Promise\<Array\<ApnInfo>>;<br>差异内容：function queryAllApns(): Promise\<Array\<ApnInfo>>;|NA|api/@ohos.telephony.data.d.ts|
|删除API|类名：data；<br>API声明：function getActiveApnName(): Promise\<string>;<br>差异内容：function getActiveApnName(): Promise\<string>;|NA|api/@ohos.telephony.data.d.ts|
|删除API|类名：data；<br>API声明：function queryApnIds(apnInfo: ApnInfo): Promise\<Array\<number>>;<br>差异内容：function queryApnIds(apnInfo: ApnInfo): Promise\<Array\<number>>;|NA|api/@ohos.telephony.data.d.ts|
|删除API|类名：data；<br>API声明：function setPreferredApn(apnId: number): Promise\<boolean>;<br>差异内容：function setPreferredApn(apnId: number): Promise\<boolean>;|NA|api/@ohos.telephony.data.d.ts|
|删除API|类名：data；<br>API声明：interface ApnInfo<br>差异内容：interface ApnInfo|NA|api/@ohos.telephony.data.d.ts|
|删除API|类名：ApnInfo；<br>API声明：apnName: string;<br>差异内容：apnName: string;|NA|api/@ohos.telephony.data.d.ts|
|删除API|类名：ApnInfo；<br>API声明：apn: string;<br>差异内容：apn: string;|NA|api/@ohos.telephony.data.d.ts|
|删除API|类名：ApnInfo；<br>API声明：mcc: string;<br>差异内容：mcc: string;|NA|api/@ohos.telephony.data.d.ts|
|删除API|类名：ApnInfo；<br>API声明：mnc: string;<br>差异内容：mnc: string;|NA|api/@ohos.telephony.data.d.ts|
|删除API|类名：ApnInfo；<br>API声明：user?: string;<br>差异内容：user?: string;|NA|api/@ohos.telephony.data.d.ts|
|删除API|类名：ApnInfo；<br>API声明：type?: string;<br>差异内容：type?: string;|NA|api/@ohos.telephony.data.d.ts|
|删除API|类名：ApnInfo；<br>API声明：proxy?: string;<br>差异内容：proxy?: string;|NA|api/@ohos.telephony.data.d.ts|
|删除API|类名：ApnInfo；<br>API声明：mmsproxy?: string;<br>差异内容：mmsproxy?: string;|NA|api/@ohos.telephony.data.d.ts|
|删除API|类名：eSIM；<br>API声明：export interface AccessRule<br>差异内容：export interface AccessRule|NA|api/@ohos.telephony.esim.d.ts|
|删除API|类名：AccessRule；<br>API声明：certificateHashHexStr: string;<br>差异内容：certificateHashHexStr: string;|NA|api/@ohos.telephony.esim.d.ts|
|删除API|类名：AccessRule；<br>API声明：packageName: string;<br>差异内容：packageName: string;|NA|api/@ohos.telephony.esim.d.ts|
|删除API|类名：AccessRule；<br>API声明：accessType: number;<br>差异内容：accessType: number;|NA|api/@ohos.telephony.esim.d.ts|
|删除API|类名：eSIM；<br>API声明：export interface DownloadableProfile<br>差异内容：export interface DownloadableProfile|NA|api/@ohos.telephony.esim.d.ts|
|删除API|类名：DownloadableProfile；<br>API声明：activationCode: string;<br>差异内容：activationCode: string;|NA|api/@ohos.telephony.esim.d.ts|
|删除API|类名：DownloadableProfile；<br>API声明：confirmationCode?: string;<br>差异内容：confirmationCode?: string;|NA|api/@ohos.telephony.esim.d.ts|
|删除API|类名：DownloadableProfile；<br>API声明：carrierName?: string;<br>差异内容：carrierName?: string;|NA|api/@ohos.telephony.esim.d.ts|
|删除API|类名：DownloadableProfile；<br>API声明：accessRules?: Array\<AccessRule>;<br>差异内容：accessRules?: Array\<AccessRule>;|NA|api/@ohos.telephony.esim.d.ts|
|删除API|类名：radio；<br>API声明：function getRadioTechSync(slotId: number): NetworkRadioTech;<br>差异内容：function getRadioTechSync(slotId: number): NetworkRadioTech;|NA|api/@ohos.telephony.radio.d.ts|
|删除API|类名：sim；<br>API声明：function getSimLabel(slotId: number, callback: AsyncCallback\<SimLabel>): void;<br>差异内容：function getSimLabel(slotId: number, callback: AsyncCallback\<SimLabel>): void;|NA|api/@ohos.telephony.sim.d.ts|
|删除API|类名：sim；<br>API声明：function getSimLabel(slotId: number): Promise\<SimLabel>;<br>差异内容：function getSimLabel(slotId: number): Promise\<SimLabel>;|NA|api/@ohos.telephony.sim.d.ts|
|删除API|类名：sim；<br>API声明：function getSimLabelSync(slotId: number): SimLabel;<br>差异内容：function getSimLabelSync(slotId: number): SimLabel;|NA|api/@ohos.telephony.sim.d.ts|
|删除API|类名：sim；<br>API声明：export enum SimType<br>差异内容：export enum SimType|NA|api/@ohos.telephony.sim.d.ts|
|删除API|类名：SimType；<br>API声明：PSIM = 0<br>差异内容：PSIM = 0|NA|api/@ohos.telephony.sim.d.ts|
|删除API|类名：SimType；<br>API声明：ESIM = 1<br>差异内容：ESIM = 1|NA|api/@ohos.telephony.sim.d.ts|
|删除API|类名：sim；<br>API声明：export interface SimLabel<br>差异内容：export interface SimLabel|NA|api/@ohos.telephony.sim.d.ts|
|删除API|类名：SimLabel；<br>API声明：simType: SimType;<br>差异内容：simType: SimType;|NA|api/@ohos.telephony.sim.d.ts|
|删除API|类名：SimLabel；<br>API声明：index: number;<br>差异内容：index: number;|NA|api/@ohos.telephony.sim.d.ts|
|起始版本有变化|类名：global；<br>API声明：declare namespace eSIM<br>差异内容：18|类名：global；<br>API声明：declare namespace eSIM<br>差异内容：14|api/@ohos.telephony.esim.d.ts|
|起始版本有变化|类名：eSIM；<br>API声明：function isSupported(slotId: number): boolean;<br>差异内容：18|类名：eSIM；<br>API声明：function isSupported(slotId: number): boolean;<br>差异内容：14|api/@ohos.telephony.esim.d.ts|
|起始版本有变化|类名：eSIM；<br>API声明：function addProfile(profile: DownloadableProfile): Promise\<boolean>;<br>差异内容：18|类名：eSIM；<br>API声明：function addProfile(profile: DownloadableProfile): Promise\<boolean>;<br>差异内容：14|api/@ohos.telephony.esim.d.ts|
