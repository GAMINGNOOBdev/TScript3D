# Documentation for the currently available library functions
> [!NOTE]
> Functions that are not covered in this file are not intended to be used by the end user.

## Namespace glm
### glm.vec
An n-dimensional vector data type.
- Constructor: `glm.vec(dataOrSizeOrVector, scalar=null)`
  If `dataOrSizeOrVector` is a vector, the data of given vector will be copied.
  If `dataOrSizeOrVector` is an array, it will be interpreted as a vector with the array length as the number of dimensions.
  If `dataOrSizeOrVector` is an integer, it will be interpreted as the number of dimensions, with `scalar` as the initial value for all components of the vector.
- `add(other)`: Adds two vectors together
- `sub(other)`: Subtracts two vectors from each other (this - other)
- `mul(other)`: Multiply this vector by other (either another vector or a scalar)
- `dot(other)`: Dot pruduct between this and the other vector
- `cross(other)`: Calculates the cross product between this and the other vector (only works with 3d vectors)
- `normalized()`: Returns this vector but normalized
- `length()`: Returns the vector length
For debugging:
- `printvec()`: Prints info about the vector using the standard `print` statement

### glm.vec2
Creates a 2D vector using x and y coordinates.
Function definition: `function vec2(x, y)`

### glm.vec3
Creates a 3D vector using x, y and z coordinates.
Function definition: `function vec3(x, y, z)`

### glm.vec4
Creates a 4D vector using x, y, z and w coordinates.
Function definition: `function vec4(x, y, z, w)`

### glm.mat4
A 4x4 matrix data type.
- Constructor: `glm.mat4(scalar,row2=null,row3=null,row4=null)`
  If `scalar` is a number, use it to set the matrix identity.
  If `scalar` is a vector/array, `row2`, `row3` and `row4` need to be set to their respective rows and `scalar` is interpreted as the first row of the matrix.
- `mul(other)`: Multiplies by either a 4d vector or another matrix


### glm.radians(angle)
Returns the angle in radians.

### glm.ortho(left, right, bottom, top, near, far)
Calculate an orthographic projection with set screen edges and near/far plane.

### glm.perspective(fovy, aspect, near, far)
Calculate a perspective projection using the vertical field of view, aspect ratio and near/far plane.

### glm.translate(m, v)
Translate a matrix `m` by vector `v`. (translate = "move")

### glm.rotate(m, angle, v)
Rotate a matrix `m` by `angle` on each axis in `v`.

### glm.scale(m, v)
Scale a matrix `m` by each axis with the values on `v`.

### glm.lookAt(eye, center, up)
Calculate the lookat vector from the eye, eye cenver and global up-vector.

## Namespace gl
> [!NOTE]
> The current implementation handles double buffering for a smoother experience.

### gl.glBeginDraw()
Begin drawing (needs to be called each frame)

### gl.glEndDraw()
End drawing (also needs to be called each frame)

### gl.glDrawTrianglesSlowButPretty(numTriangles, buffer, projection, model)
Draw `numTriangles` triangles from `buffer` using the given `projection` and the `model` matrix.
Only reason why it's "slow but pretty" is because of the lack of inlined matrix multiplications.

### gl.glDrawTriangles(numTriangles, buffer, projection, model)
Draw `numTriangles` triangles from `buffer` using the given `projection` and the `model` matrix.
This time optimized and most operations inlined for performance reasons.
