.. _msgs:

Nao msg files
#############

All ROS2 msgs in the nao_interfaces package are listed below.

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

.. _joint_positions:

JointPositions
==============

Joint positions in each motor joint, used both in receiving joint positions,
and commanding joint positions. When receiving joint positions, the position
array would be of length 25, and an empty indexes vector.

.. note::
    
    The message must be populated with either:
        * Equal length indexes and positions vectors
        * Positions array of length 25 with joint order specified in JointIndexes.msg, and an empty indexes vector

.. tip::
    
    The reason behind the messages having two options for populating, is because:
        * By not storing indexes, we can save on space, and not serialize.
        * On the other hand, by being able to specify the indexes, we can have different nodes sending
          joint position commands for different parts.

.. code-block:: python

    # A list of joint positions, corresponding to their indexes in the JointIndexes.msg.
    # The message must EITHER have:
    # - Equal length indexes and positions vectors
    # - Positions array of length 25 with joint order specified in JointIndexes.msg, and an empty indexes vector

    uint8[] indexes  # See JointIndexes.msg (eg. JointIndexes::HEADYAW)
    float32[] positions # radians

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

Joint stiffnesses in each motor joint, used both in receiving joint positions,
and commanding joint positions. Msg population is the same as in
:ref:`joint_positions`.


.. code-block:: python

    # A list of joint stiffnesses, corresponding to their indexes in the JointIndexes.msg.
    # The message must EITHER have:
    # - Equal length indexes and stiffnesses vectors
    # - Stiffnesses array of length 25 with joint order specified in JointIndexes.msg, and an empty indexes vector

    uint8[] indexes  # See JointIndexes.msg (eg. JointIndexes::HEADYAW)
    float32[] stiffnesses  # 0.0 - 1.0

JointTemperatures
=================

Temperature reported for each motor joint in the NAO.

.. tip::
    
    **The motor temperature is a simulated one**, using electric current value of the motor.
    The motor board implements a temperature limitation to protect the motor. The temperature limitation depends on robot version.

.. code-block:: python

    float32[25] temperatures  # Celcius (°C), in order of JointIndexes.msg

RGB Leds
********

Msgs that use `std_msgs/ColorRGBA`_ to specify colors for the RGB LEDs.

.. note::

    **Expect ranges for R, G and B are 0.0 - 1.0. The alpha value (A) is ignored.**

ChestLed
========

A single RGB led in the chest.

.. code-block:: python

    std_msgs/ColorRGBA color  # r, g, b should be 0.0 - 1.0. a is ignored

LeftEyeLeds
===========

See :ref:`left_eye_leds` to see which indexes correspond to which led.

.. code-block:: python

    std_msgs/ColorRGBA[8] colors

LeftFootLed
===========

A single RGB led in the left foot.

.. code-block:: python

    std_msgs/ColorRGBA color

RightEyeLeds
============

See :ref:`right_eye_leds` to see which indexes correspond to which led.

.. code-block:: python

    std_msgs/ColorRGBA[8] colors

RightFootLed
============

A single RGB led in the right foot.

.. code-block:: python

    std_msgs/ColorRGBA color


.. _blue_leds:

Blue Leds
*********

Msgs that specify intensity of the blue leds.

HeadLeds
========

See :ref:`head_leds` to see which indexes correspond to which led.

.. code-block:: python

    float32[12] intensities  # 0.0 - 1.0

LeftEarLeds
===========

See :ref:`left_ear_leds` to see which indexes correspond to which led.

.. code-block:: python

    float32[10] intensities  # 0.0 - 1.0

RightEarLeds
============

See :ref:`right_ear_leds` to see which indexes correspond to which led.

.. code-block:: python

    float32[10] intensities  # 0.0 - 1.0

RobotConfig
***********

.. code-block:: python

    string body_id  # eg."P0000073A07S94700012"
    string body_version  # eg. "6.0.0"
    string head_id  # eg. "P0000074A05S93M00061"
    string head_version  # eg. "6.0.0"


.. Joints
.. ******

.. See :ref:`joints` to see which indexes correspond to which joint

.. .. code-block:: python

..     float32[25] angles        # rad
..     float32[25] stiffnesses   # 0.0 - 1.0
..     float32[25] temperatures  # Celcius (°C)
..     float32[25] currents      # Amperes (A)
..     int32[25] statuses        # Temperature Status computed accordingly to the 
..                               # temperature limitation to protecting the motor.
..                               # 0: regular
..                               # 1: high, start to reduce stiffness
..                               # 2: very hot, stiffness reduced over 30%
..                               # 3: critically hot, stiffness is set to 0

Sonar
*****

Sonar distance measurements.

.. code-block:: python

    float32 left  # m
    float32 right  # m

SonarUsage
**********

Command to tell Lola whether to enable/disable the sonar.

.. code-block:: python

    bool left  # Set to true, to use left sonar
    bool right  # Set to true, to use right sonar

Touch
*****

.. code-block:: python

    bool head_front  # true if being touched
    bool head_middle  # true if being touched
    bool head_rear  # true if being touched

.. EyeLeds
.. *******

.. .. image:: images/eye_leds.png

.. Message identifying colors for each of the 16 RGB Leds in the NAO's eyes. **Expected range for R, G and B are 0.0 - 1.0. The alpha (A) is not used.**

.. See :ref:`eye_led_indexes` to see which indexes correspond to which led in the eyes.

.. .. code-block:: python

..     std_msgs/ColorRGBA[16] leds  # r, g, b should be 0.0 - 1.0. a is ignored

.. _std_msgs/ColorRGBA: http://docs.ros.org/en/api/std_msgs/html/msg/ColorRGBA.html