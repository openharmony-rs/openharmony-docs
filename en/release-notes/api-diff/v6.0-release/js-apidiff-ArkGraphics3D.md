| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: SceneResourceFactory;<br>API declaration: createGeometry(params: SceneNodeParameters, mesh: MeshResource): Promise\<Geometry>;<br>DIfferences: createGeometry(params: SceneNodeParameters, mesh: MeshResource): Promise\<Geometry>;|api/graphics3d/Scene.d.ts|
|New API |NA|Class name: SceneResourceFactory;<br>API declaration: createMesh(params: SceneResourceParameters, geometry: GeometryDefinition): Promise\<MeshResource>;<br>DIfferences: createMesh(params: SceneResourceParameters, geometry: GeometryDefinition): Promise\<MeshResource>;|api/graphics3d/Scene.d.ts|
|New API |NA|Class name: SceneResourceFactory;<br>API declaration: createScene(uri?: ResourceStr): Promise\<Scene>;<br>DIfferences: createScene(uri?: ResourceStr): Promise\<Scene>;|api/graphics3d/Scene.d.ts|
|New API |NA|Class name: Scene;<br>API declaration: importNode(name: string, node: Node, parent: Node \| null): Node;<br>DIfferences: importNode(name: string, node: Node, parent: Node \| null): Node;|api/graphics3d/Scene.d.ts|
|New API |NA|Class name: Scene;<br>API declaration: importScene(name: string, scene: Scene, parent: Node \| null): Node;<br>DIfferences: importScene(name: string, scene: Scene, parent: Node \| null): Node;|api/graphics3d/Scene.d.ts|
|New API |NA|Class name: global;<br>API declaration: export interface BloomSettings<br>DIfferences: export interface BloomSettings|api/graphics3d/ScenePostProcessSettings.d.ts|
|New API |NA|Class name: BloomSettings;<br>API declaration: thresholdHard?: number;<br>DIfferences: thresholdHard?: number;|api/graphics3d/ScenePostProcessSettings.d.ts|
|New API |NA|Class name: BloomSettings;<br>API declaration: thresholdSoft?: number;<br>DIfferences: thresholdSoft?: number;|api/graphics3d/ScenePostProcessSettings.d.ts|
|New API |NA|Class name: BloomSettings;<br>API declaration: scaleFactor?: number;<br>DIfferences: scaleFactor?: number;|api/graphics3d/ScenePostProcessSettings.d.ts|
|New API |NA|Class name: BloomSettings;<br>API declaration: scatter?: number;<br>DIfferences: scatter?: number;|api/graphics3d/ScenePostProcessSettings.d.ts|
|New API |NA|Class name: PostProcessSettings;<br>API declaration: bloom?: BloomSettings;<br>DIfferences: bloom?: BloomSettings;|api/graphics3d/ScenePostProcessSettings.d.ts|
|New API |NA|Class name: SceneResourceType;<br>API declaration: MESH_RESOURCE = 8<br>DIfferences: MESH_RESOURCE = 8|api/graphics3d/SceneResources.d.ts|
|New API |NA|Class name: global;<br>API declaration: export interface MeshResource<br>DIfferences: export interface MeshResource|api/graphics3d/SceneResources.d.ts|
|New API |NA|Class name: global;<br>API declaration: export enum GeometryType<br>DIfferences: export enum GeometryType|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: GeometryType;<br>API declaration: CUSTOM = 0<br>DIfferences: CUSTOM = 0|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: GeometryType;<br>API declaration: CUBE = 1<br>DIfferences: CUBE = 1|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: GeometryType;<br>API declaration: PLANE = 2<br>DIfferences: PLANE = 2|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: GeometryType;<br>API declaration: SPHERE = 3<br>DIfferences: SPHERE = 3|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: global;<br>API declaration: export abstract class GeometryDefinition<br>DIfferences: export abstract class GeometryDefinition|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: GeometryDefinition;<br>API declaration: readonly geometryType: GeometryType;<br>DIfferences: readonly geometryType: GeometryType;|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: global;<br>API declaration: export enum PrimitiveTopology<br>DIfferences: export enum PrimitiveTopology|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: PrimitiveTopology;<br>API declaration: TRIANGLE_LIST = 0<br>DIfferences: TRIANGLE_LIST = 0|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: PrimitiveTopology;<br>API declaration: TRIANGLE_STRIP = 1<br>DIfferences: TRIANGLE_STRIP = 1|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: global;<br>API declaration: export class CustomGeometry<br>DIfferences: export class CustomGeometry|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: CustomGeometry;<br>API declaration: topology?: PrimitiveTopology;<br>DIfferences: topology?: PrimitiveTopology;|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: CustomGeometry;<br>API declaration: vertices: Vec3[];<br>DIfferences: vertices: Vec3[];|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: CustomGeometry;<br>API declaration: indices?: number[];<br>DIfferences: indices?: number[];|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: CustomGeometry;<br>API declaration: normals?: Vec3[];<br>DIfferences: normals?: Vec3[];|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: CustomGeometry;<br>API declaration: uvs?: Vec2[];<br>DIfferences: uvs?: Vec2[];|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: CustomGeometry;<br>API declaration: colors?: Color[];<br>DIfferences: colors?: Color[];|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: global;<br>API declaration: export class CubeGeometry<br>DIfferences: export class CubeGeometry|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: CubeGeometry;<br>API declaration: size: Vec3;<br>DIfferences: size: Vec3;|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: global;<br>API declaration: export class PlaneGeometry<br>DIfferences: export class PlaneGeometry|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: PlaneGeometry;<br>API declaration: size: Vec2;<br>DIfferences: size: Vec2;|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: global;<br>API declaration: export class SphereGeometry<br>DIfferences: export class SphereGeometry|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: SphereGeometry;<br>API declaration: radius: number;<br>DIfferences: radius: number;|api/graphics3d/SceneTypes.d.ts|
|New API |NA|Class name: SphereGeometry;<br>API declaration: segmentCount: number;<br>DIfferences: segmentCount: number;|api/graphics3d/SceneTypes.d.ts|
