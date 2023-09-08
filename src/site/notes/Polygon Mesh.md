---
{"dg-publish":true,"permalink":"/polygon-mesh/"}
---

Related: #programming 
Contents: [[CGRA251 MOC\|CGRA251 MOC]]
[CGRA Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CGRA251_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# Why Use Triangles

- Min number of points to create a surface
- 3 points *always* define a unique plane, 4 points does not
- Well defined method ([[barycentric interpolation\|barycentric interpolation]])

## Mesh Topology

- Nearest neighbour of vertex?
	- For defining edges
- Adjacent triangles of a vertex
	- For defining faces

### Polygon Soup

- Map of faces to 3 [[Point\|Points]]
- Polygons are unrelated
- Storing *duplicates* of vertices (as all three for each face)

### Vertex-Vertex

- List of vertices
	- Stored are coords of vertex
	- And List of connected verts
- Edges and faces are [[3d Geometry#Implicit Geometry\|Implicit]]

#### With [[Adjacency Matrix\|Adjacency Matrix]]

- Store all vertices in 2d matrix
- If verts connect at `matrix[v1][v2]`, v1 and v2 are neighbours

### Face-Vertex

- Vertex list
	- Stored coords of vertex
	- And list of connected faces (incident faces)

This is what [[OBJ\|OBJ]] file type does

### Winged-Edge

- Vertex list
	- With list of incident edges
- Edge list
	- List of incident vertexs,edges,faces

Allows for easy restructuring of the mesh

## Formats

- OBJ, FBX etc