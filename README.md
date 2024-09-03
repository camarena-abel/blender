<!--
Keep this document short & concise,
linking to external resources instead of including content in-line.
See 'release/text/readme.html' for the end user read-me.
-->

About this fork branch
======================

The idea behind this modification is to assign a unique number to each vertex, which will serve as a unique identifier within the mesh. This allows you to edit the mesh by adding or deleting vertices, and then easily determine which vertices are new and which are not. To achieve this, new vertices will have the value -1, while the old ones will retain their original identifier.

To make this work, this Blender modification allows you to create an integer attribute layer (on the vertices), which name must start with "skip". The values in this layer will not be interpolated or copied during many mesh editing operations. Keep in mind that this functionality does not apply to all operations, and in some operations like "Inset", you will need to uncheck the "[x] Interpolate" checkbox in the operator.

To experiment with this functionality on the sample cube, you can run this script and modify the cube while observing the values in the "skipID" attribute layer using Blender's Spreadsheet.

	import bpy

	mesh = bpy.context.collection.objects["Cube"].data
	attribute = mesh.attributes.new(name="skipID", type="INT", domain="POINT")
	attribute_values = [i for i in range(len(mesh.vertices))]
	attribute.data.foreach_set("value", attribute_values)  

![per vertex id](https://github.com/camarena-abel/blender/blob/blender-v4.2-mod/_screenshots/minus-one-mod.png?raw=true)    

Blender
=======

Blender is the free and open source 3D creation suite.
It supports the entirety of the 3D pipeline-modeling, rigging, animation, simulation, rendering, compositing,
motion tracking and video editing.

![Blender screenshot](https://code.blender.org/wp-content/uploads/2018/12/springrg.jpg "Blender screenshot")

Project Pages
-------------

- [Main Website](http://www.blender.org)
- [Reference Manual](https://docs.blender.org/manual/en/latest/index.html)
- [User Community](https://www.blender.org/community/)

Development
-----------

- [Build Instructions](https://developer.blender.org/docs/handbook/building_blender/)
- [Code Review & Bug Tracker](https://projects.blender.org)
- [Developer Forum](https://devtalk.blender.org)
- [Developer Documentation](https://developer.blender.org/docs/)


License
-------

Blender as a whole is licensed under the GNU General Public License, Version 3.
Individual files may have a different, but compatible license.

See [blender.org/about/license](https://www.blender.org/about/license) for details.
