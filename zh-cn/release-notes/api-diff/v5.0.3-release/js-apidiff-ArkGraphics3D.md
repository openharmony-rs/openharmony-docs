| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：export interface RaycastResult<br>差异内容：export interface RaycastResult|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：RaycastResult；<br>API声明：node: Node;<br>差异内容：node: Node;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：RaycastResult；<br>API声明：centerDistance: number;<br>差异内容：centerDistance: number;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：RaycastResult；<br>API声明：hitPosition: Position3;<br>差异内容：hitPosition: Position3;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface RaycastParameters<br>差异内容：export interface RaycastParameters|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：RaycastParameters；<br>API声明：rootNode?: Node;<br>差异内容：rootNode?: Node;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface RenderResourceFactory<br>差异内容：export interface RenderResourceFactory|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：RenderResourceFactory；<br>API声明：createMesh(params: SceneResourceParameters, geometry: GeometryDefinition): Promise\<MeshResource>;<br>差异内容：createMesh(params: SceneResourceParameters, geometry: GeometryDefinition): Promise\<MeshResource>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：RenderResourceFactory；<br>API声明：createSampler(params: SceneResourceParameters): Promise\<Sampler>;<br>差异内容：createSampler(params: SceneResourceParameters): Promise\<Sampler>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：RenderResourceFactory；<br>API声明：createScene(uri?: ResourceStr): Promise\<Scene>;<br>差异内容：createScene(uri?: ResourceStr): Promise\<Scene>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：SceneResourceFactory；<br>API声明：createGeometry(params: SceneNodeParameters, mesh: MeshResource): Promise\<Geometry>;<br>差异内容：createGeometry(params: SceneNodeParameters, mesh: MeshResource): Promise\<Geometry>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SceneComponent<br>差异内容：export interface SceneComponent|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：SceneComponent；<br>API声明：name: string;<br>差异内容：name: string;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：SceneComponent；<br>API声明：readonly property: Record\<string, string \| number \| Vec2 \| Vec3 \| Vec4 \| SceneResource \| boolean \| number[] \| string[] \| SceneResource[] \| Vec2[] \| Vec3[] \| Vec4[] \| null \| undefined>;<br>差异内容：readonly property: Record\<string, string \| number \| Vec2 \| Vec3 \| Vec4 \| SceneResource \| boolean \| number[] \| string[] \| SceneResource[] \| Vec2[] \| Vec3[] \| Vec4[] \| null \| undefined>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface RenderContext<br>差异内容：export interface RenderContext|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：RenderContext；<br>API声明：getRenderResourceFactory(): RenderResourceFactory;<br>差异内容：getRenderResourceFactory(): RenderResourceFactory;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：RenderContext；<br>API声明：loadPlugin(name: string): Promise\<boolean>;<br>差异内容：loadPlugin(name: string): Promise\<boolean>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：RenderContext；<br>API声明：registerResourcePath(protocol: string, uri: string): boolean;<br>差异内容：registerResourcePath(protocol: string, uri: string): boolean;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface RenderParameters<br>差异内容：export interface RenderParameters|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：RenderParameters；<br>API声明：alwaysRender?: boolean;<br>差异内容：alwaysRender?: boolean;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：Scene；<br>API声明：static getDefaultRenderContext(): RenderContext \| null;<br>差异内容：static getDefaultRenderContext(): RenderContext \| null;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：Scene；<br>API声明：importNode(name: string, node: Node, parent: Node \| null): Node;<br>差异内容：importNode(name: string, node: Node, parent: Node \| null): Node;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：Scene；<br>API声明：importScene(name: string, scene: Scene, parent: Node \| null): Node;<br>差异内容：importScene(name: string, scene: Scene, parent: Node \| null): Node;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：Scene；<br>API声明：renderFrame(params?: RenderParameters): boolean;<br>差异内容：renderFrame(params?: RenderParameters): boolean;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：Scene；<br>API声明：createComponent(node: Node, name: string): Promise\<SceneComponent>;<br>差异内容：createComponent(node: Node, name: string): Promise\<SceneComponent>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：Scene；<br>API声明：getComponent(node: Node, name: string): SceneComponent \| null;<br>差异内容：getComponent(node: Node, name: string): SceneComponent \| null;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：Geometry；<br>API声明：readonly morpher?: Morpher;<br>差异内容：readonly morpher?: Morpher;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：Camera；<br>API声明：raycast(viewPosition: Vec2, params: RaycastParameters): Promise\<RaycastResult[]>;<br>差异内容：raycast(viewPosition: Vec2, params: RaycastParameters): Promise\<RaycastResult[]>;|api/graphics3d/SceneNodes.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface BloomSettings<br>差异内容：export interface BloomSettings|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：BloomSettings；<br>API声明：thresholdHard?: number;<br>差异内容：thresholdHard?: number;|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：BloomSettings；<br>API声明：thresholdSoft?: number;<br>差异内容：thresholdSoft?: number;|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：BloomSettings；<br>API声明：scaleFactor?: number;<br>差异内容：scaleFactor?: number;|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：BloomSettings；<br>API声明：scatter?: number;<br>差异内容：scatter?: number;|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：PostProcessSettings；<br>API声明：bloom?: BloomSettings;<br>差异内容：bloom?: BloomSettings;|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：SceneResourceType；<br>API声明：MESH_RESOURCE = 8<br>差异内容：MESH_RESOURCE = 8|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：MaterialType；<br>API声明：METALLIC_ROUGHNESS = 2<br>差异内容：METALLIC_ROUGHNESS = 2|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum CullMode<br>差异内容：export enum CullMode|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：CullMode；<br>API声明：NONE = 0<br>差异内容：NONE = 0|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：CullMode；<br>API声明：FRONT = 1<br>差异内容：FRONT = 1|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：CullMode；<br>API声明：BACK = 2<br>差异内容：BACK = 2|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Blend<br>差异内容：export interface Blend|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Blend；<br>API声明：enabled: boolean;<br>差异内容：enabled: boolean;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface RenderSort<br>差异内容：export interface RenderSort|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：RenderSort；<br>API声明：renderSortLayer?: number;<br>差异内容：renderSortLayer?: number;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：RenderSort；<br>API声明：renderSortLayerOrder?: number;<br>差异内容：renderSortLayerOrder?: number;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Material；<br>API声明：shadowReceiver?: boolean;<br>差异内容：shadowReceiver?: boolean;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Material；<br>API声明：cullMode?: CullMode;<br>差异内容：cullMode?: CullMode;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Material；<br>API声明：blend?: Blend;<br>差异内容：blend?: Blend;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Material；<br>API声明：alphaCutoff?: number;<br>差异内容：alphaCutoff?: number;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Material；<br>API声明：renderSort?: RenderSort;<br>差异内容：renderSort?: RenderSort;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface MaterialProperty<br>差异内容：export interface MaterialProperty|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：MaterialProperty；<br>API声明：image: Image \| null;<br>差异内容：image: Image \| null;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：MaterialProperty；<br>API声明：factor: Vec4;<br>差异内容：factor: Vec4;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：MaterialProperty；<br>API声明：sampler?: Sampler;<br>差异内容：sampler?: Sampler;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface MetallicRoughnessMaterial<br>差异内容：export interface MetallicRoughnessMaterial|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：MetallicRoughnessMaterial；<br>API声明：baseColor: MaterialProperty;<br>差异内容：baseColor: MaterialProperty;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：MetallicRoughnessMaterial；<br>API声明：normal: MaterialProperty;<br>差异内容：normal: MaterialProperty;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：MetallicRoughnessMaterial；<br>API声明：material: MaterialProperty;<br>差异内容：material: MaterialProperty;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：MetallicRoughnessMaterial；<br>API声明：ambientOcclusion: MaterialProperty;<br>差异内容：ambientOcclusion: MaterialProperty;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：MetallicRoughnessMaterial；<br>API声明：emissive: MaterialProperty;<br>差异内容：emissive: MaterialProperty;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：MetallicRoughnessMaterial；<br>API声明：clearCoat: MaterialProperty;<br>差异内容：clearCoat: MaterialProperty;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：MetallicRoughnessMaterial；<br>API声明：clearCoatRoughness: MaterialProperty;<br>差异内容：clearCoatRoughness: MaterialProperty;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：MetallicRoughnessMaterial；<br>API声明：clearCoatNormal: MaterialProperty;<br>差异内容：clearCoatNormal: MaterialProperty;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：MetallicRoughnessMaterial；<br>API声明：sheen: MaterialProperty;<br>差异内容：sheen: MaterialProperty;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：MetallicRoughnessMaterial；<br>API声明：specular: MaterialProperty;<br>差异内容：specular: MaterialProperty;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum SamplerFilter<br>差异内容：export enum SamplerFilter|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SamplerFilter；<br>API声明：NEAREST = 0<br>差异内容：NEAREST = 0|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SamplerFilter；<br>API声明：LINEAR = 1<br>差异内容：LINEAR = 1|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum SamplerAddressMode<br>差异内容：export enum SamplerAddressMode|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SamplerAddressMode；<br>API声明：REPEAT = 0<br>差异内容：REPEAT = 0|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SamplerAddressMode；<br>API声明：MIRRORED_REPEAT = 1<br>差异内容：MIRRORED_REPEAT = 1|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：SamplerAddressMode；<br>API声明：CLAMP_TO_EDGE = 2<br>差异内容：CLAMP_TO_EDGE = 2|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Sampler<br>差异内容：export interface Sampler|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Sampler；<br>API声明：magFilter?: SamplerFilter;<br>差异内容：magFilter?: SamplerFilter;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Sampler；<br>API声明：minFilter?: SamplerFilter;<br>差异内容：minFilter?: SamplerFilter;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Sampler；<br>API声明：mipMapMode?: SamplerFilter;<br>差异内容：mipMapMode?: SamplerFilter;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Sampler；<br>API声明：addressModeU?: SamplerAddressMode;<br>差异内容：addressModeU?: SamplerAddressMode;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Sampler；<br>API声明：addressModeV?: SamplerAddressMode;<br>差异内容：addressModeV?: SamplerAddressMode;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface Morpher<br>差异内容：export interface Morpher|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Morpher；<br>API声明：readonly targets: Record\<string, number>;<br>差异内容：readonly targets: Record\<string, number>;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface MeshResource<br>差异内容：export interface MeshResource|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：Animation；<br>API声明：speed?: number;<br>差异内容：speed?: number;|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum GeometryType<br>差异内容：export enum GeometryType|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：GeometryType；<br>API声明：CUSTOM = 0<br>差异内容：CUSTOM = 0|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：GeometryType；<br>API声明：CUBE = 1<br>差异内容：CUBE = 1|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：GeometryType；<br>API声明：PLANE = 2<br>差异内容：PLANE = 2|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：GeometryType；<br>API声明：SPHERE = 3<br>差异内容：SPHERE = 3|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare abstract class GeometryDefinition<br>差异内容：export declare abstract class GeometryDefinition|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：GeometryDefinition；<br>API声明：readonly geometryType: GeometryType;<br>差异内容：readonly geometryType: GeometryType;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum PrimitiveTopology<br>差异内容：export enum PrimitiveTopology|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：PrimitiveTopology；<br>API声明：TRIANGLE_LIST = 0<br>差异内容：TRIANGLE_LIST = 0|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：PrimitiveTopology；<br>API声明：TRIANGLE_STRIP = 1<br>差异内容：TRIANGLE_STRIP = 1|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class CustomGeometry<br>差异内容：export declare class CustomGeometry|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：CustomGeometry；<br>API声明：topology?: PrimitiveTopology;<br>差异内容：topology?: PrimitiveTopology;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：CustomGeometry；<br>API声明：vertices: Vec3[];<br>差异内容：vertices: Vec3[];|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：CustomGeometry；<br>API声明：indices?: number[];<br>差异内容：indices?: number[];|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：CustomGeometry；<br>API声明：normals?: Vec3[];<br>差异内容：normals?: Vec3[];|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：CustomGeometry；<br>API声明：uvs?: Vec2[];<br>差异内容：uvs?: Vec2[];|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：CustomGeometry；<br>API声明：colors?: Color[];<br>差异内容：colors?: Color[];|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class CubeGeometry<br>差异内容：export declare class CubeGeometry|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：CubeGeometry；<br>API声明：size: Vec3;<br>差异内容：size: Vec3;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class PlaneGeometry<br>差异内容：export declare class PlaneGeometry|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：PlaneGeometry；<br>API声明：size: Vec2;<br>差异内容：size: Vec2;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export declare class SphereGeometry<br>差异内容：export declare class SphereGeometry|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：SphereGeometry；<br>API声明：radius: number;<br>差异内容：radius: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：SphereGeometry；<br>API声明：segmentCount: number;<br>差异内容：segmentCount: number;|api/graphics3d/SceneTypes.d.ts|
|成员由子类迁移至父类|类名：SceneResourceFactory；<br>API声明：createShader(params: SceneResourceParameters): Promise\<Shader>;<br>差异内容：createShader(params: SceneResourceParameters): Promise\<Shader>;|类名：RenderResourceFactory；<br>API声明：createShader(params: SceneResourceParameters): Promise\<Shader>;<br>差异内容：createShader(params: SceneResourceParameters): Promise\<Shader>;|api/graphics3d/Scene.d.ts|
|成员由子类迁移至父类|类名：SceneResourceFactory；<br>API声明：createImage(params: SceneResourceParameters): Promise\<Image>;<br>差异内容：createImage(params: SceneResourceParameters): Promise\<Image>;|类名：RenderResourceFactory；<br>API声明：createImage(params: SceneResourceParameters): Promise\<Image>;<br>差异内容：createImage(params: SceneResourceParameters): Promise\<Image>;|api/graphics3d/Scene.d.ts|
|arkts演进版本整改兼容变化|类名：global；<br>API声明：export class Scene<br>差异内容：NA|类名：global；<br>API声明：export declare class Scene<br>差异内容：NA|api/graphics3d/Scene.d.ts|
