.. _joints:

Joints
######

Tutorials
*********

Reading a joint position from sensor
====================================

To read a joint position for a specific joint:

.. code-block:: cpp

    // Assume joints is of type nao_sensor_msgs::msg::JointPositions
    joints.positions[nao_sensor_msgs::msg::JointIndexes::HEADYAW]

:ref:`nao_sensor_msgs::msg::JointPositions<sensor_joint_positions>` contains an
array of joint positions for all joints of the NAO. The indexes for each joint
are stored as constants in :ref:`nao_sensor_msgs::msg::JointIndexes<joint_indexes>`.

Writing a joint position command
================================

**To populate the message,**

* Append index of the joint to the `indexes` vector
* Append position of the joint to the `positions` vector

For example:

.. code-block:: cpp

    // Assume joints is of type nao_sensor_msgs::msg::JointPositions
    nao_command_msgs::msg::JointPositions command;

    command.indexes.push_back(nao_command_msgs::msg::JointIndexes::HEADYAW);
    command.positions.push_back(0.2);

.. note::

    Joint indexes are stored as constants in :ref:`nao_command_msgs::msg::JointIndexes<joint_indexes>`.


Iterating over all joints
=========================

To iterate over all joints, use a for loop that iterates ``NUM_JOINTS`` times to iterate over all joints, as following:

.. code-block:: cpp

    // Create JointStiffness command with stiffness 1.0 for all joints
    nao_command_msgs::msg::JointStiffnesses command;

    for (unsigned i = 0; i < nao_command_msgs::msg::JointIndexes::NUMJOINTS; ++i)
    {
        command.indexes.push_back(i);
        command.positions.push_back(1.0);
    }

.. _joint_indexes:    

Joint Indexes
*************

A msg file that defines the indexes of joints as constants.
Used in indexes for :ref:`Sensor Joint Msgs<sensor_joints>` and :ref:`Command Joint Msgs<command_joints>`.

This msg does not have any fields, and doesn't serve a purpose in transmitting
any information on topics.

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

.. note::

    Currently, there are two identical copies of  :ref:`joint_indexes` msg file,
    in the :ref:`sensor_msgs` and :ref:`command_msgs` package.
    This is because we haven't found a nice way to avoid duplication.
    Possibly, this shouldn't even be a msg file but should be just a plain hpp file.