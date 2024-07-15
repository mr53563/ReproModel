# ReproModel

## Notes
This repository contains multiple files relating to the manuscriopt by Hicks et al. It contains the original geometry stl-file (Geometry.stl), which was created as an export from CAD. It contains a remeshed st-file (GeometryRemeshed.stl) that was edited with MeshLab (2023.12) for better triangular mesh quality (GeometryRemeshed.msh). It also contains a msh-file created with Gmsh (4.11.1) in which we created a tetrahedral mesh for import with FEBio. Finally, this repository contains an FEBio input file (GeometryRemeshed.fs2) and an FEBio output file (GeometryRemeshed.xplt). The latter two files serve as an example application of the virtual benchtop model as described in Hicks et al.

## MeshLab Procedure
1. We imported the original stl-file via File>Import Mesh (and selected Unify Duplicated Vertices).
2. We remeshed the original stl-file via Filters>Remeshing, Simplification, and Restruction> Remesing: Isotropic Explicity Remeshing (and chose the default values)
3. We saved the output as an stl-file

## Gmsh Procedure
1. We imported the output from MeshLab via File>Open
2. We created a volume via Modules>Geometry>Elementary entities>Add>Volume (select the geometry)
3. We meshed the geometry via Mesh>3D
4. We saved the output as a msh-file

## FEBio Procedure
1. We started a new model via New Model>Structural Analysis
2. We imported the out Gmsh output via File>Import Geometry
3. We assigned Dirichlet boundary conditions via Physics>Add Nodal BCs>Zero Displacement (select x,y, and z)
4. We assigned Neumann boundary conditions via Physics>Add Surface Load>Pressure
5. We assigned a Neo-Hookean material to all solids via Materials>Add Material>Neo-Hookean
6. We created a step via Steps>Create Analysis Step

All parameters, node selections, and surface selections can be viewed in the sample file in this repositor.

