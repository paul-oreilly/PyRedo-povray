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
	requires 
	    unlabeled position <Point>
	    unlabeled color <Color>
	has labels shadowless parallel jitter circular orient
	has selection light_type [spotlight, cylinder]
	has values 
	    radius falloff tightness <Number>
	    point_at <Spot>
	    area_light <AreaLight>
	    adaptive <Int>
	    area_illumination <OnOff>
	    looks_like <POVObject>
	    fade_distance fade_power <Number>
	    media_attenuation media_interaction <OnOff>
	    value projected_through <POVObject>
	has subtemplate AreaLight
	format for povray (all): light_source {{ {position} {color} {content} }}
	
	
	AreaLight
	---------
	requires 
	    axis1 axis2 <Vector3>
	    size1 size2 <Number>
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
	
