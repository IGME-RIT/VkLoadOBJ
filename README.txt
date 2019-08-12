To load OBJs, we need to adjust our Vertex Structure to hold 
vertex normals. These normals can be used for lighting, which
will come in a future tutorial. We add a place for normals now,
because OBJ files have normals. We also rename the 
prepare_textures to prepare_texture, with one parameter
for the file that gets loaded, then we change prepare_vb_ib to
take one file as a parameter. Rather than having a fixed vertex
and index buffer hardcoded into a header file, we load it from
the file. For more information on how the OBJ file works, please
look at our OpenGL OBJ loader tutorial. We also have to change
the pipelineCreateInfo to adjust for our new Vertex Structure.
We also change our Index Buffer from 32-bit to 16-bit, which
requires less memory, and gives us the same results. This change
takes place in prepare_vb_ib() and when we bind our pipeline
to the command buffer. In future tutorials, we will be seperating
Demo into Mesh, Texture, and Entity classes. Inside our Demo.h
class, we put a temporary variable "numIndices" to hold the amount
of indices in our OBJ, which will be used for our VkCmdDrawIndexed
command. In the future, this will be moved to a Mesh class