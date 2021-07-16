.. _joints:

Joints
######

Tutorials
*********

Accessing a joint angle
=======================

An example of accessing an angle for a specific joint:

.. code-block:: cpp

    joints.angles[nao_interfaces::msg::JointIndexes::HEADYAW]

Iterating over all joints
=========================

``nao_interfaces::msg::JointIndexes::NUM_JOINTS`` can be used for iterating over all joints, as following:

.. code-block:: cpp

    for (unsigned i = 0; i < nao_interfaces::msg::JointIndexes::NUMJOINTS; ++i)
    {
        // do something for each joint
    }

Joint Indexes
*************

The following list are the joint indexes copied from ``JointIndexes.msg``:

.. code-block:: cpp

    uint8 HEADYAW=0
    uint8 HEADPITCH=1
    uint8 LSHOULDERPITCH=2
    uint8 LSHOULDERROLL=3
    uint8 LELBOWYAW=4
    uint8 LELBOWROLL=5
    uint8 LWRISTYAW=6
    uint8 LHIPYAWPITCH=7
    uint8 LHIPROLL=8
    uint8 LHIPPITCH=9
    uint8 LKNEEPITCH=10
    uint8 LANKLEPITCH=11
    uint8 LANKLEROLL=12
    uint8 RHIPROLL=13
    uint8 RHIPPITCH=14
    uint8 RKNEEPITCH=15
    uint8 RANKLEPITCH=16
    uint8 RANKLEROLL=17
    uint8 RSHOULDERPITCH=18
    uint8 RSHOULDERROLL=19
    uint8 RELBOWYAW=20
    uint8 RELBOWROLL=21
    uint8 RWRISTYAW=22
    uint8 LHAND=23
    uint8 RHAND=24
    uint8 NUMJOINTS=25
