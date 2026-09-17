# Application Skill Development Guide Based on ArkTS Scripts

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=003f67010f789dc8bed9ff2524ae9ebbdab9c59f translatedAt=2026-08-25T13:14:45.897Z pushedAt=2026-08-27T12:40:00.531Z -->

## Overview

Starting from API version 26.0.0, Ability Kit supports exposing in-app business capabilities as Skills for invocation by the system intelligence agent. A Skill provides a declarative capability externalization mechanism: developers organize the business capabilities within an app that can be invoked externally into several capability units. Each unit consists of a description file (declaring its trigger scenarios, input parameter constraints, and return value contract) and an ArkTS entry script (bridging external invocations to the existing business implementation within the app), and is bound to the running context of a specified Ability through module configuration. At runtime, the system intelligence agent performs semantic matching of "intent-capability" based on the description file and converts the result into a natural language reply for the user.

Through Skills, developers can expose app capabilities to the system intelligence agent with a thin wrapper without modifying the existing business implementation; the system intelligence agent does not need to understand the internal implementation of each app and can complete scheduling relying solely on the unified declarative contract.
> **Note:**
>
> Only the Stage model is supported; the FA model is not available.

## API Description

The following are the main interfaces used for developing application Skills based on ArkTS scripts. For more interfaces and usage, see [@ohos.app.ability.scriptManager](../reference/apis-ability-kit/js-apis-app-ability-scriptManager.md).

| Interface Name | Description |
| -------- | -------- |
| [ExecuteResult](../reference/apis-ability-kit/js-apis-app-ability-scriptManager.md#executeresult) | Execution result of the ArkTS script. |
| [ArkTSScriptInfo](../reference/apis-ability-kit/js-apis-app-ability-scriptManager.md#arktsscriptinfo) | The first parameter of the app's ArkTS script entry function, used to receive the script context information passed by the system. |
| [completeArkTSScriptInApp(context: Context, requestCode: string, result: ExecuteResult): Promise\<void>](../reference/apis-ability-kit/js-apis-app-ability-scriptManager.md#scriptmanagercompletearktsscriptinapp) | Completes the execution of the app's ArkTS script and reports the execution result. Uses a Promise for asynchronous callback. |

## How to Develop

The following uses the "Music Assistant Skill (`example-org-music-assistant`)" as an example to demonstrate how to implement the capabilities of playing music by name (`playMusicByName`) and playback control (`controlPlayback`) in your own app through code development and encapsulation.

1. Create files and directories.

   Create files and directories under the module (`entry`) with the following structure:

   ```text
   Application/
   ├── AppScope/
   │   ├── app.json5
   │   └── resources/
   └── entry/
       ├── skills/                            <- [Fixed value] Root directory of all Skills in the current module
       │   └── example-org-music-assistant/   <- Skill name, which must be consistent with the name in SKILL.md. To prevent naming conflicts, it is recommended to use the company or organization name as a prefix.
       │       ├── scripts/                   <- [Fixed value] ETS script directory
       │       │   └── MusicSkill.ets         <- Skill entry script
       │       └── SKILL.md                   <- [Fixed value] Skill description file
       └── src/
           └── main/
               ├── ets/
               │   ├── entryability/
               │   │   └── EntryAbility.ets
               │   └── service/
               │       └── MusicPlayer.ets    <- In-app business service (called by the Skill entry script)
               ├── module.json5
               └── resources/
   ```

2. Configure the module.json5 file.

   Add the [skillProfiles tag](../quick-start/module-configuration-file.md#skillprofiles) under the `module` tag in `entry/src/main/module.json5` to register the Skill with the module.

   The sample Skill needs the network permission to access the cloud music list at runtime. Configure it under the requestPermissions tag within the `module` tag.

   <!-- @[module_skill](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/ArktsSkillDevelopmentGuide/entry/src/main/module.json5) -->

   ``` JSON5
   {
     "module": {
       // ...
       "skillProfiles": [
         {
           "name": "example-org-music-assistant",  // Skill name, which must be consistent with the name in SKILL.md
           "abilityName": "EntryAbility",          // Name of the component associated with this Skill
           "srcEntries": [                         // List of code file paths that implement the Skill
             "../../skills/example-org-music-assistant/scripts/MusicSkill.ets"
           ],
           "version": "1.0.0"
         }
       ],
   
       "requestPermissions": [  // List of permissions required for Skill execution
         { "name": "ohos.permission.INTERNET" }
       ],
       // ...
     }
   }
   ```

3. Implement the ArkTS script.

The ArkTS entry script (`MusicSkill.ets`) serves as a thin adaptation layer in the Skill invocation chain. It forwards the string parameters passed in by the system intelligence agent to the existing in-app business implementation, and returns the business execution result according to the contract declared in SKILL.md. The `MusicPlayer` it calls is an existing business implementation of the application and has no coupling with the Skill mechanism itself, so its internal logic is not elaborated in this section.

3.1 Import Skill-related interfaces.

The entry script needs to import `scriptManager` from `@kit.AbilityKit`, and also import the in-app business module to be bridged.

   <!-- @[music_skill_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/ArktsSkillDevelopmentGuide/entry/skills/example-org-music-assistant/scripts/MusicSkill.ets) -->

   ``` TypeScript
   
   import { scriptManager } from '@kit.AbilityKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   // Existing in-app business module
   import { MusicPlayer, Track, PlayResult } from '../../../src/main/ets/service/MusicPlayer';
   ```

3.2 Define the entry class skeleton.

The entry script exports a class using `export default`. Each `public async` method in the class corresponds to a capability declared in SKILL.md and must satisfy the following conventions:

- **Method name convention**: Must be exactly the same as the `functionName` in SKILL.md (in this example, `playMusicByName` and `controlPlayback`).

- **Method signature convention**: The first parameter type is fixed as [ArkTSScriptInfo](../reference/apis-ability-kit/js-apis-app-ability-scriptManager.md#arktsscriptinfo).

   <!-- @[music_skill](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/ArktsSkillDevelopmentGuide/entry/skills/example-org-music-assistant/scripts/MusicSkill.ets) -->

   ``` TypeScript
   export default class MusicSkill {
     // ...
     public async playMusicByName(info: scriptManager.ArkTSScriptInfo, ...argv: string[]): Promise<void> {
       /* See 3.3 to 3.5 */
       // ...
     }
   
     // ...
     public async controlPlayback(info: scriptManager.ArkTSScriptInfo, ...argv: string[]): Promise<void> {
       /* Same pattern as above */
       // ...
     }
   
     // ...
   }
   ```

   3.3 Parse and validate the input parameters.

   The first task of each capability method is to obtain parameters from `argv` by position and perform pre-validation against the `args` Schema in SKILL.md.

   <!-- @[music_skill_verify](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/ArktsSkillDevelopmentGuide/entry/skills/example-org-music-assistant/scripts/MusicSkill.ets) -->

   ``` TypeScript
   // Example 1: For the two optional parameters of playMusicByName, at least one must be non-empty.
   const songName: string = argv.length > 0 ? argv[0].trim() : '';
   const singer: string = argv.length > 1 ? argv[1].trim() : '';
   if (songName.length === 0 && singer.length === 0) {
     // Return a response through the ERR_INVALID_PARAMS branch (see 3.5) and do not proceed to the business logic.
         // ...
     return;
   }
       // ...
   
   // Example 2: For the enum value parameter of controlPlayback, perform a secondary validation using a trustlist.
   const action: string = argv.length > 0 ? argv[0].trim() : '';
   const validActions: string[] = ['pause', 'resume', 'next', 'previous'];
   if (!validActions.includes(action)) {
     // Return a response through the ERR_INVALID_PARAMS branch.
         // ...
     return;
   }
   ```

   3.4 Invoke the in-app business implementation.

   After validation passes, invoke the existing business interface to complete the actual task. The entry script does not carry business logic; it only acts as a "parameter adapter", reading the business return value and runtime exceptions, and mapping them to the different result branches declared in SKILL.md.

   <!-- @[music_skill_try](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/ArktsSkillDevelopmentGuide/entry/skills/example-org-music-assistant/scripts/MusicSkill.ets)  -->

   ``` TypeScript
   
   try {
     // Directly call the existing business API in the application.
     const playResult: PlayResult | null = MusicPlayer.searchAndPlay(songName, singer);
     // Map the business return value to the "success" or "miss" branch (see 3.5).
         // ...
   } catch (e) {
     // Map business exceptions uniformly to the ERR_INTERNAL branch (see 3.5).
     const err = e as BusinessError;
   // ...
   }
   ```

   3.5 Construct ExecuteResult according to the contract and return it.

   After the business execution is complete, encapsulate the result as [ExecuteResult](../reference/apis-ability-kit/js-apis-app-ability-scriptManager.md#executeresult) and return it to the system intelligence agent by calling [completeArkTSScriptInApp](../reference/apis-ability-kit/js-apis-app-ability-scriptManager.md#scriptmanagercompletearktsscriptinapp). The returned content should be consistent with the branch declared in the "execution return value" section of SKILL.md.

   <!-- @[music_skill_branch](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/ArktsSkillDevelopmentGuide/entry/skills/example-org-music-assistant/scripts/MusicSkill.ets) -->

   ``` TypeScript
   // Success branch example
   const first: Track = playResult.tracks[0];     
   const playingTrack: Record<string, Object> = {     
     'name': first.name,     
     'singer': first.singer,     
     'duration': first.duration     
   };
   const data: Record<string, Object> = {     
     'playingTrack': playingTrack,     
     'matchedCount': playResult.tracks.length     
   };
   const payload: Record<string, Object> = {
     'type': 'result',
     'status': 'success',
     'data': data
   };
   await this.report(info, { code: 0, result: payload });
         // ...
   
   // Failure branch example (using ERR_NOT_FOUND as an example)
   const payloadData: Record<string, Object> = {     
     'searchedKeywords': [] 
   };
   const payload: Record<string, Object> = {
     'type': 'result',
     'status': 'failed',
     'errCode': 'ERR_NOT_FOUND',
     'data': payloadData,
     'suggestion': `Could not find ${singer}${songName.length > 0 ? `'s "${songName}"` : ' related songs'}`
   };
   await this.report(info, { code: -1, result: payload });
   // ...
   
   // The only response exit: only wraps API calls and exception printing, and does not participate in result construction
   private async report(info: scriptManager.ArkTSScriptInfo, result: scriptManager.ExecuteResult): Promise<void> {
     try {
       await scriptManager.completeArkTSScriptInApp(info.context, info.requestCode, result);
     } catch (e) {
       const err = e as BusinessError;
       console.error(`completeArkTSScriptInApp failed, code: ${err.code}, message: ${err.message}`);
     }
   }
   ```

4. Write SKILL.md.

   SKILL.md is the declarative contract file of a Skill and the sole basis for the system intelligence to perform "intent-capability" matching. It mainly consists of three sections: "metadata -> trigger scenarios -> capability contracts".

   4.1 Write the metadata (YAML Front Matter).

   Use YAML Front Matter at the top of the file to declare `name` and `description`. Among them, `name` must be exactly consistent with the Skill directory name and `skillProfiles[].name` in `module.json5`; `description` should concisely describe the capability scope and serve as the key basis for the system intelligence to perform initial Skill filtering.

   ```text
   ---
   name: example-org-music-assistant
   description: Provides music search, playback, and playback control capabilities, responding to playback control commands such as "play a song", "skip", and "pause".
   ---
   ```

   4.2 Write the trigger scenarios.

   Use natural language to list typical utterances, and supplement the cases where the Skill should not be invoked to define the capability boundary and reduce false triggering. Typical utterances should cover multiple ways of expressing the corresponding capability, and boundary descriptions should cover adjacent intents that are easily confused.

   ```text
   ## Trigger scenarios

   Call this skill when the user clearly expresses **playing music** or **controlling the current playback**. Typical phrases:

   - "Play SingerA's 'SongA'"
   - "Play 'SongA'"
   - "Pause", "Resume"
   - "Skip", "Next", "Previous"

   When not to call:

   - The user says "Add this song to my favorites" — the intent is to modify the playlist; this skill only supports playback and playback control.
   - The user says "What concerts are on today" — the intent is to look up information, not playback.
   - The user does not clearly indicate playback (e.g., "This song is so good") — this is an emotional expression; no call is needed.
   - The user says "Turn down the volume" — the intent is system volume control, which should be handled by system capabilities.
   ```

   4.3 Write the "execution parameters" contract for each capability.

   Each capability corresponds to a `### Scenario N: capability name (functionName)` subsection. The "execution parameters" section must include a call example in `exec-cli` form and a JSON Schema constraint.

   The call example contains four core fields: `command` is fixed to `ohos-arkTSScript`; `skillName` must be consistent with `name` in SKILL.md; `scriptPath` is the entry script path relative to the Skill directory; `functionName` must strictly correspond to the public method name in MusicSkill.ets.

   ```bash
   exec-cli(command: ohos-arkTSScript --skillName 'example-org-music-assistant' --scriptPath 'scripts/MusicSkill.ets' --functionName 'playMusicByName' --args '{
       "arg1": "SongA",
       "arg2": "SingerA"
   }'
   )
   ```

    The core of the Schema lies in the `args` subobject, which defines the input parameter structure that the system intelligence agent can fill in. `playMusicByName` supports filling in either "song name" or "singer", so an `anyOf` constraint is used to ensure that at least one of them is included:

   ```json
   "args": {
     "type": "object",
     "properties": {
       "arg1": {
         "type": "string",
         "description": "Song name, such as *SongA*"
       },
       "arg2": {
         "type": "string",
         "description": "Singer name, such as SingerA"
       }
     },
     "anyOf": [
       { "required": ["arg1"] },
       { "required": ["arg2"] }
     ]
   }
   ```

   4.4 Write the "execution return value" contract for each capability.

   The "execution return value" section must first list all possible result examples (success + various failures), and then provide the overall JSON Schema constraint.

   Taking `playMusicByName` as an example, four groups of examples need to be listed one by one:

   ```json5
   // 1. Successfully played
   {
       "type": "result",
       "status": "success",
       "data": {
           "playingTrack": {
               "name": "SongA",
               "singer": "SingerA",
               "duration": 269
           },
           "matchedCount": 1
       }
   }
   ```

   ```json5
   // 2. Invalid input parameters
   {
       "type": "result",
       "status": "failed",
       "errCode": "ERR_INVALID_PARAMS",
       "errMsg": "songName and singer are both empty",
       "suggestion": "I didn't catch that. Which song would you like to listen to?"
   }
   ```

   ```json5
   // 3. No match found
   {
       "type": "result",
       "status": "failed",
       "errCode": "ERR_NOT_FOUND",
       "data": {
           "searchedKeywords": ["SongA", "SingerA"]
       },
       "suggestion": "Could not find *SongA* by SingerA"
   }
   ```

   ```json5
   // 4. Internal error
   {
       "type": "result",
       "status": "failed",
       "errCode": "ERR_INTERNAL",
       "errMsg": "network timeout",
       "suggestion": "Playback failed. Please try again later."
   }
   ```

The corresponding Schema defines common fields at the top level and enumerates the four branch forms above through `oneOf`:

   ```json5
   {
     "type": "object",
     "required": ["type", "status"],
     "properties": {
       "type":   { "type": "string", "const": "result" },
       "status": { "type": "string", "enum": ["success", "failed"] },
       "data":   { "type": "object" },
       "errCode": {
         "type": "string",
         "enum": ["ERR_INVALID_PARAMS", "ERR_NOT_FOUND", "ERR_INTERNAL"]
       },
       "errMsg":     { "type": "string", "minLength": 1 },
       "suggestion": { "type": "string", "minLength": 1 }
     },
     "oneOf": [
       /* Success:             requires data.playingTrack and data.matchedCount*/
       /* ERR_INVALID_PARAMS:  requires errMsg and suggestion*/
       /* ERR_NOT_FOUND:       requires data.searchedKeywords and suggestion*/
       /* ERR_INTERNAL:        requires errMsg and suggestion */
     ]
   }
   ```

<!--RP1--><!--RP1End-->

## Related Examples

For application Skill development, refer to the following related examples:

- [Music Assistant Skill Sample Project (example-org-music-assistant)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/bmsSample/ArktsSkillDevelopmentGuide)