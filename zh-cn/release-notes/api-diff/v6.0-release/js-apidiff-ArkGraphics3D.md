| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：SceneResourceFactory；<br>API声明：createGeometry(params: SceneNodeParameters, mesh: MeshResource): Promise\<Geometry>;<br>差异内容：createGeometry(params: SceneNodeParameters, mesh: MeshResource): Promise\<Geometry>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：SceneResourceFactory；<br>API声明：createMesh(params: SceneResourceParameters, geometry: GeometryDefinition): Promise\<MeshResource>;<br>差异内容：createMesh(params: SceneResourceParameters, geometry: GeometryDefinition): Promise\<MeshResource>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：SceneResourceFactory；<br>API声明：createScene(uri?: ResourceStr): Promise\<Scene>;<br>差异内容：createScene(uri?: ResourceStr): Promise\<Scene>;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：Scene；<br>API声明：importNode(name: string, node: Node, parent: Node \| null): Node;<br>差异内容：importNode(name: string, node: Node, parent: Node \| null): Node;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：Scene；<br>API声明：importScene(name: string, scene: Scene, parent: Node \| null): Node;<br>差异内容：importScene(name: string, scene: Scene, parent: Node \| null): Node;|api/graphics3d/Scene.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface BloomSettings<br>差异内容：export interface BloomSettings|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：BloomSettings；<br>API声明：thresholdHard?: number;<br>差异内容：thresholdHard?: number;|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：BloomSettings；<br>API声明：thresholdSoft?: number;<br>差异内容：thresholdSoft?: number;|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：BloomSettings；<br>API声明：scaleFactor?: number;<br>差异内容：scaleFactor?: number;|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：BloomSettings；<br>API声明：scatter?: number;<br>差异内容：scatter?: number;|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：PostProcessSettings；<br>API声明：bloom?: BloomSettings;<br>差异内容：bloom?: BloomSettings;|api/graphics3d/ScenePostProcessSettings.d.ts|
|新增API|NA|类名：SceneResourceType；<br>API声明：MESH_RESOURCE = 8<br>差异内容：MESH_RESOURCE = 8|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface MeshResource<br>差异内容：export interface MeshResource|api/graphics3d/SceneResources.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum GeometryType<br>差异内容：export enum GeometryType|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：GeometryType；<br>API声明：CUSTOM = 0<br>差异内容：CUSTOM = 0|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：GeometryType；<br>API声明：CUBE = 1<br>差异内容：CUBE = 1|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：GeometryType；<br>API声明：PLANE = 2<br>差异内容：PLANE = 2|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：GeometryType；<br>API声明：SPHERE = 3<br>差异内容：SPHERE = 3|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export abstract class GeometryDefinition<br>差异内容：export abstract class GeometryDefinition|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：GeometryDefinition；<br>API声明：readonly geometryType: GeometryType;<br>差异内容：readonly geometryType: GeometryType;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export enum PrimitiveTopology<br>差异内容：export enum PrimitiveTopology|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：PrimitiveTopology；<br>API声明：TRIANGLE_LIST = 0<br>差异内容：TRIANGLE_LIST = 0|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：PrimitiveTopology；<br>API声明：TRIANGLE_STRIP = 1<br>差异内容：TRIANGLE_STRIP = 1|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export class CustomGeometry<br>差异内容：export class CustomGeometry|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：CustomGeometry；<br>API声明：topology?: PrimitiveTopology;<br>差异内容：topology?: PrimitiveTopology;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：CustomGeometry；<br>API声明：vertices: Vec3[];<br>差异内容：vertices: Vec3[];|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：CustomGeometry；<br>API声明：indices?: number[];<br>差异内容：indices?: number[];|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：CustomGeometry；<br>API声明：normals?: Vec3[];<br>差异内容：normals?: Vec3[];|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：CustomGeometry；<br>API声明：uvs?: Vec2[];<br>差异内容：uvs?: Vec2[];|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：CustomGeometry；<br>API声明：colors?: Color[];<br>差异内容：colors?: Color[];|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export class CubeGeometry<br>差异内容：export class CubeGeometry|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：CubeGeometry；<br>API声明：size: Vec3;<br>差异内容：size: Vec3;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export class PlaneGeometry<br>差异内容：export class PlaneGeometry|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：PlaneGeometry；<br>API声明：size: Vec2;<br>差异内容：size: Vec2;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：global；<br>API声明：export class SphereGeometry<br>差异内容：export class SphereGeometry|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：SphereGeometry；<br>API声明：radius: number;<br>差异内容：radius: number;|api/graphics3d/SceneTypes.d.ts|
|新增API|NA|类名：SphereGeometry；<br>API声明：segmentCount: number;<br>差异内容：segmentCount: number;|api/graphics3d/SceneTypes.d.ts|
