.. code_light_source:

*************
Light Sources
*************



Template
========

The template used to generate the python class for a light source

.. pyRedo ::

	LightSource
	-----------
	extends Transformable
	requires unlabeled position <Point>
	requires unlabeled color <Color>
	has labels shadowless parallel
	has selection light_type [spotlight, cylinder]
	has values radius falloff tightness <Number>
	has value point_at <Spot>
	has value area_light <AreaLight>
	has value adaptive <Int>
	has value area_illumination <OnOff>
	has labels jitter circular orient
	has looks_like <POVObject>
	has fade_distance fade_power <Number>
	has values media_attenuation media_interaction <OnOff>
	has value projected_through <POVObject>
	has subtemplate AreaLight
	format for povray (all): light_source {{ {position} {color} {content} }}
	
	
	AreaLight
	---------
	requires axis1 axis2 <Vector3>
	requires size1 size2 <Number>
	format for povray (all): area_light {axis1} {axis2} {size1} {size2}
	
	
	

POVRay Specification
====================

	LIGHT_SOURCE:
	  light_source {
	    <Location>, COLOR
	    [LIGHT_MODIFIERS...]
	    }
	LIGHT_MODIFIER:
	  LIGHT_TYPE | SPOTLIGHT_ITEM | AREA_LIGHT_ITEMS |
	  GENERAL_LIGHT_MODIFIERS
	LIGHT_TYPE:
	  spotlight | shadowless | cylinder | parallel
	SPOTLIGHT_ITEM:
	  radius Radius | falloff Falloff | tightness Tightness |
	  point_at <Spot>
	PARALLEL_ITEM:
	  point_at <Spot>
	AREA_LIGHT_ITEM:
	  area_light <Axis_1>, <Axis_2>, Size_1, Size_2 |
	  adaptive Adaptive | area_illumination [Bool] |
	  jitter | circular | orient
	GENERAL_LIGHT_MODIFIERS:
	  looks_like { OBJECT } |
	  TRANSFORMATION fade_distance Fade_Distance |
	  fade_power Fade_Power | media_attenuation [Bool] |
	  media_interaction [Bool] | projected_through
	
