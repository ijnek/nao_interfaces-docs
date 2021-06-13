.. _joint_indexes:

Joint Indexes
#############

The following list are the joint indexes copied from ``Joints.msg``:

.. code-block:: cpp

    int32 HEADYAW=0
    int32 HEADPITCH=1
    int32 LSHOULDERPITCH=2
    int32 LSHOULDERROLL=3
    int32 LELBOWYAW=4
    int32 LELBOWROLL=5
    int32 LWRISTYAW=6
    int32 LHIPYAWPITCH=7
    int32 LHIPROLL=8
    int32 LHIPPITCH=9
    int32 LKNEEPITCH=10
    int32 LANKLEPITCH=11
    int32 LANKLEROLL=12
    int32 RHIPROLL=13
    int32 RHIPPITCH=14
    int32 RKNEEPITCH=15
    int32 RANKLEPITCH=16
    int32 RANKLEROLL=17
    int32 RSHOULDERPITCH=18
    int32 RSHOULDERROLL=19
    int32 RELBOWYAW=20
    int32 RELBOWROLL=21
    int32 RWRISTYAW=22
    int32 LHAND=23
    int32 RHAND=24
    int32 NUMJOINTS=25

Accessing a joint angle
***********************

An example of accessing an angle for a specific joint:

.. code-block:: cpp

    joints.angles[nao_interfaces::msg::Joints::HEADYAW]

Iterating over all joints
*************************

``nao_interfaces::msg::Joints::NUM_JOINTS`` can be used for iterating over all joints, as following:

.. code-block:: cpp

    for (unsigned i = 0; i < nao_interfaces::msg::Joints::NUMJOINTS; ++i)
    {
        // do something for each joint
    }
