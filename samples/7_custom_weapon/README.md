# Demo 7 : Custom weapons

Here's the demo for the biggest part of this controller, the customization.

The controller was made with the idea of being extended without restriction. Thanks to Godot node system and to the GDScript's pythonic ability, it is possible to very easily add features without reimplementing everything. You only need to create the parts you need and register them in the weapon factory.

There are 6 main parts you can change:
* the data model, which contains all attributes concerning the player. It is not always needed to change it, especially if it's only to add some attributes since it has a modifier dictionnary which contains a dynamic list of attributes. Note: ammo automatic regeneration should be done here.
* the controller itself, if you need to add some core features to the controller itself. It should not contain any logic about weapons (that goes in weapon base) nor about the player himself (that goes in the data model).
* the weapon base, which is actually the weapon that the player wears. Imagine it like a gun or a rocket launcher that you get in your hand. So, it's not the bullet nor the impact that will be in the wall. The weapon base is a spatial node that will be physically attached to the weapon point of the controller. Consider that axis -Z (negative Z) is where the weapon base should point to, since the whole controller is looking in the direction of -Z as well.
* the projectile. Wether it's a fireball, a bouncing grenade or a laser ray, it is a spatial node that is generated by the weapon base. How it moves or behave is completely customized. A fireball will have a fixed_process that makes it move until it detects a collision in an area. A laser will stay attached to the weapon base and follow the camera's direction. And a grenade would be a rigid body with bouncing ability.
* the impact. It's usually an explosion but it can be anything. It's something created at the collision point (if the weapon base or projectile creates one) and that's all. The object must manage itself what it does. For instance, an explosion is merely a couple of particle nodes with an animation player that kills the node at the end of the animation.
* the weapon factory. It would be always required to extend the default one because it contains the preload paths to the new weapons or stuff you created. And in the various getter functions, you return the instance of your object if the name of the requested weapon, projectile, explosion or sound is matching the name of your object.

In this demo, the famous weapon from the Doom game was implemented. This weapon has the particularity that when it collides with something, all enemies that are visible in the camera are hit, no matter where they are. A custom weapon base, projectile and explosion were created for this gun.
