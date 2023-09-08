---
{"dg-publish":true,"permalink":"/3d-geometry/","tags":["3d"]}
---

Related: #programming 
Contents: [[CGRA251 MOC\|CGRA251 MOC]]
[CGRA Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CGRA251_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# 3d Geometry

- Can perform [[3d Transformations\|3d Transformations]] on it

## Types of Geometry

### Explicit Geometry

- Point clouds, triangle meshes etc
- [[Polygon Mesh\|Polygon Mesh]]


### Implicit Geometry

- Parametric geometry
- Lines/curves/parametric surfaces

### Volume Geometry

- Voxel grid (stack of images)
- Medical Images (MRI?) 

## Vertex

- A vertex is a collection of generic attributes
	- Positional coords
	- Colours
	- texture coords
	- Any other info associated with that point in space


- Position is generally stored in 4d [[Homogeneous Coordinates\|Homogeneous Coordinates]] (x,y,z,w)
	- If $w=1 \ (x,y,z,0)$, then that point is a *position* in space
	- If $w = 0 \ (x,y,z,1)$, then the vector is a *direction* in space

## Relationships Between Points/Vectors

P = Point (Vertex)
V = Vector/Direction (normal)

$$P-P=V$$
$$P+V=P$$
$$V+V=V$$
$$P+P=n/a$$


