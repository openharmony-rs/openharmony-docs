# SceneTypes(3D scene common type declarations)

## Summary

### Classes

| Name | Description |
| --- | --- |
| [CubeGeometry](arkts-arkgraphics3d-scenetypes-cubegeometry-c.md) | A cube geometry type that inherits from GeometryDefinition. |
| [CustomGeometry](arkts-arkgraphics3d-scenetypes-customgeometry-c.md) | A custom geometry type that inherits from GeometryDefinition. |
| [CylinderGeometry](arkts-arkgraphics3d-scenetypes-cylindergeometry-c.md) | A cylinder geometry type that inherits from GeometryDefinition. |
| [GeometryDefinition](arkts-arkgraphics3d-scenetypes-geometrydefinition-c.md) | An abstract class used to define the properties of specific geometry types. |
| [PlaneGeometry](arkts-arkgraphics3d-scenetypes-planegeometry-c.md) | A plane geometry type that inherits from GeometryDefinition. |
| [SphereGeometry](arkts-arkgraphics3d-scenetypes-spheregeometry-c.md) | A sphere geometry type that inherits from GeometryDefinition. |

### Interfaces

| Name | Description |
| --- | --- |
| [Aabb](arkts-arkgraphics3d-scenetypes-aabb-i.md) | Axis aligned boundary box used to determine whether two objects in space are overlapping. |
| [Color](arkts-arkgraphics3d-scenetypes-color-i.md) | Color in RGBA format. It consists of four components: red, green, blue, and alpha. |
| [Mat4x4](arkts-arkgraphics3d-scenetypes-mat4x4-i.md) | A camera matrix, which is a mathematical tool for transforming 3D world coordinates into 2D image coordinates. |
| [Quaternion](arkts-arkgraphics3d-scenetypes-quaternion-i.md) | A mathematical notation for representing spatial rotations of elements in 3D space. Compared with Euler angles, a quaternion has advantages in numerical stability and avoiding the gimbal lock problem. |
| [Rect](arkts-arkgraphics3d-scenetypes-rect-i.md) | Rectangle in a plane. |
| [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md) | A two-dimensional vector used to represent a point or a direction in 2D space. It consists of two components: x and y. |
| [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md) | A three-dimensional vector used to represent a point, a direction, or a vector transformation in 3D space. It consists of three components: x, y, and z. |
| [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md) | A four-dimensional vector used to represent a point, a direction, or a vector transformation in 4D space. It consists of four components: x, y, z, and w. The fourth component (w) enhances normalization and convenience for various calculations and transformations. |

### Types

| Name | Description |
| --- | --- |
| [Position3](arkts-arkgraphics3d-position3-t.md) | Position of an object in 3D space. The type is a three-dimensional vector. The unit is the scene unit in the world coordinate system (such as cm, m, and km). The value can be any value. |
| [Rotation3](arkts-arkgraphics3d-rotation3-t.md) | Rotation of an object in 3D space. The type is a three-dimensional vector in the unit of radian (rad). The value can be any value. |
| [Scale3](arkts-arkgraphics3d-scale3-t.md) | Scaling of an object in 3D space. The value is of the Vec3 type. Any 3D vector. |

### Enums

| Name | Description |
| --- | --- |
| [GeometryType](arkts-arkgraphics3d-scenetypes-geometrytype-e.md) | Enumerates the geometry types. |
| [PrimitiveTopology](arkts-arkgraphics3d-scenetypes-primitivetopology-e.md) | Enumerates the vertex processing methods. |
| [RenderingPipelineType](arkts-arkgraphics3d-scenetypes-renderingpipelinetype-e.md) | Enumerates the rendering pipeline types. |
| [ShadowAlgorithmType](arkts-arkgraphics3d-scenetypes-shadowalgorithmtype-e.md) | Enumerates the types of shadow algorithms. |
