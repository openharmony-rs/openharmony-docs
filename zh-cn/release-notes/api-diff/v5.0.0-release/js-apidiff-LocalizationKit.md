| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：global；<br>API声明：export interface RawFileDescriptor<br>差异内容：NA|类名：global；<br>API声明：export interface RawFileDescriptor<br>差异内容：crossplatform|api/global/rawFileDescriptor.d.ts|
|API跨平台权限变更|类名：RawFileDescriptor；<br>API声明：fd: number;<br>差异内容：NA|类名：RawFileDescriptor；<br>API声明：fd: number;<br>差异内容：crossplatform|api/global/rawFileDescriptor.d.ts|
|API跨平台权限变更|类名：RawFileDescriptor；<br>API声明：offset: number;<br>差异内容：NA|类名：RawFileDescriptor；<br>API声明：offset: number;<br>差异内容：crossplatform|api/global/rawFileDescriptor.d.ts|
|API跨平台权限变更|类名：RawFileDescriptor；<br>API声明：length: number;<br>差异内容：NA|类名：RawFileDescriptor；<br>API声明：length: number;<br>差异内容：crossplatform|api/global/rawFileDescriptor.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare namespace i18n<br>差异内容：NA|类名：global；<br>API声明：declare namespace i18n<br>差异内容：crossplatform|api/@ohos.i18n.d.ts|
|API跨平台权限变更|类名：ResourceManager；<br>API声明：getDrawableDescriptor(resId: number, density?: number, type?: number): DrawableDescriptor;<br>差异内容：NA|类名：ResourceManager；<br>API声明：getDrawableDescriptor(resId: number, density?: number, type?: number): DrawableDescriptor;<br>差异内容：crossplatform|api/@ohos.resourceManager.d.ts|
|API跨平台权限变更|类名：ResourceManager；<br>API声明：getDrawableDescriptor(resource: Resource, density?: number, type?: number): DrawableDescriptor;<br>差异内容：NA|类名：ResourceManager；<br>API声明：getDrawableDescriptor(resource: Resource, density?: number, type?: number): DrawableDescriptor;<br>差异内容：crossplatform|api/@ohos.resourceManager.d.ts|
|API跨平台权限变更|类名：ResourceManager；<br>API声明：getDrawableDescriptorByName(resName: string, density?: number, type?: number): DrawableDescriptor;<br>差异内容：NA|类名：ResourceManager；<br>API声明：getDrawableDescriptorByName(resName: string, density?: number, type?: number): DrawableDescriptor;<br>差异内容：crossplatform|api/@ohos.resourceManager.d.ts|
|API废弃版本变更|类名：ResourceManager；<br>API声明：release();<br>差异内容：NA|类名：ResourceManager；<br>API声明：release();<br>差异内容：12|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace sendableResourceManager<br>差异内容：declare namespace sendableResourceManager|api/@ohos.sendableResourceManager.d.ets|
|新增API|NA|类名：sendableResourceManager；<br>API声明：export function resourceToSendableResource(resource: Resource): SendableResource;<br>差异内容：export function resourceToSendableResource(resource: Resource): SendableResource;|api/@ohos.sendableResourceManager.d.ets|
|新增API|NA|类名：sendableResourceManager；<br>API声明：export function sendableResourceToResource(resource: SendableResource): Resource;<br>差异内容：export function sendableResourceToResource(resource: SendableResource): Resource;|api/@ohos.sendableResourceManager.d.ets|
|新增API|NA|类名：sendableResourceManager；<br>API声明：export type Resource = _Resource;<br>差异内容：export type Resource = _Resource;|api/@ohos.sendableResourceManager.d.ets|
|新增API|NA|类名：sendableResourceManager；<br>API声明：export type SendableResource = _SendableResource;<br>差异内容：export type SendableResource = _SendableResource;|api/@ohos.sendableResourceManager.d.ets|
|新增API|NA|类名：global；<br>API声明：interface SendableResource<br>差异内容：interface SendableResource|api/global/sendableResource.d.ets|
|新增API|NA|类名：SendableResource；<br>API声明：bundleName: string;<br>差异内容：bundleName: string;|api/global/sendableResource.d.ets|
|新增API|NA|类名：SendableResource；<br>API声明：moduleName: string;<br>差异内容：moduleName: string;|api/global/sendableResource.d.ets|
|新增API|NA|类名：SendableResource；<br>API声明：id: number;<br>差异内容：id: number;|api/global/sendableResource.d.ets|
|新增API|NA|类名：SendableResource；<br>API声明：params?: collections.Array\<string \| number>;<br>差异内容：params?: collections.Array\<string \| number>;|api/global/sendableResource.d.ets|
|新增API|NA|类名：SendableResource；<br>API声明：type?: number;<br>差异内容：type?: number;|api/global/sendableResource.d.ets|
|新增API|NA|类名：I18NUtil；<br>API声明：static getBestMatchLocale(locale: string, localeList: string[]): string;<br>差异内容：static getBestMatchLocale(locale: string, localeList: string[]): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：I18NUtil；<br>API声明：static getThreeLetterLanguage(locale: string): string;<br>差异内容：static getThreeLetterLanguage(locale: string): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：I18NUtil；<br>API声明：static getThreeLetterRegion(locale: string): string;<br>差异内容：static getThreeLetterRegion(locale: string): string;|api/@ohos.i18n.d.ts|
|新增API|NA|类名：resourceManager；<br>API声明：export enum ColorMode<br>差异内容：export enum ColorMode|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：DARK = 0<br>差异内容：DARK = 0|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ColorMode；<br>API声明：LIGHT = 1<br>差异内容：LIGHT = 1|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：deviceType: DeviceType;<br>差异内容：deviceType: DeviceType;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：screenDensity: ScreenDensity;<br>差异内容：screenDensity: ScreenDensity;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：colorMode: ColorMode;<br>差异内容：colorMode: ColorMode;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：mcc: number;<br>差异内容：mcc: number;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：Configuration；<br>API声明：mnc: number;<br>差异内容：mnc: number;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：isRawDir(path: string): boolean;<br>差异内容：isRawDir(path: string): boolean;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getOverrideResourceManager(configuration?: Configuration): ResourceManager;<br>差异内容：getOverrideResourceManager(configuration?: Configuration): ResourceManager;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：getOverrideConfiguration(): Configuration;<br>差异内容：getOverrideConfiguration(): Configuration;|api/@ohos.resourceManager.d.ts|
|新增API|NA|类名：ResourceManager；<br>API声明：updateOverrideConfiguration(configuration: Configuration): void;<br>差异内容：updateOverrideConfiguration(configuration: Configuration): void;|api/@ohos.resourceManager.d.ts|
|新增kit|类名：global；<br>API声明：api\global\rawFileDescriptor.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\global\rawFileDescriptor.d.ts<br>差异内容：LocalizationKit|api/global/rawFileDescriptor.d.ts|
|新增kit|类名：global；<br>API声明：api\global\resource.d.ts<br>差异内容：NA|类名：global；<br>API声明：api\global\resource.d.ts<br>差异内容：LocalizationKit|api/global/resource.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.sendableResourceManager.d.ets<br>差异内容：LocalizationKit|api/@ohos.sendableResourceManager.d.ets|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\global\sendableResource.d.ets<br>差异内容：LocalizationKit|api/global/sendableResource.d.ets|
|API从支持元服务到不支持元服务|类名：resourceManager；<br>API声明：export function getResourceManager(callback: AsyncCallback\<ResourceManager>): void;<br>差异内容：atomicservice|类名：resourceManager；<br>API声明：export function getResourceManager(callback: AsyncCallback\<ResourceManager>): void;<br>差异内容：NA|api/@ohos.resourceManager.d.ts|
|API从支持元服务到不支持元服务|类名：resourceManager；<br>API声明：export function getResourceManager(bundleName: string, callback: AsyncCallback\<ResourceManager>): void;<br>差异内容：atomicservice|类名：resourceManager；<br>API声明：export function getResourceManager(bundleName: string, callback: AsyncCallback\<ResourceManager>): void;<br>差异内容：NA|api/@ohos.resourceManager.d.ts|
|API从支持元服务到不支持元服务|类名：resourceManager；<br>API声明：export function getResourceManager(): Promise\<ResourceManager>;<br>差异内容：atomicservice|类名：resourceManager；<br>API声明：export function getResourceManager(): Promise\<ResourceManager>;<br>差异内容：NA|api/@ohos.resourceManager.d.ts|
|API从支持元服务到不支持元服务|类名：resourceManager；<br>API声明：export function getResourceManager(bundleName: string): Promise\<ResourceManager>;<br>差异内容：atomicservice|类名：resourceManager；<br>API声明：export function getResourceManager(bundleName: string): Promise\<ResourceManager>;<br>差异内容：NA|api/@ohos.resourceManager.d.ts|
|API从不支持元服务到支持元服务|类名：System；<br>API声明：static getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string;<br>差异内容：NA|类名：System；<br>API声明：static getDisplayCountry(country: string, locale: string, sentenceCase?: boolean): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：System；<br>API声明：static getSystemLanguages(): Array\<string>;<br>差异内容：NA|类名：System；<br>API声明：static getSystemLanguages(): Array\<string>;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：System；<br>API声明：static getSystemCountries(language: string): Array\<string>;<br>差异内容：NA|类名：System；<br>API声明：static getSystemCountries(language: string): Array\<string>;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：System；<br>API声明：static isSuggested(language: string, region?: string): boolean;<br>差异内容：NA|类名：System；<br>API声明：static isSuggested(language: string, region?: string): boolean;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：System；<br>API声明：static getSystemRegion(): string;<br>差异内容：NA|类名：System；<br>API声明：static getSystemRegion(): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：System；<br>API声明：static is24HourClock(): boolean;<br>差异内容：NA|类名：System；<br>API声明：static is24HourClock(): boolean;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：System；<br>API声明：static getPreferredLanguageList(): Array\<string>;<br>差异内容：NA|类名：System；<br>API声明：static getPreferredLanguageList(): Array\<string>;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：System；<br>API声明：static getFirstPreferredLanguage(): string;<br>差异内容：NA|类名：System；<br>API声明：static getFirstPreferredLanguage(): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：System；<br>API声明：static setAppPreferredLanguage(language: string): void;<br>差异内容：NA|类名：System；<br>API声明：static setAppPreferredLanguage(language: string): void;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：System；<br>API声明：static getAppPreferredLanguage(): string;<br>差异内容：NA|类名：System；<br>API声明：static getAppPreferredLanguage(): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：System；<br>API声明：static getUsingLocalDigit(): boolean;<br>差异内容：NA|类名：System；<br>API声明：static getUsingLocalDigit(): boolean;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export class I18NUtil<br>差异内容：NA|类名：i18n；<br>API声明：export class I18NUtil<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：I18NUtil；<br>API声明：static unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: number, locale: string, style?: string): string;<br>差异内容：NA|类名：I18NUtil；<br>API声明：static unitConvert(fromUnit: UnitInfo, toUnit: UnitInfo, value: number, locale: string, style?: string): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：I18NUtil；<br>API声明：static getDateOrder(locale: string): string;<br>差异内容：NA|类名：I18NUtil；<br>API声明：static getDateOrder(locale: string): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：I18NUtil；<br>API声明：static getTimePeriodName(hour: number, locale?: string): string;<br>差异内容：NA|类名：I18NUtil；<br>API声明：static getTimePeriodName(hour: number, locale?: string): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export interface UnitInfo<br>差异内容：NA|类名：i18n；<br>API声明：export interface UnitInfo<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：UnitInfo；<br>API声明：unit: string;<br>差异内容：NA|类名：UnitInfo；<br>API声明：unit: string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：UnitInfo；<br>API声明：measureSystem: string;<br>差异内容：NA|类名：UnitInfo；<br>API声明：measureSystem: string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export interface PhoneNumberFormatOptions<br>差异内容：NA|类名：i18n；<br>API声明：export interface PhoneNumberFormatOptions<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：PhoneNumberFormatOptions；<br>API声明：type?: string;<br>差异内容：NA|类名：PhoneNumberFormatOptions；<br>API声明：type?: string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export class PhoneNumberFormat<br>差异内容：NA|类名：i18n；<br>API声明：export class PhoneNumberFormat<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：PhoneNumberFormat；<br>API声明：isValidNumber(number: string): boolean;<br>差异内容：NA|类名：PhoneNumberFormat；<br>API声明：isValidNumber(number: string): boolean;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：PhoneNumberFormat；<br>API声明：format(number: string): string;<br>差异内容：NA|类名：PhoneNumberFormat；<br>API声明：format(number: string): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：PhoneNumberFormat；<br>API声明：getLocationName(number: string, locale: string): string;<br>差异内容：NA|类名：PhoneNumberFormat；<br>API声明：getLocationName(number: string, locale: string): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export function getCalendar(locale: string, type?: string): Calendar;<br>差异内容：NA|类名：i18n；<br>API声明：export function getCalendar(locale: string, type?: string): Calendar;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export class Calendar<br>差异内容：NA|类名：i18n；<br>API声明：export class Calendar<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Calendar；<br>API声明：setTime(date: Date): void;<br>差异内容：NA|类名：Calendar；<br>API声明：setTime(date: Date): void;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Calendar；<br>API声明：setTime(time: number): void;<br>差异内容：NA|类名：Calendar；<br>API声明：setTime(time: number): void;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Calendar；<br>API声明：set(year: number, month: number, date: number, hour?: number, minute?: number, second?: number): void;<br>差异内容：NA|类名：Calendar；<br>API声明：set(year: number, month: number, date: number, hour?: number, minute?: number, second?: number): void;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Calendar；<br>API声明：setTimeZone(timezone: string): void;<br>差异内容：NA|类名：Calendar；<br>API声明：setTimeZone(timezone: string): void;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Calendar；<br>API声明：getTimeZone(): string;<br>差异内容：NA|类名：Calendar；<br>API声明：getTimeZone(): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Calendar；<br>API声明：getFirstDayOfWeek(): number;<br>差异内容：NA|类名：Calendar；<br>API声明：getFirstDayOfWeek(): number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Calendar；<br>API声明：setFirstDayOfWeek(value: number): void;<br>差异内容：NA|类名：Calendar；<br>API声明：setFirstDayOfWeek(value: number): void;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Calendar；<br>API声明：getMinimalDaysInFirstWeek(): number;<br>差异内容：NA|类名：Calendar；<br>API声明：getMinimalDaysInFirstWeek(): number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Calendar；<br>API声明：setMinimalDaysInFirstWeek(value: number): void;<br>差异内容：NA|类名：Calendar；<br>API声明：setMinimalDaysInFirstWeek(value: number): void;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Calendar；<br>API声明：get(field: string): number;<br>差异内容：NA|类名：Calendar；<br>API声明：get(field: string): number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Calendar；<br>API声明：getDisplayName(locale: string): string;<br>差异内容：NA|类名：Calendar；<br>API声明：getDisplayName(locale: string): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Calendar；<br>API声明：isWeekend(date?: Date): boolean;<br>差异内容：NA|类名：Calendar；<br>API声明：isWeekend(date?: Date): boolean;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Calendar；<br>API声明：add(field: string, amount: number): void;<br>差异内容：NA|类名：Calendar；<br>API声明：add(field: string, amount: number): void;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Calendar；<br>API声明：getTimeInMillis(): number;<br>差异内容：NA|类名：Calendar；<br>API声明：getTimeInMillis(): number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Calendar；<br>API声明：compareDays(date: Date): number;<br>差异内容：NA|类名：Calendar；<br>API声明：compareDays(date: Date): number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export function isRTL(locale: string): boolean;<br>差异内容：NA|类名：i18n；<br>API声明：export function isRTL(locale: string): boolean;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export function getLineInstance(locale: string): BreakIterator;<br>差异内容：NA|类名：i18n；<br>API声明：export function getLineInstance(locale: string): BreakIterator;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export class BreakIterator<br>差异内容：NA|类名：i18n；<br>API声明：export class BreakIterator<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：BreakIterator；<br>API声明：current(): number;<br>差异内容：NA|类名：BreakIterator；<br>API声明：current(): number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：BreakIterator；<br>API声明：first(): number;<br>差异内容：NA|类名：BreakIterator；<br>API声明：first(): number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：BreakIterator；<br>API声明：last(): number;<br>差异内容：NA|类名：BreakIterator；<br>API声明：last(): number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：BreakIterator；<br>API声明：next(index?: number): number;<br>差异内容：NA|类名：BreakIterator；<br>API声明：next(index?: number): number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：BreakIterator；<br>API声明：previous(): number;<br>差异内容：NA|类名：BreakIterator；<br>API声明：previous(): number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：BreakIterator；<br>API声明：setLineBreakText(text: string): void;<br>差异内容：NA|类名：BreakIterator；<br>API声明：setLineBreakText(text: string): void;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：BreakIterator；<br>API声明：following(offset: number): number;<br>差异内容：NA|类名：BreakIterator；<br>API声明：following(offset: number): number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：BreakIterator；<br>API声明：getLineBreakText(): string;<br>差异内容：NA|类名：BreakIterator；<br>API声明：getLineBreakText(): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：BreakIterator；<br>API声明：isBoundary(offset: number): boolean;<br>差异内容：NA|类名：BreakIterator；<br>API声明：isBoundary(offset: number): boolean;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export function getInstance(locale?: string): IndexUtil;<br>差异内容：NA|类名：i18n；<br>API声明：export function getInstance(locale?: string): IndexUtil;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export class IndexUtil<br>差异内容：NA|类名：i18n；<br>API声明：export class IndexUtil<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：IndexUtil；<br>API声明：getIndexList(): Array\<string>;<br>差异内容：NA|类名：IndexUtil；<br>API声明：getIndexList(): Array\<string>;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：IndexUtil；<br>API声明：addLocale(locale: string): void;<br>差异内容：NA|类名：IndexUtil；<br>API声明：addLocale(locale: string): void;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：IndexUtil；<br>API声明：getIndex(text: string): string;<br>差异内容：NA|类名：IndexUtil；<br>API声明：getIndex(text: string): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export class Unicode<br>差异内容：NA|类名：i18n；<br>API声明：export class Unicode<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Unicode；<br>API声明：static isDigit(char: string): boolean;<br>差异内容：NA|类名：Unicode；<br>API声明：static isDigit(char: string): boolean;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Unicode；<br>API声明：static isSpaceChar(char: string): boolean;<br>差异内容：NA|类名：Unicode；<br>API声明：static isSpaceChar(char: string): boolean;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Unicode；<br>API声明：static isWhitespace(char: string): boolean;<br>差异内容：NA|类名：Unicode；<br>API声明：static isWhitespace(char: string): boolean;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Unicode；<br>API声明：static isRTL(char: string): boolean;<br>差异内容：NA|类名：Unicode；<br>API声明：static isRTL(char: string): boolean;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Unicode；<br>API声明：static isIdeograph(char: string): boolean;<br>差异内容：NA|类名：Unicode；<br>API声明：static isIdeograph(char: string): boolean;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Unicode；<br>API声明：static isLetter(char: string): boolean;<br>差异内容：NA|类名：Unicode；<br>API声明：static isLetter(char: string): boolean;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Unicode；<br>API声明：static isLowerCase(char: string): boolean;<br>差异内容：NA|类名：Unicode；<br>API声明：static isLowerCase(char: string): boolean;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Unicode；<br>API声明：static isUpperCase(char: string): boolean;<br>差异内容：NA|类名：Unicode；<br>API声明：static isUpperCase(char: string): boolean;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Unicode；<br>API声明：static getType(char: string): string;<br>差异内容：NA|类名：Unicode；<br>API声明：static getType(char: string): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export function getTimeZone(zoneID?: string): TimeZone;<br>差异内容：NA|类名：i18n；<br>API声明：export function getTimeZone(zoneID?: string): TimeZone;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export class TimeZone<br>差异内容：NA|类名：i18n；<br>API声明：export class TimeZone<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：TimeZone；<br>API声明：getID(): string;<br>差异内容：NA|类名：TimeZone；<br>API声明：getID(): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：TimeZone；<br>API声明：getDisplayName(locale?: string, isDST?: boolean): string;<br>差异内容：NA|类名：TimeZone；<br>API声明：getDisplayName(locale?: string, isDST?: boolean): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：TimeZone；<br>API声明：getRawOffset(): number;<br>差异内容：NA|类名：TimeZone；<br>API声明：getRawOffset(): number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：TimeZone；<br>API声明：getOffset(date?: number): number;<br>差异内容：NA|类名：TimeZone；<br>API声明：getOffset(date?: number): number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：TimeZone；<br>API声明：static getAvailableIDs(): Array\<string>;<br>差异内容：NA|类名：TimeZone；<br>API声明：static getAvailableIDs(): Array\<string>;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：TimeZone；<br>API声明：static getAvailableZoneCityIDs(): Array\<string>;<br>差异内容：NA|类名：TimeZone；<br>API声明：static getAvailableZoneCityIDs(): Array\<string>;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：TimeZone；<br>API声明：static getCityDisplayName(cityID: string, locale: string): string;<br>差异内容：NA|类名：TimeZone；<br>API声明：static getCityDisplayName(cityID: string, locale: string): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：TimeZone；<br>API声明：static getTimezoneFromCity(cityID: string): TimeZone;<br>差异内容：NA|类名：TimeZone；<br>API声明：static getTimezoneFromCity(cityID: string): TimeZone;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：TimeZone；<br>API声明：static getTimezonesByLocation(longitude: number, latitude: number): Array\<TimeZone>;<br>差异内容：NA|类名：TimeZone；<br>API声明：static getTimezonesByLocation(longitude: number, latitude: number): Array\<TimeZone>;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export class Transliterator<br>差异内容：NA|类名：i18n；<br>API声明：export class Transliterator<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Transliterator；<br>API声明：static getAvailableIDs(): string[];<br>差异内容：NA|类名：Transliterator；<br>API声明：static getAvailableIDs(): string[];<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Transliterator；<br>API声明：static getInstance(id: string): Transliterator;<br>差异内容：NA|类名：Transliterator；<br>API声明：static getInstance(id: string): Transliterator;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Transliterator；<br>API声明：transform(text: string): string;<br>差异内容：NA|类名：Transliterator；<br>API声明：transform(text: string): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export enum NormalizerMode<br>差异内容：NA|类名：i18n；<br>API声明：export enum NormalizerMode<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：NormalizerMode；<br>API声明：NFC = 1<br>差异内容：NA|类名：NormalizerMode；<br>API声明：NFC = 1<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：NormalizerMode；<br>API声明：NFD = 2<br>差异内容：NA|类名：NormalizerMode；<br>API声明：NFD = 2<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：NormalizerMode；<br>API声明：NFKC = 3<br>差异内容：NA|类名：NormalizerMode；<br>API声明：NFKC = 3<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：NormalizerMode；<br>API声明：NFKD = 4<br>差异内容：NA|类名：NormalizerMode；<br>API声明：NFKD = 4<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export class Normalizer<br>差异内容：NA|类名：i18n；<br>API声明：export class Normalizer<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Normalizer；<br>API声明：static getInstance(mode: NormalizerMode): Normalizer;<br>差异内容：NA|类名：Normalizer；<br>API声明：static getInstance(mode: NormalizerMode): Normalizer;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：Normalizer；<br>API声明：normalize(text: string): string;<br>差异内容：NA|类名：Normalizer；<br>API声明：normalize(text: string): string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export interface HolidayInfoItem<br>差异内容：NA|类名：i18n；<br>API声明：export interface HolidayInfoItem<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：HolidayInfoItem；<br>API声明：baseName: string;<br>差异内容：NA|类名：HolidayInfoItem；<br>API声明：baseName: string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：HolidayInfoItem；<br>API声明：year: number;<br>差异内容：NA|类名：HolidayInfoItem；<br>API声明：year: number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：HolidayInfoItem；<br>API声明：month: number;<br>差异内容：NA|类名：HolidayInfoItem；<br>API声明：month: number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：HolidayInfoItem；<br>API声明：day: number;<br>差异内容：NA|类名：HolidayInfoItem；<br>API声明：day: number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：HolidayInfoItem；<br>API声明：localNames?: Array\<HolidayLocalName>;<br>差异内容：NA|类名：HolidayInfoItem；<br>API声明：localNames?: Array\<HolidayLocalName>;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export interface HolidayLocalName<br>差异内容：NA|类名：i18n；<br>API声明：export interface HolidayLocalName<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：HolidayLocalName；<br>API声明：language: string;<br>差异内容：NA|类名：HolidayLocalName；<br>API声明：language: string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：HolidayLocalName；<br>API声明：name: string;<br>差异内容：NA|类名：HolidayLocalName；<br>API声明：name: string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export class HolidayManager<br>差异内容：NA|类名：i18n；<br>API声明：export class HolidayManager<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：HolidayManager；<br>API声明：isHoliday(date?: Date): boolean;<br>差异内容：NA|类名：HolidayManager；<br>API声明：isHoliday(date?: Date): boolean;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：HolidayManager；<br>API声明：getHolidayInfoItemArray(year?: number): Array\<HolidayInfoItem>;<br>差异内容：NA|类名：HolidayManager；<br>API声明：getHolidayInfoItemArray(year?: number): Array\<HolidayInfoItem>;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export interface EntityInfoItem<br>差异内容：NA|类名：i18n；<br>API声明：export interface EntityInfoItem<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：EntityInfoItem；<br>API声明：begin: number;<br>差异内容：NA|类名：EntityInfoItem；<br>API声明：begin: number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：EntityInfoItem；<br>API声明：end: number;<br>差异内容：NA|类名：EntityInfoItem；<br>API声明：end: number;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：EntityInfoItem；<br>API声明：type: string;<br>差异内容：NA|类名：EntityInfoItem；<br>API声明：type: string;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：i18n；<br>API声明：export class EntityRecognizer<br>差异内容：NA|类名：i18n；<br>API声明：export class EntityRecognizer<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：EntityRecognizer；<br>API声明：findEntityInfo(text: string): Array\<EntityInfoItem>;<br>差异内容：NA|类名：EntityRecognizer；<br>API声明：findEntityInfo(text: string): Array\<EntityInfoItem>;<br>差异内容：atomicservice|api/@ohos.i18n.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace intl<br>差异内容：NA|类名：global；<br>API声明：declare namespace intl<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：intl；<br>API声明：export interface LocaleOptions<br>差异内容：NA|类名：intl；<br>API声明：export interface LocaleOptions<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：LocaleOptions；<br>API声明：calendar?: string;<br>差异内容：NA|类名：LocaleOptions；<br>API声明：calendar?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：LocaleOptions；<br>API声明：collation?: string;<br>差异内容：NA|类名：LocaleOptions；<br>API声明：collation?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：LocaleOptions；<br>API声明：hourCycle?: string;<br>差异内容：NA|类名：LocaleOptions；<br>API声明：hourCycle?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：LocaleOptions；<br>API声明：numberingSystem?: string;<br>差异内容：NA|类名：LocaleOptions；<br>API声明：numberingSystem?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：LocaleOptions；<br>API声明：numeric?: boolean;<br>差异内容：NA|类名：LocaleOptions；<br>API声明：numeric?: boolean;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：LocaleOptions；<br>API声明：caseFirst?: string;<br>差异内容：NA|类名：LocaleOptions；<br>API声明：caseFirst?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：intl；<br>API声明：export class Locale<br>差异内容：NA|类名：intl；<br>API声明：export class Locale<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：Locale；<br>API声明：language: string;<br>差异内容：NA|类名：Locale；<br>API声明：language: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：Locale；<br>API声明：script: string;<br>差异内容：NA|类名：Locale；<br>API声明：script: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：Locale；<br>API声明：region: string;<br>差异内容：NA|类名：Locale；<br>API声明：region: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：Locale；<br>API声明：baseName: string;<br>差异内容：NA|类名：Locale；<br>API声明：baseName: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：Locale；<br>API声明：caseFirst: string;<br>差异内容：NA|类名：Locale；<br>API声明：caseFirst: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：Locale；<br>API声明：calendar: string;<br>差异内容：NA|类名：Locale；<br>API声明：calendar: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：Locale；<br>API声明：collation: string;<br>差异内容：NA|类名：Locale；<br>API声明：collation: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：Locale；<br>API声明：hourCycle: string;<br>差异内容：NA|类名：Locale；<br>API声明：hourCycle: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：Locale；<br>API声明：numberingSystem: string;<br>差异内容：NA|类名：Locale；<br>API声明：numberingSystem: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：Locale；<br>API声明：numeric: boolean;<br>差异内容：NA|类名：Locale；<br>API声明：numeric: boolean;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：Locale；<br>API声明：toString(): string;<br>差异内容：NA|类名：Locale；<br>API声明：toString(): string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：Locale；<br>API声明：maximize(): Locale;<br>差异内容：NA|类名：Locale；<br>API声明：maximize(): Locale;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：Locale；<br>API声明：minimize(): Locale;<br>差异内容：NA|类名：Locale；<br>API声明：minimize(): Locale;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：intl；<br>API声明：export interface DateTimeOptions<br>差异内容：NA|类名：intl；<br>API声明：export interface DateTimeOptions<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：locale?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：locale?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：dateStyle?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：dateStyle?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：timeStyle?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：timeStyle?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：hourCycle?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：hourCycle?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：timeZone?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：timeZone?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：numberingSystem?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：numberingSystem?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：hour12?: boolean;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：hour12?: boolean;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：weekday?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：weekday?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：era?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：era?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：year?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：year?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：month?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：month?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：day?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：day?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：hour?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：hour?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：minute?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：minute?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：second?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：second?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：timeZoneName?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：timeZoneName?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：dayPeriod?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：dayPeriod?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：localeMatcher?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：localeMatcher?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeOptions；<br>API声明：formatMatcher?: string;<br>差异内容：NA|类名：DateTimeOptions；<br>API声明：formatMatcher?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：intl；<br>API声明：export class DateTimeFormat<br>差异内容：NA|类名：intl；<br>API声明：export class DateTimeFormat<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeFormat；<br>API声明：format(date: Date): string;<br>差异内容：NA|类名：DateTimeFormat；<br>API声明：format(date: Date): string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeFormat；<br>API声明：formatRange(startDate: Date, endDate: Date): string;<br>差异内容：NA|类名：DateTimeFormat；<br>API声明：formatRange(startDate: Date, endDate: Date): string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：DateTimeFormat；<br>API声明：resolvedOptions(): DateTimeOptions;<br>差异内容：NA|类名：DateTimeFormat；<br>API声明：resolvedOptions(): DateTimeOptions;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：intl；<br>API声明：export interface NumberOptions<br>差异内容：NA|类名：intl；<br>API声明：export interface NumberOptions<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：locale?: string;<br>差异内容：NA|类名：NumberOptions；<br>API声明：locale?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：currency?: string;<br>差异内容：NA|类名：NumberOptions；<br>API声明：currency?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：currencySign?: string;<br>差异内容：NA|类名：NumberOptions；<br>API声明：currencySign?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：currencyDisplay?: string;<br>差异内容：NA|类名：NumberOptions；<br>API声明：currencyDisplay?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：unit?: string;<br>差异内容：NA|类名：NumberOptions；<br>API声明：unit?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：unitDisplay?: string;<br>差异内容：NA|类名：NumberOptions；<br>API声明：unitDisplay?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：unitUsage?: string;<br>差异内容：NA|类名：NumberOptions；<br>API声明：unitUsage?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：signDisplay?: string;<br>差异内容：NA|类名：NumberOptions；<br>API声明：signDisplay?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：compactDisplay?: string;<br>差异内容：NA|类名：NumberOptions；<br>API声明：compactDisplay?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：notation?: string;<br>差异内容：NA|类名：NumberOptions；<br>API声明：notation?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：localeMatcher?: string;<br>差异内容：NA|类名：NumberOptions；<br>API声明：localeMatcher?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：style?: string;<br>差异内容：NA|类名：NumberOptions；<br>API声明：style?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：numberingSystem?: string;<br>差异内容：NA|类名：NumberOptions；<br>API声明：numberingSystem?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：useGrouping?: boolean;<br>差异内容：NA|类名：NumberOptions；<br>API声明：useGrouping?: boolean;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：minimumIntegerDigits?: number;<br>差异内容：NA|类名：NumberOptions；<br>API声明：minimumIntegerDigits?: number;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：minimumFractionDigits?: number;<br>差异内容：NA|类名：NumberOptions；<br>API声明：minimumFractionDigits?: number;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：maximumFractionDigits?: number;<br>差异内容：NA|类名：NumberOptions；<br>API声明：maximumFractionDigits?: number;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：minimumSignificantDigits?: number;<br>差异内容：NA|类名：NumberOptions；<br>API声明：minimumSignificantDigits?: number;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberOptions；<br>API声明：maximumSignificantDigits?: number;<br>差异内容：NA|类名：NumberOptions；<br>API声明：maximumSignificantDigits?: number;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：intl；<br>API声明：export class NumberFormat<br>差异内容：NA|类名：intl；<br>API声明：export class NumberFormat<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberFormat；<br>API声明：format(number: number): string;<br>差异内容：NA|类名：NumberFormat；<br>API声明：format(number: number): string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：NumberFormat；<br>API声明：resolvedOptions(): NumberOptions;<br>差异内容：NA|类名：NumberFormat；<br>API声明：resolvedOptions(): NumberOptions;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：intl；<br>API声明：export interface CollatorOptions<br>差异内容：NA|类名：intl；<br>API声明：export interface CollatorOptions<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：CollatorOptions；<br>API声明：localeMatcher?: string;<br>差异内容：NA|类名：CollatorOptions；<br>API声明：localeMatcher?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：CollatorOptions；<br>API声明：usage?: string;<br>差异内容：NA|类名：CollatorOptions；<br>API声明：usage?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：CollatorOptions；<br>API声明：sensitivity?: string;<br>差异内容：NA|类名：CollatorOptions；<br>API声明：sensitivity?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：CollatorOptions；<br>API声明：ignorePunctuation?: boolean;<br>差异内容：NA|类名：CollatorOptions；<br>API声明：ignorePunctuation?: boolean;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：CollatorOptions；<br>API声明：collation?: string;<br>差异内容：NA|类名：CollatorOptions；<br>API声明：collation?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：CollatorOptions；<br>API声明：numeric?: boolean;<br>差异内容：NA|类名：CollatorOptions；<br>API声明：numeric?: boolean;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：CollatorOptions；<br>API声明：caseFirst?: string;<br>差异内容：NA|类名：CollatorOptions；<br>API声明：caseFirst?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：intl；<br>API声明：export class Collator<br>差异内容：NA|类名：intl；<br>API声明：export class Collator<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：Collator；<br>API声明：compare(first: string, second: string): number;<br>差异内容：NA|类名：Collator；<br>API声明：compare(first: string, second: string): number;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：Collator；<br>API声明：resolvedOptions(): CollatorOptions;<br>差异内容：NA|类名：Collator；<br>API声明：resolvedOptions(): CollatorOptions;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：intl；<br>API声明：export interface PluralRulesOptions<br>差异内容：NA|类名：intl；<br>API声明：export interface PluralRulesOptions<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：PluralRulesOptions；<br>API声明：localeMatcher?: string;<br>差异内容：NA|类名：PluralRulesOptions；<br>API声明：localeMatcher?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：PluralRulesOptions；<br>API声明：type?: string;<br>差异内容：NA|类名：PluralRulesOptions；<br>API声明：type?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：PluralRulesOptions；<br>API声明：minimumIntegerDigits?: number;<br>差异内容：NA|类名：PluralRulesOptions；<br>API声明：minimumIntegerDigits?: number;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：PluralRulesOptions；<br>API声明：minimumFractionDigits?: number;<br>差异内容：NA|类名：PluralRulesOptions；<br>API声明：minimumFractionDigits?: number;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：PluralRulesOptions；<br>API声明：maximumFractionDigits?: number;<br>差异内容：NA|类名：PluralRulesOptions；<br>API声明：maximumFractionDigits?: number;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：PluralRulesOptions；<br>API声明：minimumSignificantDigits?: number;<br>差异内容：NA|类名：PluralRulesOptions；<br>API声明：minimumSignificantDigits?: number;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：PluralRulesOptions；<br>API声明：maximumSignificantDigits?: number;<br>差异内容：NA|类名：PluralRulesOptions；<br>API声明：maximumSignificantDigits?: number;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：intl；<br>API声明：export class PluralRules<br>差异内容：NA|类名：intl；<br>API声明：export class PluralRules<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：PluralRules；<br>API声明：select(n: number): string;<br>差异内容：NA|类名：PluralRules；<br>API声明：select(n: number): string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：intl；<br>API声明：export interface RelativeTimeFormatInputOptions<br>差异内容：NA|类名：intl；<br>API声明：export interface RelativeTimeFormatInputOptions<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：RelativeTimeFormatInputOptions；<br>API声明：localeMatcher?: string;<br>差异内容：NA|类名：RelativeTimeFormatInputOptions；<br>API声明：localeMatcher?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：RelativeTimeFormatInputOptions；<br>API声明：numeric?: string;<br>差异内容：NA|类名：RelativeTimeFormatInputOptions；<br>API声明：numeric?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：RelativeTimeFormatInputOptions；<br>API声明：style?: string;<br>差异内容：NA|类名：RelativeTimeFormatInputOptions；<br>API声明：style?: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：intl；<br>API声明：export interface RelativeTimeFormatResolvedOptions<br>差异内容：NA|类名：intl；<br>API声明：export interface RelativeTimeFormatResolvedOptions<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：RelativeTimeFormatResolvedOptions；<br>API声明：locale: string;<br>差异内容：NA|类名：RelativeTimeFormatResolvedOptions；<br>API声明：locale: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：RelativeTimeFormatResolvedOptions；<br>API声明：style: string;<br>差异内容：NA|类名：RelativeTimeFormatResolvedOptions；<br>API声明：style: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：RelativeTimeFormatResolvedOptions；<br>API声明：numeric: string;<br>差异内容：NA|类名：RelativeTimeFormatResolvedOptions；<br>API声明：numeric: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：RelativeTimeFormatResolvedOptions；<br>API声明：numberingSystem: string;<br>差异内容：NA|类名：RelativeTimeFormatResolvedOptions；<br>API声明：numberingSystem: string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：intl；<br>API声明：export class RelativeTimeFormat<br>差异内容：NA|类名：intl；<br>API声明：export class RelativeTimeFormat<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：RelativeTimeFormat；<br>API声明：format(value: number, unit: string): string;<br>差异内容：NA|类名：RelativeTimeFormat；<br>API声明：format(value: number, unit: string): string;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：RelativeTimeFormat；<br>API声明：formatToParts(value: number, unit: string): Array\<object>;<br>差异内容：NA|类名：RelativeTimeFormat；<br>API声明：formatToParts(value: number, unit: string): Array\<object>;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
|API从不支持元服务到支持元服务|类名：RelativeTimeFormat；<br>API声明：resolvedOptions(): RelativeTimeFormatResolvedOptions;<br>差异内容：NA|类名：RelativeTimeFormat；<br>API声明：resolvedOptions(): RelativeTimeFormatResolvedOptions;<br>差异内容：atomicservice|api/@ohos.intl.d.ts|
