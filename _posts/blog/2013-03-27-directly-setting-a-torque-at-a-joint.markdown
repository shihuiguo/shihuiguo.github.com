---
layout: post
status: publish
published: true
title: Directly Setting A Torque at A Joint In Bullet
author: Shihui Guo
author_login: yierbosimao
author_email: mr.shihuiguo@gmail.com
excerpt: "In ODE(Open Dynamic Engine), Motors allow you to set joint velocities directly.
  However, you may instead wish to set the torque or force at a joint instead. These
  functions do just that. Note that they don't affect the motor, but simply call dBodyAddForce
  dBodyAddTorque on the bodies attached to it.\r\n<pre>\r\n<code>\r\nvoid dJointAddHingeTorque(
  dJointID j, dReal torque )\r\n{\r\n    dxJointHinge* joint = ( dxJointHinge* )j;\r\n
  \   dVector3 axis;\r\n    dAASSERT( joint );\r\n    checktype( joint, Hinge );\r\n\r\n
  \   if ( joint->flags & dJOINT_REVERSE )\r\n        torque = -torque;\r\n\r\n    getAxis(
  joint, axis, joint->axis1 );\r\n    axis[0] *= torque;\r\n    axis[1] *= torque;\r\n
  \   axis[2] *= torque;\r\n\r\n    if ( joint->node[0].body != 0 )\r\n        dBodyAddTorque(
  joint->node[0].body, axis[0], axis[1], axis[2] );\r\n    if ( joint->node[1].body
  != 0 )\r\n        dBodyAddTorque( joint->node[1].body, -axis[0], -axis[1], -axis[2]
  );\r\n}\r\n</code>\r\n</pre>\r\n"
wordpress_id: 447
wordpress_url: http://www.guoshihui.net/?p=447
date: '2013-03-27 23:10:01 +0800'
date_gmt: '2013-03-27 23:10:01 +0800'
categories:
- blog
- bullet
- cg
tags: []
comments: []
---
<p>In ODE(Open Dynamic Engine), Motors allow you to set joint velocities directly. However, you may instead wish to set the torque or force at a joint instead. These functions do just that. Note that they don't affect the motor, but simply call dBodyAddForce dBodyAddTorque on the bodies attached to it.</p>
<pre>
<code>
void dJointAddHingeTorque( dJointID j, dReal torque )
{
    dxJointHinge* joint = ( dxJointHinge* )j;
    dVector3 axis;
    dAASSERT( joint );
    checktype( joint, Hinge );

    if ( joint->flags & dJOINT_REVERSE )
        torque = -torque;

    getAxis( joint, axis, joint->axis1 );
    axis[0] *= torque;
    axis[1] *= torque;
    axis[2] *= torque;

    if ( joint->node[0].body != 0 )
        dBodyAddTorque( joint->node[0].body, axis[0], axis[1], axis[2] );
    if ( joint->node[1].body != 0 )
        dBodyAddTorque( joint->node[1].body, -axis[0], -axis[1], -axis[2] );
}
</code>
</pre>
<p><a id="more"></a><a id="more-447"></a><br />
That is, it applies a torque with magnitude torque, in the direction of the hinge axis, to body 1, and with the same magnitude but in opposite direction to body 2. This function is just a wrapper for dBodyAddTorque.</p>
<p>There is no such implementation in bullet, but surely we can implement it by ourselves. For example if you have a hinge btHingeConstraint* pHinge you may get its axis in world space and apply a torque T to both bodies:</p>
<pre><code>
btVector3 hingeAxisLocal = pHinge->getAFrame().getBasis().getColumn(2); // z-axis of constraint frame
btVector3 hingeAxisWorld = pHinge->getRigidBodyA().getWorldTransform().getBasis() * hingeAxisLocal;
btVector3 hingeTorque = T * hingeAxisWorld;
pHinge->getRigidBodyA().applyTorque(hingeTorque);
pHinge->getRigidBodyB().applyTorque(-hingeTorque);
</code></pre>
<p>Bullet has a wider feature of complete collision detection, softbody etc, but in modelling rigid body links, it doesn't have advantage over ODE. One of its major issues here is not being stable in the case of large mass ratio (two neighbour objects have significantly different mass, such as a robotic finger linked to an arm).</p>
<p>References:<br />
<a href="http://ode-wiki.org/wiki/index.php?title=Manual:_Joint_Types_and_Functions#Setting_Joint_Torques.2FForces_Directly">ODE WIKI</a><br />
<a href="http://sourceforge.net/projects/opende/files/">ODE Source Code</a><br />
<a href="http://www.bulletphysics.org/Bullet/phpBB3/viewtopic.php?f=9&t=4871">Bullet Forum Post</a><br />
<a href="http://www.bulletphysics.org/Bullet/phpBB3/viewtopic.php?f=9&t=5033&hilit=joint+torque">Bullet Forum Post</a></p>
