| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace calendarManager<br>差异内容：declare namespace calendarManager|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：function getCalendarManager(context: Context): CalendarManager;<br>差异内容：function getCalendarManager(context: Context): CalendarManager;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：export interface CalendarManager<br>差异内容：export interface CalendarManager|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarManager；<br>API声明：createCalendar(calendarAccount: CalendarAccount): Promise\<Calendar>;<br>差异内容：createCalendar(calendarAccount: CalendarAccount): Promise\<Calendar>;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarManager；<br>API声明：createCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;<br>差异内容：createCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarManager；<br>API声明：deleteCalendar(calendar: Calendar): Promise\<void>;<br>差异内容：deleteCalendar(calendar: Calendar): Promise\<void>;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarManager；<br>API声明：deleteCalendar(calendar: Calendar, callback: AsyncCallback\<void>): void;<br>差异内容：deleteCalendar(calendar: Calendar, callback: AsyncCallback\<void>): void;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarManager；<br>API声明：getCalendar(calendarAccount?: CalendarAccount): Promise\<Calendar>;<br>差异内容：getCalendar(calendarAccount?: CalendarAccount): Promise\<Calendar>;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarManager；<br>API声明：getCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;<br>差异内容：getCalendar(calendarAccount: CalendarAccount, callback: AsyncCallback\<Calendar>): void;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarManager；<br>API声明：getCalendar(callback: AsyncCallback\<Calendar>): void;<br>差异内容：getCalendar(callback: AsyncCallback\<Calendar>): void;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarManager；<br>API声明：getAllCalendars(): Promise\<Calendar[]>;<br>差异内容：getAllCalendars(): Promise\<Calendar[]>;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarManager；<br>API声明：getAllCalendars(callback: AsyncCallback\<Calendar[]>): void;<br>差异内容：getAllCalendars(callback: AsyncCallback\<Calendar[]>): void;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：export interface Calendar<br>差异内容：export interface Calendar|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：readonly id: number;<br>差异内容：readonly id: number;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：addEvent(event: Event): Promise\<number>;<br>差异内容：addEvent(event: Event): Promise\<number>;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：addEvent(event: Event, callback: AsyncCallback\<number>): void;<br>差异内容：addEvent(event: Event, callback: AsyncCallback\<number>): void;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：addEvents(events: Event[]): Promise\<void>;<br>差异内容：addEvents(events: Event[]): Promise\<void>;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：addEvents(events: Event[], callback: AsyncCallback\<void>): void;<br>差异内容：addEvents(events: Event[], callback: AsyncCallback\<void>): void;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：deleteEvent(id: number): Promise\<void>;<br>差异内容：deleteEvent(id: number): Promise\<void>;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：deleteEvent(id: number, callback: AsyncCallback\<void>): void;<br>差异内容：deleteEvent(id: number, callback: AsyncCallback\<void>): void;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：deleteEvents(ids: number[]): Promise\<void>;<br>差异内容：deleteEvents(ids: number[]): Promise\<void>;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：deleteEvents(ids: number[], callback: AsyncCallback\<void>): void;<br>差异内容：deleteEvents(ids: number[], callback: AsyncCallback\<void>): void;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：updateEvent(event: Event): Promise\<void>;<br>差异内容：updateEvent(event: Event): Promise\<void>;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：updateEvent(event: Event, callback: AsyncCallback\<void>): void;<br>差异内容：updateEvent(event: Event, callback: AsyncCallback\<void>): void;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：getEvents(eventFilter?: EventFilter, eventKey?: (keyof Event)[]): Promise\<Event[]>;<br>差异内容：getEvents(eventFilter?: EventFilter, eventKey?: (keyof Event)[]): Promise\<Event[]>;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：getEvents(eventFilter: EventFilter, eventKey: (keyof Event)[], callback: AsyncCallback\<Event[]>): void;<br>差异内容：getEvents(eventFilter: EventFilter, eventKey: (keyof Event)[], callback: AsyncCallback\<Event[]>): void;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：getEvents(callback: AsyncCallback\<Event[]>): void;<br>差异内容：getEvents(callback: AsyncCallback\<Event[]>): void;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：getConfig(): CalendarConfig;<br>差异内容：getConfig(): CalendarConfig;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：setConfig(config: CalendarConfig): Promise\<void>;<br>差异内容：setConfig(config: CalendarConfig): Promise\<void>;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：setConfig(config: CalendarConfig, callback: AsyncCallback\<void>): void;<br>差异内容：setConfig(config: CalendarConfig, callback: AsyncCallback\<void>): void;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Calendar；<br>API声明：getAccount(): CalendarAccount;<br>差异内容：getAccount(): CalendarAccount;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：interface CalendarAccount<br>差异内容：interface CalendarAccount|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarAccount；<br>API声明：readonly name: string;<br>差异内容：readonly name: string;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarAccount；<br>API声明：type: CalendarType;<br>差异内容：type: CalendarType;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarAccount；<br>API声明：displayName?: string;<br>差异内容：displayName?: string;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：interface CalendarConfig<br>差异内容：interface CalendarConfig|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarConfig；<br>API声明：enableReminder?: boolean;<br>差异内容：enableReminder?: boolean;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarConfig；<br>API声明：color?: number \| string;<br>差异内容：color?: number \| string;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：interface Event<br>差异内容：interface Event|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：id?: number;<br>差异内容：id?: number;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：type: EventType;<br>差异内容：type: EventType;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：title?: string;<br>差异内容：title?: string;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：location?: Location;<br>差异内容：location?: Location;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：startTime: number;<br>差异内容：startTime: number;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：endTime: number;<br>差异内容：endTime: number;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：isAllDay?: boolean;<br>差异内容：isAllDay?: boolean;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：attendee?: Attendee[];<br>差异内容：attendee?: Attendee[];|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：timeZone?: string;<br>差异内容：timeZone?: string;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：reminderTime?: number[];<br>差异内容：reminderTime?: number[];|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：recurrenceRule?: RecurrenceRule;<br>差异内容：recurrenceRule?: RecurrenceRule;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：description?: string;<br>差异内容：description?: string;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Event；<br>API声明：service?: EventService;<br>差异内容：service?: EventService;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：enum CalendarType<br>差异内容：enum CalendarType|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarType；<br>API声明：LOCAL = 'local'<br>差异内容：LOCAL = 'local'|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarType；<br>API声明：EMAIL = 'email'<br>差异内容：EMAIL = 'email'|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarType；<br>API声明：BIRTHDAY = 'birthday'<br>差异内容：BIRTHDAY = 'birthday'|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarType；<br>API声明：CALDAV = 'caldav'<br>差异内容：CALDAV = 'caldav'|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：CalendarType；<br>API声明：SUBSCRIBED = 'subscribed'<br>差异内容：SUBSCRIBED = 'subscribed'|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：interface Location<br>差异内容：interface Location|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：location?: string;<br>差异内容：location?: string;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：longitude?: number;<br>差异内容：longitude?: number;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Location；<br>API声明：latitude?: number;<br>差异内容：latitude?: number;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：class EventFilter<br>差异内容：class EventFilter|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：EventFilter；<br>API声明：static filterById(ids: number[]): EventFilter;<br>差异内容：static filterById(ids: number[]): EventFilter;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：EventFilter；<br>API声明：static filterByTime(start: number, end: number): EventFilter;<br>差异内容：static filterByTime(start: number, end: number): EventFilter;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：EventFilter；<br>API声明：static filterByTitle(title: string): EventFilter;<br>差异内容：static filterByTitle(title: string): EventFilter;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：enum EventType<br>差异内容：enum EventType|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：EventType；<br>API声明：NORMAL = 0<br>差异内容：NORMAL = 0|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：EventType；<br>API声明：IMPORTANT = 1<br>差异内容：IMPORTANT = 1|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：export interface RecurrenceRule<br>差异内容：export interface RecurrenceRule|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：RecurrenceRule；<br>API声明：recurrenceFrequency: RecurrenceFrequency;<br>差异内容：recurrenceFrequency: RecurrenceFrequency;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：RecurrenceRule；<br>API声明：expire?: number;<br>差异内容：expire?: number;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：export enum RecurrenceFrequency<br>差异内容：export enum RecurrenceFrequency|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：RecurrenceFrequency；<br>API声明：YEARLY = 0<br>差异内容：YEARLY = 0|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：RecurrenceFrequency；<br>API声明：MONTHLY = 1<br>差异内容：MONTHLY = 1|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：RecurrenceFrequency；<br>API声明：WEEKLY = 2<br>差异内容：WEEKLY = 2|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：RecurrenceFrequency；<br>API声明：DAILY = 3<br>差异内容：DAILY = 3|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：export interface Attendee<br>差异内容：export interface Attendee|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Attendee；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：Attendee；<br>API声明：email: string;<br>差异内容：email: string;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：export interface EventService<br>差异内容：export interface EventService|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：EventService；<br>API声明：type: ServiceType;<br>差异内容：type: ServiceType;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：EventService；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：EventService；<br>API声明：description?: string;<br>差异内容：description?: string;|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：calendarManager；<br>API声明：export enum ServiceType<br>差异内容：export enum ServiceType|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：ServiceType；<br>API声明：MEETING = 'Meeting'<br>差异内容：MEETING = 'Meeting'|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：ServiceType；<br>API声明：WATCHING = 'Watching'<br>差异内容：WATCHING = 'Watching'|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：ServiceType；<br>API声明：REPAYMENT = 'Repayment'<br>差异内容：REPAYMENT = 'Repayment'|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：ServiceType；<br>API声明：LIVE = 'Live'<br>差异内容：LIVE = 'Live'|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：ServiceType；<br>API声明：SHOPPING = 'Shopping'<br>差异内容：SHOPPING = 'Shopping'|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：ServiceType；<br>API声明：TRIP = 'Trip'<br>差异内容：TRIP = 'Trip'|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：ServiceType；<br>API声明：CLASS = 'Class'<br>差异内容：CLASS = 'Class'|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：ServiceType；<br>API声明：SPORTS_EVENTS = 'SportsEvents'<br>差异内容：SPORTS_EVENTS = 'SportsEvents'|api/@ohos.calendarManager.d.ts|
|新增API|NA|类名：ServiceType；<br>API声明：SPORTS_EXERCISE = 'SportsExercise'<br>差异内容：SPORTS_EXERCISE = 'SportsExercise'|api/@ohos.calendarManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.calendarManager.d.ts<br>差异内容：CalendarKit|api/@ohos.calendarManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.CalendarKit.d.ts<br>差异内容：CalendarKit|kits/@kit.CalendarKit.d.ts|
