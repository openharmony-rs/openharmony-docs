# 日程管理

<!--Kit: Calendar Kit-->
<!--Subsystem: Applications-->
<!--Owner: @qq_42718467-->
<!--Designer: @huangxinwei-->
<!--Tester: @z30055209-->
<!--Adviser: @ge-yafang-->

日程指特定的事件或者活动安排，日程管理即对这些事件、活动进行规划和控制，能更有效地利用相关资源、提高生产力和效率，使人们更好地管理时间和任务。

Calendar Kit中的日程[Event](../reference/apis-calendar-kit/js-apis-calendarManager.md#event)归属于某个对应的日历账户[Calendar](../reference/apis-calendar-kit/js-apis-calendarManager.md#calendar)，一个日历账户下可以有多个日程，一个日程只属于一个Calendar。

获取到日历账户对象之后，即可对该账户下的日程进行管理，包括日程的创建、删除、修改、查询等操作。在创建、修改日程时，支持对日程的标题、开始时间、结束时间、日程类型、日程地点、日程提醒时间、日程重复规则等相关信息进行设置，以便进行更丰富更有效的日程管理。

## 接口说明

以下是日程管理的相关接口，更多详细接口及使用请参考[@ohos.calendarManager](../reference/apis-calendar-kit/js-apis-calendarManager.md)。

| 接口名称                                      | 描述                                             |
| ----------------------------------------- |------------------------------------------------|
| getCalendarManager(context: Context): CalendarManager | 根据上下文获取CalendarManager对象，用于管理日历。               |
| createCalendar(calendarAccount: CalendarAccount): Promise\<Calendar> | 根据日历账户信息，创建一个Calendar对象，使用Promise异步回调。         |
| addEvent(event: Event): Promise\<number>  | 创建日程，入参Event不填日程id，使用Promise异步回调。              |
| editEvent(event: Event): Promise\<number> | 通过跳转到日程创建界面创建单个日程，入参Event不填日程id，使用Promise异步回调。 |
| deleteEvent(id: number): Promise\<void>   | 删除指定日程id的日程，使用Promise异步回调。                     |
| updateEvent(event: Event): Promise\<void> | 更新日程，使用Promise异步回调。                            |
| getEvents(eventFilter?: EventFilter, eventKey?: (keyof Event)[]): Promise\<Event[]> | 获取Calendar下符合查询条件的Event，使用Promise异步回调。         |

## 开发步骤

1. 导入相关依赖。

	<!-- @[calendarEvent_entryAbilityImport](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Calendar/CalendarEvent/entry/src/main/ets/entryability/EntryAbility.ets) -->
    
    ``` TypeScript
    import { abilityAccessCtrl, AbilityConstant, common, PermissionRequestResult, Permissions, UIAbility, Want } from '@kit.AbilityKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    import { calendarManager } from '@kit.CalendarKit';
    import { window } from '@kit.ArkUI';
    import { hilog } from '@kit.PerformanceAnalysisKit';
    ```

2. 申请权限。使用Calendar Kit时，需要在module.json5中声明申请读写日历日程所需的权限：`ohos.permission.READ_CALENDAR`和`ohos.permission.WRITE_CALENDAR`。具体指导可见[声明权限](../security/AccessToken/declare-permissions.md)。

3. 根据上下文获取日程管理器对象calendarMgr，用于对日历账户进行相关管理操作。推荐在`EntryAbility.ets`文件中进行操作。

	<!-- @[calendarEvent_entryAbility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Calendar/CalendarEvent/entry/src/main/ets/entryability/EntryAbility.ets) -->
    
    ``` TypeScript
    const DOMAIN = 0x0000;
    
    export let calendarMgr: calendarManager.CalendarManager | null = null;
    
    export let mContext: common.UIAbilityContext | null = null;
    
    export default class EntryAbility extends UIAbility {
      onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        hilog.info(DOMAIN, 'testTag', '%{public}s', "Ability onCreate");
      }
    
      onDestroy(): void {
        hilog.info(DOMAIN, 'testTag', '%{public}s', "Ability onDestroy");
      }
    
      onWindowStageCreate(windowStage: window.WindowStage): void {
        // Main window is created, set main page for this ability
        hilog.info(DOMAIN, 'testTag', '%{public}s', "Ability onWindowStageCreate");
        windowStage.loadContent('pages/Index', (err, data) => {
          if (err.code) {
            hilog.error(DOMAIN, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err));
            return;
          }
          hilog.info(DOMAIN, 'testTag', 'Succeeded in loading the content.');
        });
        mContext = this.context;
        const permissions: Permissions[] = ['ohos.permission.READ_CALENDAR', 'ohos.permission.WRITE_CALENDAR'];
        let atManager = abilityAccessCtrl.createAtManager();
        atManager.requestPermissionsFromUser(mContext, permissions).then((result: PermissionRequestResult) => {
          hilog.info(DOMAIN, 'testTag', 'get Permission success');
          calendarMgr = calendarManager.getCalendarManager(mContext);
        }).catch((error: BusinessError) => {
          hilog.error(DOMAIN, 'testTag', 'get Permission error, Cause: %{public}s', JSON.stringify(error));
        })
      }
    
      onWindowStageDestroy(): void {
        // Main window is destroyed, release UI related resources
        hilog.info(DOMAIN, 'testTag', '%{public}s', "Ability onWindowStageDestroy");
      }
    
      onForeground(): void {
        // Ability has brought to foreground
        hilog.info(DOMAIN, 'testTag', '%{public}s', "Ability onForeground");
      }
    
      onBackground(): void {
        // Ability has back to background
        hilog.info(DOMAIN, 'testTag', '%{public}s', "Ability onBackground");
      }
    }
    ```

4. 根据日历账户信息创建Calendar对象，用于进行日程管理。设置日历配置信息，可以根据需要打开日程提醒、设置日历账户颜色。

	<!-- @[calendarEvent_indexImport](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Calendar/CalendarEvent/entry/src/main/ets/pages/Index.ets) -->
    <!-- @[calendarEvent_createCalendar](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Calendar/CalendarEvent/entry/src/main/ets/pages/Index.ets) -->

5. 在当前日历账户下添加日历日程，注意入参中不需要填写日程id。

   创建日程时，支持设置日程的标题、开始时间、结束时间、日程类型、日程地点、日程提醒时间、日程重复规则等相关信息。

   日程创建成功后会返回一个日程id，作为日程的唯一标识，后续可按照日程id进行指定日程的更新或删除。

   目前支持以下两种方式来创建日程。

   方式一：可以在日历账户下通过`addEvent()`或`addEvents()`接口创建日程。其中可使用`addEvent()`接口创建单个日程，也可以使用`addEvents()`接口批量创建日程，此处以创建单个日程为例。

   方式二：在获取到日历管理器对象后，可通过`editEvent()`接口创建单个日程。调用此接口创建日程时，会跳转到日程创建页面，在日程创建页面进行相关操作完成日程的创建, `editEvent()`不支持自定义周期性日程创建。
   
   <!-- @[calendarEvent_eventParam](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Calendar/CalendarEvent/entry/src/main/ets/pages/Index.ets) -->
   <!-- @[calendarEvent_addEvent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Calendar/CalendarEvent/entry/src/main/ets/pages/Index.ets) -->

6. 按照日程id进行指定日程的更新，更新日程相关信息。

	<!-- @[calendarEvent_updateEvent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Calendar/CalendarEvent/entry/src/main/ets/pages/Index.ets) -->

7. 查询当前日历账户下的所有日程。由于涉及数据隐私安全，进行了权限管控的应用无法获取其他创建的日程信息。根据不同的查询条件和查询字段，返回不同的查询结果。

   当没有查询条件和查询字段时，可查询指定日历账户下的所有日程。
   <!-- @[calendarEvent_getEvents](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Calendar/CalendarEvent/entry/src/main/ets/pages/Index.ets) -->

   还支持根据日程id、日程开始和结束时间、日程标题等查询条件来查询日程。
   <!-- @[calendarEvent_getEvent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Calendar/CalendarEvent/entry/src/main/ets/pages/Index.ets) -->

8. 按照日程id进行指定日程的删除。可以通过`deleteEvent()`接口进行单个日程的删除，也可以通过`deleteEvents()`接口批量删除指定日程，此处以删除单个指定日程为例。

	<!-- @[calendarEvent_deleteEvent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Calendar/CalendarEvent/entry/src/main/ets/pages/Index.ets) -->
