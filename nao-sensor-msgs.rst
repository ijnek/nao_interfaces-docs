.. _nao_sensor_msgs:

NAO Sensor Msgs
###############

Accelerometer
*************

.. image:: /images/accelerometer.png

Units are in m/s :sup:`2`

Note that gravity is measured by an accelerometer.
When standing, the robot will measure 9.8 m/s :sup:`2` POSITIVE in the z-direction, since its 
receiving an acceleration upwards from the floor when compared to a freefall state.

.. code-block:: python

    float32 x  # m/s/s
    float32 y  # m/s/s
    float32 z  # m/s/s

Angle
*****

.. image:: /images/angle.png

Units are in rad.

.. code-block:: python

    float32 x  # rad
    float32 y  # rad

Battery
*******

.. code-block:: python

    float32 charge  # 0% - 100%
    bool charging  # True if robot is getting charged
    float32 current  # In Amperes, negative for discharge, positive for charge
    float32 temperature  # Celcius (°C)

Buttons
*******

.. code-block:: python

    bool chest  # true if being pressed
    bool l_foot_bumper_left  # true if being pressed
    bool l_foot_bumper_right  # true if being pressed
    bool r_foot_bumper_left  # true if being pressed
    bool r_foot_bumper_right  # true if being pressed

FSR
***

.. code-block:: python

    float32 l_foot_front_left  # kg
    float32 l_foot_front_right  # kg
    float32 l_foot_back_left  # kg
    float32 l_foot_back_right  # kg
    float32 r_foot_front_left  # kg
    float32 r_foot_front_right  # kg
    float32 r_foot_back_left  # kg
    float32 r_foot_back_right  # kg

Gyroscope
*********

.. image:: /images/gyroscope.png

Units are in rad/s.

.. code-block:: python

    float32 x  # rad/s
    float32 y  # rad/s
    float32 z  # rad/s

Joints
******

JointCurrents
=============

Electrical current, reported from the current sensors in each motor joint
of the NAO.

.. code-block:: python

    float32[25] currents  # Amperes (A), in order of JointIndexes.msg

JointIndexes
============

A msg file that defines the indexes used across all joint msgs.
This msg does not have any fields, and doesn't serve a purpose in transmitting
any information on topics. Examples of using this msg are shown in :ref:`joints`.

JointPositions
==============

Joint positions in each motor joint.

.. code-block:: python

    # An array of joint positions, corresponding to their indexes in the JointIndexes.msg.

    float32[25] positions # radians

JointStatuses
=============

Temperature status enums, computed accordingly to the temperature limitation to protect the motors.

.. code-block:: python
    
    int32 STATUS_NORMAL=0          # normal
    int32 STATUS_HOT=1             # high, start to reduce stiffness
    int32 STATUS_VERY_HOT=2        # very hot, stiffness reduced over 30%
    int32 STATUS_CRITICALLY_HOT=3  # critically hot, stiffness is set to 0

    int32[25] statuses  # Status codes, in order of JointIndexes.msg

JointStiffnesses
================

Joint stiffnesses in each motor joint.

.. code-block:: python

    # An array of joint stiffnesses, corresponding to their indexes in the JointIndexes.msg.

    float32[25] stiffnesses  # 0.0 - 1.0

JointTemperatures
=================

Temperature reported for each motor joint in the NAO.

.. tip::
    
    **The motor temperature is a simulated one**, using electric current value of the motor.
    The motor board implements a temperature limitation to protect the motor. The temperature limitation depends on robot version.

.. code-block:: python

    float32[25] temperatures  # Celcius (°C), in order of JointIndexes.msg

RobotConfig
***********

.. code-block:: python

    string body_id  # eg."P0000073A07S94700012"
    string body_version  # eg. "6.0.0"
    string head_id  # eg. "P0000074A05S93M00061"
    string head_version  # eg. "6.0.0"

Sonar
*****

Sonar distance measurements.

.. code-block:: python

    float32 left  # m
    float32 right  # m

Touch
*****

.. code-block:: python

    bool head_front  # true if being touched
    bool head_middle  # true if being touched
    bool head_rear  # true if being touched
