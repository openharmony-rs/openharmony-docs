| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API|NA|Class name: global;<br>API declaration: export interface SceneResourceParameters<br>Differences: export interface SceneResourceParameters|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: SceneResourceParameters;<br>API declaration: name: string;<br>Differences: name: string;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: SceneResourceParameters;<br>API declaration: uri?: ResourceStr;<br>Differences: uri?: ResourceStr;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface SceneNodeParameters<br>Differences: export interface SceneNodeParameters|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: SceneNodeParameters;<br>API declaration: name: string;<br>Differences: name: string;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: SceneNodeParameters;<br>API declaration: path?: string;<br>Differences: path?: string;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface SceneResourceFactory<br>Differences: export interface SceneResourceFactory|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: SceneResourceFactory;<br>API declaration: createCamera(params: SceneNodeParameters): Promise\<Camera>;<br>Differences: createCamera(params: SceneNodeParameters): Promise\<Camera>;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: SceneResourceFactory;<br>API declaration: createLight(params: SceneNodeParameters, lightType: LightType): Promise\<Light>;<br>Differences: createLight(params: SceneNodeParameters, lightType: LightType): Promise\<Light>;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: SceneResourceFactory;<br>API declaration: createNode(params: SceneNodeParameters): Promise\<Node>;<br>Differences: createNode(params: SceneNodeParameters): Promise\<Node>;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: SceneResourceFactory;<br>API declaration: createMaterial(params: SceneResourceParameters, materialType: MaterialType): Promise\<Material>;<br>Differences: createMaterial(params: SceneResourceParameters, materialType: MaterialType): Promise\<Material>;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: SceneResourceFactory;<br>API declaration: createShader(params: SceneResourceParameters): Promise\<Shader>;<br>Differences: createShader(params: SceneResourceParameters): Promise\<Shader>;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: SceneResourceFactory;<br>API declaration: createImage(params: SceneResourceParameters): Promise\<Image>;<br>Differences: createImage(params: SceneResourceParameters): Promise\<Image>;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: SceneResourceFactory;<br>API declaration: createEnvironment(params: SceneResourceParameters): Promise\<Environment>;<br>Differences: createEnvironment(params: SceneResourceParameters): Promise\<Environment>;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: global;<br>API declaration: export class Scene<br>Differences: export class Scene|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: Scene;<br>API declaration: static load(uri?: ResourceStr): Promise\<Scene>;<br>Differences: static load(uri?: ResourceStr): Promise\<Scene>;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: Scene;<br>API declaration: environment: Environment;<br>Differences: environment: Environment;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: Scene;<br>API declaration: readonly animations: Animation[];<br>Differences: readonly animations: Animation[];|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: Scene;<br>API declaration: readonly root: Node \| null;<br>Differences: readonly root: Node \| null;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: Scene;<br>API declaration: getNodeByPath(path: string, type?: NodeType): Node \| null;<br>Differences: getNodeByPath(path: string, type?: NodeType): Node \| null;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: Scene;<br>API declaration: getResourceFactory(): SceneResourceFactory;<br>Differences: getResourceFactory(): SceneResourceFactory;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: Scene;<br>API declaration: destroy(): void;<br>Differences: destroy(): void;|api/graphics3d/Scene.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface LayerMask<br>Differences: export interface LayerMask|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: LayerMask;<br>API declaration: getEnabled(index: number): boolean;<br>Differences: getEnabled(index: number): boolean;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: LayerMask;<br>API declaration: setEnabled(index: number, enabled: boolean): void;<br>Differences: setEnabled(index: number, enabled: boolean): void;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export enum NodeType<br>Differences: export enum NodeType|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: NodeType;<br>API declaration: NODE = 1<br>Differences: NODE = 1|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: NodeType;<br>API declaration: GEOMETRY = 2<br>Differences: GEOMETRY = 2|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: NodeType;<br>API declaration: CAMERA = 3<br>Differences: CAMERA = 3|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: NodeType;<br>API declaration: LIGHT = 4<br>Differences: LIGHT = 4|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Container<br>Differences: export interface Container|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Container;<br>API declaration: append(item: T): void;<br>Differences: append(item: T): void;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Container;<br>API declaration: insertAfter(item: T, sibling: T \| null): void;<br>Differences: insertAfter(item: T, sibling: T \| null): void;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Container;<br>API declaration: remove(item: T): void;<br>Differences: remove(item: T): void;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Container;<br>API declaration: get(index: number): T \| null;<br>Differences: get(index: number): T \| null;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Container;<br>API declaration: clear(): void;<br>Differences: clear(): void;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Container;<br>API declaration: count(): number;<br>Differences: count(): number;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Node<br>Differences: export interface Node|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Node;<br>API declaration: position: Position3;<br>Differences: position: Position3;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Node;<br>API declaration: rotation: Quaternion;<br>Differences: rotation: Quaternion;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Node;<br>API declaration: scale: Scale3;<br>Differences: scale: Scale3;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Node;<br>API declaration: visible: boolean;<br>Differences: visible: boolean;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Node;<br>API declaration: readonly nodeType: NodeType;<br>Differences: readonly nodeType: NodeType;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Node;<br>API declaration: readonly layerMask: LayerMask;<br>Differences: readonly layerMask: LayerMask;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Node;<br>API declaration: readonly path: string;<br>Differences: readonly path: string;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Node;<br>API declaration: readonly parent: Node \| null;<br>Differences: readonly parent: Node \| null;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Node;<br>API declaration: getNodeByPath(path: string): Node \| null;<br>Differences: getNodeByPath(path: string): Node \| null;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Node;<br>API declaration: readonly children: Container\<Node>;<br>Differences: readonly children: Container\<Node>;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Geometry<br>Differences: export interface Geometry|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Geometry;<br>API declaration: readonly mesh: Mesh;<br>Differences: readonly mesh: Mesh;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export enum LightType<br>Differences: export enum LightType|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: LightType;<br>API declaration: DIRECTIONAL = 1<br>Differences: DIRECTIONAL = 1|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: LightType;<br>API declaration: SPOT = 2<br>Differences: SPOT = 2|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Light<br>Differences: export interface Light|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Light;<br>API declaration: readonly lightType: LightType;<br>Differences: readonly lightType: LightType;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Light;<br>API declaration: color: Color;<br>Differences: color: Color;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Light;<br>API declaration: intensity: number;<br>Differences: intensity: number;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Light;<br>API declaration: shadowEnabled: boolean;<br>Differences: shadowEnabled: boolean;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Light;<br>API declaration: enabled: boolean;<br>Differences: enabled: boolean;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface SpotLight<br>Differences: export interface SpotLight|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface DirectionalLight<br>Differences: export interface DirectionalLight|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Camera<br>Differences: export interface Camera|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Camera;<br>API declaration: fov: number;<br>Differences: fov: number;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Camera;<br>API declaration: nearPlane: number;<br>Differences: nearPlane: number;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Camera;<br>API declaration: farPlane: number;<br>Differences: farPlane: number;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Camera;<br>API declaration: enabled: boolean;<br>Differences: enabled: boolean;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Camera;<br>API declaration: postProcess: PostProcessSettings \| null;<br>Differences: postProcess: PostProcessSettings \| null;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: Camera;<br>API declaration: clearColor: Color \| null;<br>Differences: clearColor: Color \| null;|api/graphics3d/SceneNodes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export enum ToneMappingType<br>Differences: export enum ToneMappingType|api/graphics3d/ScenePostProcessSettings.d.ts|
|New API|NA|Class name: ToneMappingType;<br>API declaration: ACES = 0<br>Differences: ACES = 0|api/graphics3d/ScenePostProcessSettings.d.ts|
|New API|NA|Class name: ToneMappingType;<br>API declaration: ACES_2020 = 1<br>Differences: ACES_2020 = 1|api/graphics3d/ScenePostProcessSettings.d.ts|
|New API|NA|Class name: ToneMappingType;<br>API declaration: FILMIC = 2<br>Differences: FILMIC = 2|api/graphics3d/ScenePostProcessSettings.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface ToneMappingSettings<br>Differences: export interface ToneMappingSettings|api/graphics3d/ScenePostProcessSettings.d.ts|
|New API|NA|Class name: ToneMappingSettings;<br>API declaration: type?: ToneMappingType;<br>Differences: type?: ToneMappingType;|api/graphics3d/ScenePostProcessSettings.d.ts|
|New API|NA|Class name: ToneMappingSettings;<br>API declaration: exposure?: number;<br>Differences: exposure?: number;|api/graphics3d/ScenePostProcessSettings.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface PostProcessSettings<br>Differences: export interface PostProcessSettings|api/graphics3d/ScenePostProcessSettings.d.ts|
|New API|NA|Class name: PostProcessSettings;<br>API declaration: toneMapping?: ToneMappingSettings;<br>Differences: toneMapping?: ToneMappingSettings;|api/graphics3d/ScenePostProcessSettings.d.ts|
|New API|NA|Class name: global;<br>API declaration: export enum SceneResourceType<br>Differences: export enum SceneResourceType|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: SceneResourceType;<br>API declaration: UNKNOWN = 0<br>Differences: UNKNOWN = 0|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: SceneResourceType;<br>API declaration: NODE = 1<br>Differences: NODE = 1|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: SceneResourceType;<br>API declaration: ENVIRONMENT = 2<br>Differences: ENVIRONMENT = 2|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: SceneResourceType;<br>API declaration: MATERIAL = 3<br>Differences: MATERIAL = 3|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: SceneResourceType;<br>API declaration: MESH = 4<br>Differences: MESH = 4|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: SceneResourceType;<br>API declaration: ANIMATION = 5<br>Differences: ANIMATION = 5|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: SceneResourceType;<br>API declaration: SHADER = 6<br>Differences: SHADER = 6|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: SceneResourceType;<br>API declaration: IMAGE = 7<br>Differences: IMAGE = 7|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface SceneResource<br>Differences: export interface SceneResource|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: SceneResource;<br>API declaration: name: string;<br>Differences: name: string;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: SceneResource;<br>API declaration: readonly resourceType: SceneResourceType;<br>Differences: readonly resourceType: SceneResourceType;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: SceneResource;<br>API declaration: readonly uri?: ResourceStr;<br>Differences: readonly uri?: ResourceStr;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: SceneResource;<br>API declaration: destroy(): void;<br>Differences: destroy(): void;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Shader<br>Differences: export interface Shader|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Shader;<br>API declaration: readonly inputs: Record\<string, number \| Vec2 \| Vec3 \| Vec4 \| Image>;<br>Differences: readonly inputs: Record\<string, number \| Vec2 \| Vec3 \| Vec4 \| Image>;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: global;<br>API declaration: export enum MaterialType<br>Differences: export enum MaterialType|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: MaterialType;<br>API declaration: SHADER = 1<br>Differences: SHADER = 1|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Material<br>Differences: export interface Material|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Material;<br>API declaration: readonly materialType: MaterialType;<br>Differences: readonly materialType: MaterialType;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface ShaderMaterial<br>Differences: export interface ShaderMaterial|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: ShaderMaterial;<br>API declaration: colorShader?: Shader;<br>Differences: colorShader?: Shader;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface SubMesh<br>Differences: export interface SubMesh|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: SubMesh;<br>API declaration: name: string;<br>Differences: name: string;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: SubMesh;<br>API declaration: material: Material;<br>Differences: material: Material;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: SubMesh;<br>API declaration: readonly aabb: Aabb;<br>Differences: readonly aabb: Aabb;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Mesh<br>Differences: export interface Mesh|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Mesh;<br>API declaration: readonly subMeshes: SubMesh[];<br>Differences: readonly subMeshes: SubMesh[];|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Mesh;<br>API declaration: readonly aabb: Aabb;<br>Differences: readonly aabb: Aabb;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Mesh;<br>API declaration: materialOverride?: Material;<br>Differences: materialOverride?: Material;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Animation<br>Differences: export interface Animation|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Animation;<br>API declaration: enabled: boolean;<br>Differences: enabled: boolean;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Animation;<br>API declaration: readonly duration: number;<br>Differences: readonly duration: number;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Animation;<br>API declaration: readonly running: boolean;<br>Differences: readonly running: boolean;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Animation;<br>API declaration: readonly progress: number;<br>Differences: readonly progress: number;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Animation;<br>API declaration: onFinished(callback: Callback\<void>): void;<br>Differences: onFinished(callback: Callback\<void>): void;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Animation;<br>API declaration: onStarted(callback: Callback\<void>): void;<br>Differences: onStarted(callback: Callback\<void>): void;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Animation;<br>API declaration: pause(): void;<br>Differences: pause(): void;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Animation;<br>API declaration: restart(): void;<br>Differences: restart(): void;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Animation;<br>API declaration: seek(position: number): void;<br>Differences: seek(position: number): void;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Animation;<br>API declaration: start(): void;<br>Differences: start(): void;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Animation;<br>API declaration: stop(): void;<br>Differences: stop(): void;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Animation;<br>API declaration: finish(): void;<br>Differences: finish(): void;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: global;<br>API declaration: export enum EnvironmentBackgroundType<br>Differences: export enum EnvironmentBackgroundType|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: EnvironmentBackgroundType;<br>API declaration: BACKGROUND_NONE = 0<br>Differences: BACKGROUND_NONE = 0|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: EnvironmentBackgroundType;<br>API declaration: BACKGROUND_IMAGE = 1<br>Differences: BACKGROUND_IMAGE = 1|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: EnvironmentBackgroundType;<br>API declaration: BACKGROUND_CUBEMAP = 2<br>Differences: BACKGROUND_CUBEMAP = 2|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: EnvironmentBackgroundType;<br>API declaration: BACKGROUND_EQUIRECTANGULAR = 3<br>Differences: BACKGROUND_EQUIRECTANGULAR = 3|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Environment<br>Differences: export interface Environment|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Environment;<br>API declaration: backgroundType: EnvironmentBackgroundType;<br>Differences: backgroundType: EnvironmentBackgroundType;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Environment;<br>API declaration: indirectDiffuseFactor: Vec4;<br>Differences: indirectDiffuseFactor: Vec4;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Environment;<br>API declaration: indirectSpecularFactor: Vec4;<br>Differences: indirectSpecularFactor: Vec4;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Environment;<br>API declaration: environmentMapFactor: Vec4;<br>Differences: environmentMapFactor: Vec4;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Environment;<br>API declaration: environmentImage?: Image \| null;<br>Differences: environmentImage?: Image \| null;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Environment;<br>API declaration: radianceImage?: Image \| null;<br>Differences: radianceImage?: Image \| null;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Environment;<br>API declaration: irradianceCoefficients?: Vec3[];<br>Differences: irradianceCoefficients?: Vec3[];|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Image<br>Differences: export interface Image|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Image;<br>API declaration: readonly width: number;<br>Differences: readonly width: number;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: Image;<br>API declaration: readonly height: number;<br>Differences: readonly height: number;|api/graphics3d/SceneResources.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Vec2<br>Differences: export interface Vec2|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Vec2;<br>API declaration: x: number;<br>Differences: x: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Vec2;<br>API declaration: y: number;<br>Differences: y: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Vec3<br>Differences: export interface Vec3|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Vec3;<br>API declaration: x: number;<br>Differences: x: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Vec3;<br>API declaration: y: number;<br>Differences: y: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Vec3;<br>API declaration: z: number;<br>Differences: z: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Vec4<br>Differences: export interface Vec4|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Vec4;<br>API declaration: x: number;<br>Differences: x: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Vec4;<br>API declaration: y: number;<br>Differences: y: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Vec4;<br>API declaration: z: number;<br>Differences: z: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Vec4;<br>API declaration: w: number;<br>Differences: w: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Quaternion<br>Differences: export interface Quaternion|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Quaternion;<br>API declaration: x: number;<br>Differences: x: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Quaternion;<br>API declaration: y: number;<br>Differences: y: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Quaternion;<br>API declaration: z: number;<br>Differences: z: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Quaternion;<br>API declaration: w: number;<br>Differences: w: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Aabb<br>Differences: export interface Aabb|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Aabb;<br>API declaration: aabbMin: Vec3;<br>Differences: aabbMin: Vec3;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Aabb;<br>API declaration: aabbMax: Vec3;<br>Differences: aabbMax: Vec3;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Color<br>Differences: export interface Color|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Color;<br>API declaration: r: number;<br>Differences: r: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Color;<br>API declaration: g: number;<br>Differences: g: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Color;<br>API declaration: b: number;<br>Differences: b: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Color;<br>API declaration: a: number;<br>Differences: a: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface Rect<br>Differences: export interface Rect|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Rect;<br>API declaration: x: number;<br>Differences: x: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Rect;<br>API declaration: y: number;<br>Differences: y: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Rect;<br>API declaration: width: number;<br>Differences: width: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: Rect;<br>API declaration: height: number;<br>Differences: height: number;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export type Position3 = Vec3;<br>Differences: export type Position3 = Vec3;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export type Rotation3 = Vec3;<br>Differences: export type Rotation3 = Vec3;|api/graphics3d/SceneTypes.d.ts|
|New API|NA|Class name: global;<br>API declaration: export type Scale3 = Vec3;<br>Differences: export type Scale3 = Vec3;|api/graphics3d/SceneTypes.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.graphics.scene.d.ts<br>Differences: ArkGraphics3D|api/@ohos.graphics.scene.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\graphics3d\Scene.d.ts<br>Differences: ArkGraphics3D|api/graphics3d/Scene.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\graphics3d\SceneNodes.d.ts<br>Differences: ArkGraphics3D|api/graphics3d/SceneNodes.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\graphics3d\ScenePostProcessSettings.d.ts<br>Differences: ArkGraphics3D|api/graphics3d/ScenePostProcessSettings.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\graphics3d\SceneResources.d.ts<br>Differences: ArkGraphics3D|api/graphics3d/SceneResources.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\graphics3d\SceneTypes.d.ts<br>Differences: ArkGraphics3D|api/graphics3d/SceneTypes.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.ArkGraphics3D.d.ts<br>Differences: ArkGraphics3D|kits/@kit.ArkGraphics3D.d.ts|
