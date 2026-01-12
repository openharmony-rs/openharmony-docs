| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: SceneResourceFactory;<br>API declaration: createShader(params: SceneResourceParameters): Promise\<Shader>;<br>Differences: createShader(params: SceneResourceParameters): Promise\<Shader>;|api/graphics3d/Scene.d.ts|
|New API |NA|Class name: SceneResourceFactory;<br>API declaration: createImage(params: SceneResourceParameters): Promise\<Image>;<br>Differences: createImage(params: SceneResourceParameters): Promise\<Image>;|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: global;<br>API declaration: export interface RaycastResult<br>Differences: export interface RaycastResult|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: RaycastResult;<br>API declaration: node: Node;<br>Differences: node: Node;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: RaycastResult;<br>API declaration: centerDistance: number;<br>Differences: centerDistance: number;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: RaycastResult;<br>API declaration: hitPosition: Position3;<br>Differences: hitPosition: Position3;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: global;<br>API declaration: export interface RaycastParameters<br>Differences: export interface RaycastParameters|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: RaycastParameters;<br>API declaration: rootNode?: Node;<br>Differences: rootNode?: Node;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: global;<br>API declaration: export interface RenderResourceFactory<br>Differences: export interface RenderResourceFactory|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: RenderResourceFactory;<br>API declaration: createShader(params: SceneResourceParameters): Promise\<Shader>;<br>Differences: createShader(params: SceneResourceParameters): Promise\<Shader>;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: RenderResourceFactory;<br>API declaration: createImage(params: SceneResourceParameters): Promise\<Image>;<br>Differences: createImage(params: SceneResourceParameters): Promise\<Image>;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: RenderResourceFactory;<br>API declaration: createMesh(params: SceneResourceParameters, geometry: GeometryDefinition): Promise\<MeshResource>;<br>Differences: createMesh(params: SceneResourceParameters, geometry: GeometryDefinition): Promise\<MeshResource>;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: RenderResourceFactory;<br>API declaration: createSampler(params: SceneResourceParameters): Promise\<Sampler>;<br>Differences: createSampler(params: SceneResourceParameters): Promise\<Sampler>;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: RenderResourceFactory;<br>API declaration: createScene(uri?: ResourceStr): Promise\<Scene>;<br>Differences: createScene(uri?: ResourceStr): Promise\<Scene>;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: SceneResourceFactory;<br>API declaration: createGeometry(params: SceneNodeParameters, mesh: MeshResource): Promise\<Geometry>;<br>Differences: createGeometry(params: SceneNodeParameters, mesh: MeshResource): Promise\<Geometry>;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: global;<br>API declaration: export interface SceneComponent<br>Differences: export interface SceneComponent|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: SceneComponent;<br>API declaration: name: string;<br>Differences: name: string;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: SceneComponent;<br>API declaration: readonly property: Record\<string, string \| number \| Vec2 \| Vec3 \| Vec4 \| SceneResource \| boolean \| number[] \| string[] \| SceneResource[] \| Vec2[] \| Vec3[] \| Vec4[] \| null \| undefined>;<br>Differences: readonly property: Record\<string, string \| number \| Vec2 \| Vec3 \| Vec4 \| SceneResource \| boolean \| number[] \| string[] \| SceneResource[] \| Vec2[] \| Vec3[] \| Vec4[] \| null \| undefined>;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: global;<br>API declaration: export interface RenderContext<br>Differences: export interface RenderContext|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: RenderContext;<br>API declaration: getRenderResourceFactory(): RenderResourceFactory;<br>Differences: getRenderResourceFactory(): RenderResourceFactory;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: RenderContext;<br>API declaration: loadPlugin(name: string): Promise\<boolean>;<br>Differences: loadPlugin(name: string): Promise\<boolean>;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: RenderContext;<br>API declaration: registerResourcePath(protocol: string, uri: string): boolean;<br>Differences: registerResourcePath(protocol: string, uri: string): boolean;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: Scene;<br>API declaration: static getDefaultRenderContext(): RenderContext \| null;<br>Differences: static getDefaultRenderContext(): RenderContext \| null;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: Scene;<br>API declaration: importNode(name: string, node: Node, parent: Node \| null): Node;<br>Differences: importNode(name: string, node: Node, parent: Node \| null): Node;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: Scene;<br>API declaration: importScene(name: string, scene: Scene, parent: Node \| null): Node;<br>Differences: importScene(name: string, scene: Scene, parent: Node \| null): Node;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: Scene;<br>API declaration: createComponent(node: Node, name: string): Promise\<SceneComponent>;<br>Differences: createComponent(node: Node, name: string): Promise\<SceneComponent>;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: Scene;<br>API declaration: getComponent(node: Node, name: string): SceneComponent \| null;<br>Differences: getComponent(node: Node, name: string): SceneComponent \| null;|NA|api/graphics3d/Scene.d.ts|
| Deleted API|Class name: Geometry;<br>API declaration: readonly morpher?: Morpher;<br>Differences: readonly morpher?: Morpher;|NA|api/graphics3d/SceneNodes.d.ts|
| Deleted API|Class name: Camera;<br>API declaration: raycast(viewPosition: Vec2, params: RaycastParameters): Promise\<RaycastResult[]>;<br>Differences: raycast(viewPosition: Vec2, params: RaycastParameters): Promise\<RaycastResult[]>;|NA|api/graphics3d/SceneNodes.d.ts|
| Deleted API|Class name: global;<br>API declaration: export interface BloomSettings<br>Differences: export interface BloomSettings|NA|api/graphics3d/ScenePostProcessSettings.d.ts|
| Deleted API|Class name: BloomSettings;<br>API declaration: thresholdHard?: number;<br>Differences: thresholdHard?: number;|NA|api/graphics3d/ScenePostProcessSettings.d.ts|
| Deleted API|Class name: BloomSettings;<br>API declaration: thresholdSoft?: number;<br>Differences: thresholdSoft?: number;|NA|api/graphics3d/ScenePostProcessSettings.d.ts|
| Deleted API|Class name: BloomSettings;<br>API declaration: scaleFactor?: number;<br>Differences: scaleFactor?: number;|NA|api/graphics3d/ScenePostProcessSettings.d.ts|
| Deleted API|Class name: BloomSettings;<br>API declaration: scatter?: number;<br>Differences: scatter?: number;|NA|api/graphics3d/ScenePostProcessSettings.d.ts|
| Deleted API|Class name: PostProcessSettings;<br>API declaration: bloom?: BloomSettings;<br>Differences: bloom?: BloomSettings;|NA|api/graphics3d/ScenePostProcessSettings.d.ts|
| Deleted API|Class name: SceneResourceType;<br>API declaration: MESH_RESOURCE = 8<br>Differences: MESH_RESOURCE = 8|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: MaterialType;<br>API declaration: METALLIC_ROUGHNESS = 2<br>Differences: METALLIC_ROUGHNESS = 2|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: global;<br>API declaration: export enum CullMode<br>Differences: export enum CullMode|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: CullMode;<br>API declaration: NONE = 0<br>Differences: NONE = 0|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: CullMode;<br>API declaration: FRONT = 1<br>Differences: FRONT = 1|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: CullMode;<br>API declaration: BACK = 2<br>Differences: BACK = 2|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: global;<br>API declaration: export interface Blend<br>Differences: export interface Blend|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: Blend;<br>API declaration: enabled: boolean;<br>Differences: enabled: boolean;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: global;<br>API declaration: export interface RenderSort<br>Differences: export interface RenderSort|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: RenderSort;<br>API declaration: renderSortLayer?: number;<br>Differences: renderSortLayer?: number;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: RenderSort;<br>API declaration: renderSortLayerOrder?: number;<br>Differences: renderSortLayerOrder?: number;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: Material;<br>API declaration: shadowReceiver?: boolean;<br>Differences: shadowReceiver?: boolean;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: Material;<br>API declaration: cullMode?: CullMode;<br>Differences: cullMode?: CullMode;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: Material;<br>API declaration: blend?: Blend;<br>Differences: blend?: Blend;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: Material;<br>API declaration: alphaCutoff?: number;<br>Differences: alphaCutoff?: number;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: Material;<br>API declaration: renderSort?: RenderSort;<br>Differences: renderSort?: RenderSort;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: global;<br>API declaration: export interface MaterialProperty<br>Differences: export interface MaterialProperty|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: MaterialProperty;<br>API declaration: image: Image \| null;<br>Differences: image: Image \| null;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: MaterialProperty;<br>API declaration: factor: Vec4;<br>Differences: factor: Vec4;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: MaterialProperty;<br>API declaration: sampler?: Sampler;<br>Differences: sampler?: Sampler;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: global;<br>API declaration: export interface MetallicRoughnessMaterial<br>Differences: export interface MetallicRoughnessMaterial|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: MetallicRoughnessMaterial;<br>API declaration: baseColor: MaterialProperty;<br>Differences: baseColor: MaterialProperty;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: MetallicRoughnessMaterial;<br>API declaration: normal: MaterialProperty;<br>Differences: normal: MaterialProperty;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: MetallicRoughnessMaterial;<br>API declaration: material: MaterialProperty;<br>Differences: material: MaterialProperty;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: MetallicRoughnessMaterial;<br>API declaration: ambientOcclusion: MaterialProperty;<br>Differences: ambientOcclusion: MaterialProperty;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: MetallicRoughnessMaterial;<br>API declaration: emissive: MaterialProperty;<br>Differences: emissive: MaterialProperty;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: MetallicRoughnessMaterial;<br>API declaration: clearCoat: MaterialProperty;<br>Differences: clearCoat: MaterialProperty;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: MetallicRoughnessMaterial;<br>API declaration: clearCoatRoughness: MaterialProperty;<br>Differences: clearCoatRoughness: MaterialProperty;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: MetallicRoughnessMaterial;<br>API declaration: clearCoatNormal: MaterialProperty;<br>Differences: clearCoatNormal: MaterialProperty;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: MetallicRoughnessMaterial;<br>API declaration: sheen: MaterialProperty;<br>Differences: sheen: MaterialProperty;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: MetallicRoughnessMaterial;<br>API declaration: specular: MaterialProperty;<br>Differences: specular: MaterialProperty;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: global;<br>API declaration: export enum SamplerFilter<br>Differences: export enum SamplerFilter|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: SamplerFilter;<br>API declaration: NEAREST = 0<br>Differences: NEAREST = 0|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: SamplerFilter;<br>API declaration: LINEAR = 1<br>Differences: LINEAR = 1|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: global;<br>API declaration: export enum SamplerAddressMode<br>Differences: export enum SamplerAddressMode|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: SamplerAddressMode;<br>API declaration: REPEAT = 0<br>Differences: REPEAT = 0|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: SamplerAddressMode;<br>API declaration: MIRRORED_REPEAT = 1<br>Differences: MIRRORED_REPEAT = 1|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: SamplerAddressMode;<br>API declaration: CLAMP_TO_EDGE = 2<br>Differences: CLAMP_TO_EDGE = 2|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: global;<br>API declaration: export interface Sampler<br>Differences: export interface Sampler|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: Sampler;<br>API declaration: magFilter?: SamplerFilter;<br>Differences: magFilter?: SamplerFilter;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: Sampler;<br>API declaration: minFilter?: SamplerFilter;<br>Differences: minFilter?: SamplerFilter;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: Sampler;<br>API declaration: mipMapMode?: SamplerFilter;<br>Differences: mipMapMode?: SamplerFilter;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: Sampler;<br>API declaration: addressModeU?: SamplerAddressMode;<br>Differences: addressModeU?: SamplerAddressMode;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: Sampler;<br>API declaration: addressModeV?: SamplerAddressMode;<br>Differences: addressModeV?: SamplerAddressMode;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: global;<br>API declaration: export interface Morpher<br>Differences: export interface Morpher|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: Morpher;<br>API declaration: readonly targets: Record\<string, number>;<br>Differences: readonly targets: Record\<string, number>;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: global;<br>API declaration: export interface MeshResource<br>Differences: export interface MeshResource|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: Animation;<br>API declaration: speed?: number;<br>Differences: speed?: number;|NA|api/graphics3d/SceneResources.d.ts|
| Deleted API|Class name: global;<br>API declaration: export enum GeometryType<br>Differences: export enum GeometryType|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: GeometryType;<br>API declaration: CUSTOM = 0<br>Differences: CUSTOM = 0|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: GeometryType;<br>API declaration: CUBE = 1<br>Differences: CUBE = 1|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: GeometryType;<br>API declaration: PLANE = 2<br>Differences: PLANE = 2|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: GeometryType;<br>API declaration: SPHERE = 3<br>Differences: SPHERE = 3|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: global;<br>API declaration: export declare abstract class GeometryDefinition<br>Differences: export declare abstract class GeometryDefinition|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: GeometryDefinition;<br>API declaration: readonly geometryType: GeometryType;<br>Differences: readonly geometryType: GeometryType;|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: global;<br>API declaration: export enum PrimitiveTopology<br>Differences: export enum PrimitiveTopology|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: PrimitiveTopology;<br>API declaration: TRIANGLE_LIST = 0<br>Differences: TRIANGLE_LIST = 0|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: PrimitiveTopology;<br>API declaration: TRIANGLE_STRIP = 1<br>Differences: TRIANGLE_STRIP = 1|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: global;<br>API declaration: export declare class CustomGeometry<br>Differences: export declare class CustomGeometry|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: CustomGeometry;<br>API declaration: topology?: PrimitiveTopology;<br>Differences: topology?: PrimitiveTopology;|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: CustomGeometry;<br>API declaration: vertices: Vec3[];<br>Differences: vertices: Vec3[];|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: CustomGeometry;<br>API declaration: indices?: number[];<br>Differences: indices?: number[];|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: CustomGeometry;<br>API declaration: normals?: Vec3[];<br>Differences: normals?: Vec3[];|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: CustomGeometry;<br>API declaration: uvs?: Vec2[];<br>Differences: uvs?: Vec2[];|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: CustomGeometry;<br>API declaration: colors?: Color[];<br>Differences: colors?: Color[];|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: global;<br>API declaration: export declare class CubeGeometry<br>Differences: export declare class CubeGeometry|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: CubeGeometry;<br>API declaration: size: Vec3;<br>Differences: size: Vec3;|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: global;<br>API declaration: export declare class PlaneGeometry<br>Differences: export declare class PlaneGeometry|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: PlaneGeometry;<br>API declaration: size: Vec2;<br>Differences: size: Vec2;|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: global;<br>API declaration: export declare class SphereGeometry<br>Differences: export declare class SphereGeometry|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: SphereGeometry;<br>API declaration: radius: number;<br>Differences: radius: number;|NA|api/graphics3d/SceneTypes.d.ts|
| Deleted API|Class name: SphereGeometry;<br>API declaration: segmentCount: number;<br>Differences: segmentCount: number;|NA|api/graphics3d/SceneTypes.d.ts|
|Compatible for ArkTS version evolution|Class name: global;<br>API declaration: export declare class Scene<br>Differences: NA|Class name: global;<br>API declaration: export class Scene<br>Differences: NA|api/graphics3d/Scene.d.ts|
