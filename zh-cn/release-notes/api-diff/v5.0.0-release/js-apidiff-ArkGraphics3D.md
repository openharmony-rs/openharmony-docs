| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：export interface SceneResourceParameters<br>差异内容：export interface SceneResourceParameters|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：SceneResourceParameters；<br>API声明：name: string;<br>差异内容：name: string;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：SceneResourceParameters；<br>API声明：uri?: ResourceStr;<br>差异内容：uri?: ResourceStr;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SceneNodeParameters<br>差异内容：export interface SceneNodeParameters|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：SceneNodeParameters；<br>API声明：name: string;<br>差异内容：name: string;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：SceneNodeParameters；<br>API声明：path?: string;<br>差异内容：path?: string;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SceneResourceFactory<br>差异内容：export interface SceneResourceFactory|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：SceneResourceFactory；<br>API声明：createCamera(params: SceneNodeParameters): Promise\<Camera>;<br>差异内容：createCamera(params: SceneNodeParameters): Promise\<Camera>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：SceneResourceFactory；<br>API声明：createLight(params: SceneNodeParameters, lightType: LightType): Promise\<Light>;<br>差异内容：createLight(params: SceneNodeParameters, lightType: LightType): Promise\<Light>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：SceneResourceFactory；<br>API声明：createNode(params: SceneNodeParameters): Promise\<Node>;<br>差异内容：createNode(params: SceneNodeParameters): Promise\<Node>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：SceneResourceFactory；<br>API声明：createMaterial(params: SceneResourceParameters, materialType: MaterialType): Promise\<Material>;<br>差异内容：createMaterial(params: SceneResourceParameters, materialType: MaterialType): Promise\<Material>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：SceneResourceFactory；<br>API声明：createShader(params: SceneResourceParameters): Promise\<Shader>;<br>差异内容：createShader(params: SceneResourceParameters): Promise\<Shader>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：SceneResourceFactory；<br>API声明：createImage(params: SceneResourceParameters): Promise\<Image>;<br>差异内容：createImage(params: SceneResourceParameters): Promise\<Image>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：SceneResourceFactory；<br>API声明：createEnvironment(params: SceneResourceParameters): Promise\<Environment>;<br>差异内容：createEnvironment(params: SceneResourceParameters): Promise\<Environment>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：global；<br>API声明：export class Scene<br>差异内容：export class Scene|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：Scene；<br>API声明：static load(uri?: ResourceStr): Promise\<Scene>;<br>差异内容：static load(uri?: ResourceStr): Promise\<Scene>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：Scene；<br>API声明：environment: Environment;<br>差异内容：environment: Environment;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：Scene；<br>API声明：readonly animations: Animation[];<br>差异内容：readonly animations: Animation[];|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：Scene；<br>API声明：readonly root: Node \| null;<br>差异内容：readonly root: Node \| null;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：Scene；<br>API声明：getNodeByPath(path: string, type?: NodeType): Node \| null;<br>差异内容：getNodeByPath(path: string, type?: NodeType): Node \| null;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：Scene；<br>API声明：getResourceFactory(): SceneResourceFactory;<br>差异内容：getResourceFactory(): SceneResourceFactory;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：Scene；<br>API声明：destroy(): void;<br>差异内容：destroy(): void;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface LayerMask<br>差异内容：export interface LayerMask|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：LayerMask；<br>API声明：getEnabled(index: number): boolean;<br>差异内容：getEnabled(index: number): boolean;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：LayerMask；<br>API声明：setEnabled(index: number, enabled: boolean): void;<br>差异内容：setEnabled(index: number, enabled: boolean): void;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum NodeType<br>差异内容：export enum NodeType|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：NodeType；<br>API声明：NODE = 1<br>差异内容：NODE = 1|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：NodeType；<br>API声明：GEOMETRY = 2<br>差异内容：GEOMETRY = 2|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：NodeType；<br>API声明：CAMERA = 3<br>差异内容：CAMERA = 3|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：NodeType；<br>API声明：LIGHT = 4<br>差异内容：LIGHT = 4|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Container<br>差异内容：export interface Container|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Container；<br>API声明：append(item: T): void;<br>差异内容：append(item: T): void;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Container；<br>API声明：insertAfter(item: T, sibling: T \| null): void;<br>差异内容：insertAfter(item: T, sibling: T \| null): void;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Container；<br>API声明：remove(item: T): void;<br>差异内容：remove(item: T): void;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Container；<br>API声明：get(index: number): T \| null;<br>差异内容：get(index: number): T \| null;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Container；<br>API声明：clear(): void;<br>差异内容：clear(): void;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Container；<br>API声明：count(): number;<br>差异内容：count(): number;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Node<br>差异内容：export interface Node|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Node；<br>API声明：position: Position3;<br>差异内容：position: Position3;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Node；<br>API声明：rotation: Quaternion;<br>差异内容：rotation: Quaternion;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Node；<br>API声明：scale: Scale3;<br>差异内容：scale: Scale3;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Node；<br>API声明：visible: boolean;<br>差异内容：visible: boolean;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Node；<br>API声明：readonly nodeType: NodeType;<br>差异内容：readonly nodeType: NodeType;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Node；<br>API声明：readonly layerMask: LayerMask;<br>差异内容：readonly layerMask: LayerMask;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Node；<br>API声明：readonly path: string;<br>差异内容：readonly path: string;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Node；<br>API声明：readonly parent: Node \| null;<br>差异内容：readonly parent: Node \| null;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Node；<br>API声明：getNodeByPath(path: string): Node \| null;<br>差异内容：getNodeByPath(path: string): Node \| null;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Node；<br>API声明：readonly children: Container\<Node>;<br>差异内容：readonly children: Container\<Node>;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Geometry<br>差异内容：export interface Geometry|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Geometry；<br>API声明：readonly mesh: Mesh;<br>差异内容：readonly mesh: Mesh;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum LightType<br>差异内容：export enum LightType|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：LightType；<br>API声明：DIRECTIONAL = 1<br>差异内容：DIRECTIONAL = 1|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：LightType；<br>API声明：SPOT = 2<br>差异内容：SPOT = 2|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Light<br>差异内容：export interface Light|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Light；<br>API声明：readonly lightType: LightType;<br>差异内容：readonly lightType: LightType;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Light；<br>API声明：color: Color;<br>差异内容：color: Color;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Light；<br>API声明：intensity: number;<br>差异内容：intensity: number;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Light；<br>API声明：shadowEnabled: boolean;<br>差异内容：shadowEnabled: boolean;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Light；<br>API声明：enabled: boolean;<br>差异内容：enabled: boolean;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SpotLight<br>差异内容：export interface SpotLight|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface DirectionalLight<br>差异内容：export interface DirectionalLight|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Camera<br>差异内容：export interface Camera|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Camera；<br>API声明：fov: number;<br>差异内容：fov: number;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Camera；<br>API声明：nearPlane: number;<br>差异内容：nearPlane: number;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Camera；<br>API声明：farPlane: number;<br>差异内容：farPlane: number;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Camera；<br>API声明：enabled: boolean;<br>差异内容：enabled: boolean;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Camera；<br>API声明：postProcess: PostProcessSettings \| null;<br>差异内容：postProcess: PostProcessSettings \| null;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Camera；<br>API声明：clearColor: Color \| null;<br>差异内容：clearColor: Color \| null;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum ToneMappingType<br>差异内容：export enum ToneMappingType|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：ToneMappingType；<br>API声明：ACES = 0<br>差异内容：ACES = 0|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：ToneMappingType；<br>API声明：ACES_2020 = 1<br>差异内容：ACES_2020 = 1|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：ToneMappingType；<br>API声明：FILMIC = 2<br>差异内容：FILMIC = 2|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface ToneMappingSettings<br>差异内容：export interface ToneMappingSettings|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：ToneMappingSettings；<br>API声明：type?: ToneMappingType;<br>差异内容：type?: ToneMappingType;|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：ToneMappingSettings；<br>API声明：exposure?: number;<br>差异内容：exposure?: number;|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface PostProcessSettings<br>差异内容：export interface PostProcessSettings|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：PostProcessSettings；<br>API声明：toneMapping?: ToneMappingSettings;<br>差异内容：toneMapping?: ToneMappingSettings;|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum SceneResourceType<br>差异内容：export enum SceneResourceType|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SceneResourceType；<br>API声明：UNKNOWN = 0<br>差异内容：UNKNOWN = 0|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SceneResourceType；<br>API声明：NODE = 1<br>差异内容：NODE = 1|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SceneResourceType；<br>API声明：ENVIRONMENT = 2<br>差异内容：ENVIRONMENT = 2|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SceneResourceType；<br>API声明：MATERIAL = 3<br>差异内容：MATERIAL = 3|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SceneResourceType；<br>API声明：MESH = 4<br>差异内容：MESH = 4|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SceneResourceType；<br>API声明：ANIMATION = 5<br>差异内容：ANIMATION = 5|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SceneResourceType；<br>API声明：SHADER = 6<br>差异内容：SHADER = 6|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SceneResourceType；<br>API声明：IMAGE = 7<br>差异内容：IMAGE = 7|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SceneResource<br>差异内容：export interface SceneResource|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SceneResource；<br>API声明：name: string;<br>差异内容：name: string;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SceneResource；<br>API声明：readonly resourceType: SceneResourceType;<br>差异内容：readonly resourceType: SceneResourceType;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SceneResource；<br>API声明：readonly uri?: ResourceStr;<br>差异内容：readonly uri?: ResourceStr;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SceneResource；<br>API声明：destroy(): void;<br>差异内容：destroy(): void;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Shader<br>差异内容：export interface Shader|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Shader；<br>API声明：readonly inputs: Record\<string, number \| Vec2 \| Vec3 \| Vec4 \| Image>;<br>差异内容：readonly inputs: Record\<string, number \| Vec2 \| Vec3 \| Vec4 \| Image>;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum MaterialType<br>差异内容：export enum MaterialType|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：MaterialType；<br>API声明：SHADER = 1<br>差异内容：SHADER = 1|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Material<br>差异内容：export interface Material|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Material；<br>API声明：readonly materialType: MaterialType;<br>差异内容：readonly materialType: MaterialType;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface ShaderMaterial<br>差异内容：export interface ShaderMaterial|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：ShaderMaterial；<br>API声明：colorShader?: Shader;<br>差异内容：colorShader?: Shader;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SubMesh<br>差异内容：export interface SubMesh|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SubMesh；<br>API声明：name: string;<br>差异内容：name: string;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SubMesh；<br>API声明：material: Material;<br>差异内容：material: Material;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SubMesh；<br>API声明：readonly aabb: Aabb;<br>差异内容：readonly aabb: Aabb;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Mesh<br>差异内容：export interface Mesh|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Mesh；<br>API声明：readonly subMeshes: SubMesh[];<br>差异内容：readonly subMeshes: SubMesh[];|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Mesh；<br>API声明：readonly aabb: Aabb;<br>差异内容：readonly aabb: Aabb;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Mesh；<br>API声明：materialOverride?: Material;<br>差异内容：materialOverride?: Material;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Animation<br>差异内容：export interface Animation|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Animation；<br>API声明：enabled: boolean;<br>差异内容：enabled: boolean;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Animation；<br>API声明：readonly duration: number;<br>差异内容：readonly duration: number;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Animation；<br>API声明：readonly running: boolean;<br>差异内容：readonly running: boolean;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Animation；<br>API声明：readonly progress: number;<br>差异内容：readonly progress: number;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Animation；<br>API声明：onFinished(callback: Callback\<void>): void;<br>差异内容：onFinished(callback: Callback\<void>): void;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Animation；<br>API声明：onStarted(callback: Callback\<void>): void;<br>差异内容：onStarted(callback: Callback\<void>): void;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Animation；<br>API声明：pause(): void;<br>差异内容：pause(): void;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Animation；<br>API声明：restart(): void;<br>差异内容：restart(): void;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Animation；<br>API声明：seek(position: number): void;<br>差异内容：seek(position: number): void;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Animation；<br>API声明：start(): void;<br>差异内容：start(): void;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Animation；<br>API声明：stop(): void;<br>差异内容：stop(): void;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Animation；<br>API声明：finish(): void;<br>差异内容：finish(): void;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum EnvironmentBackgroundType<br>差异内容：export enum EnvironmentBackgroundType|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：EnvironmentBackgroundType；<br>API声明：BACKGROUND_NONE = 0<br>差异内容：BACKGROUND_NONE = 0|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：EnvironmentBackgroundType；<br>API声明：BACKGROUND_IMAGE = 1<br>差异内容：BACKGROUND_IMAGE = 1|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：EnvironmentBackgroundType；<br>API声明：BACKGROUND_CUBEMAP = 2<br>差异内容：BACKGROUND_CUBEMAP = 2|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：EnvironmentBackgroundType；<br>API声明：BACKGROUND_EQUIRECTANGULAR = 3<br>差异内容：BACKGROUND_EQUIRECTANGULAR = 3|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Environment<br>差异内容：export interface Environment|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Environment；<br>API声明：backgroundType: EnvironmentBackgroundType;<br>差异内容：backgroundType: EnvironmentBackgroundType;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Environment；<br>API声明：indirectDiffuseFactor: Vec4;<br>差异内容：indirectDiffuseFactor: Vec4;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Environment；<br>API声明：indirectSpecularFactor: Vec4;<br>差异内容：indirectSpecularFactor: Vec4;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Environment；<br>API声明：environmentMapFactor: Vec4;<br>差异内容：environmentMapFactor: Vec4;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Environment；<br>API声明：environmentImage?: Image \| null;<br>差异内容：environmentImage?: Image \| null;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Environment；<br>API声明：radianceImage?: Image \| null;<br>差异内容：radianceImage?: Image \| null;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Environment；<br>API声明：irradianceCoefficients?: Vec3[];<br>差异内容：irradianceCoefficients?: Vec3[];|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Image<br>差异内容：export interface Image|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Image；<br>API声明：readonly width: number;<br>差异内容：readonly width: number;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Image；<br>API声明：readonly height: number;<br>差异内容：readonly height: number;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Vec2<br>差异内容：export interface Vec2|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Vec2；<br>API声明：x: number;<br>差异内容：x: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Vec2；<br>API声明：y: number;<br>差异内容：y: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Vec3<br>差异内容：export interface Vec3|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Vec3；<br>API声明：x: number;<br>差异内容：x: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Vec3；<br>API声明：y: number;<br>差异内容：y: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Vec3；<br>API声明：z: number;<br>差异内容：z: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Vec4<br>差异内容：export interface Vec4|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Vec4；<br>API声明：x: number;<br>差异内容：x: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Vec4；<br>API声明：y: number;<br>差异内容：y: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Vec4；<br>API声明：z: number;<br>差异内容：z: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Vec4；<br>API声明：w: number;<br>差异内容：w: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Quaternion<br>差异内容：export interface Quaternion|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Quaternion；<br>API声明：x: number;<br>差异内容：x: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Quaternion；<br>API声明：y: number;<br>差异内容：y: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Quaternion；<br>API声明：z: number;<br>差异内容：z: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Quaternion；<br>API声明：w: number;<br>差异内容：w: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Aabb<br>差异内容：export interface Aabb|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Aabb；<br>API声明：aabbMin: Vec3;<br>差异内容：aabbMin: Vec3;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Aabb；<br>API声明：aabbMax: Vec3;<br>差异内容：aabbMax: Vec3;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Color<br>差异内容：export interface Color|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Color；<br>API声明：r: number;<br>差异内容：r: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Color；<br>API声明：g: number;<br>差异内容：g: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Color；<br>API声明：b: number;<br>差异内容：b: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Color；<br>API声明：a: number;<br>差异内容：a: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Rect<br>差异内容：export interface Rect|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Rect；<br>API声明：x: number;<br>差异内容：x: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Rect；<br>API声明：y: number;<br>差异内容：y: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Rect；<br>API声明：width: number;<br>差异内容：width: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：Rect；<br>API声明：height: number;<br>差异内容：height: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export type Position3 = Vec3;<br>差异内容：export type Position3 = Vec3;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export type Rotation3 = Vec3;<br>差异内容：export type Rotation3 = Vec3;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export type Scale3 = Vec3;<br>差异内容：export type Scale3 = Vec3;|api/graphics3d/SceneTypes.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.graphics.scene.d.ts<br>差异内容：ArkGraphics3D|api/@ohos.graphics.scene.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\graphics3d\Scene.d.ts<br>差异内容：ArkGraphics3D|api/graphics3d/Scene.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\graphics3d\SceneNodes.d.ts<br>差异内容：ArkGraphics3D|api/graphics3d/SceneNodes.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\graphics3d\ScenePostProcessSettings.d.ts<br>差异内容：ArkGraphics3D|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\graphics3d\SceneResources.d.ts<br>差异内容：ArkGraphics3D|api/graphics3d/SceneResources.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\graphics3d\SceneTypes.d.ts<br>差异内容：ArkGraphics3D|api/graphics3d/SceneTypes.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.ArkGraphics3D.d.ts<br>差异内容：ArkGraphics3D|kits/@kit.ArkGraphics3D.d.ts|
