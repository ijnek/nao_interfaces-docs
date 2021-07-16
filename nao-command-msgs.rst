.. _nao_command_msgs:

NAO Command Msgs
################

.. _command_joints:

Joints
******

JointIndexes
============

A msg file that defines the indexes used across all joint msgs.
This msg does not have any fields, and doesn't serve a purpose in transmitting
any information on topics. Examples of using this msg are shown in :ref:`joints`.

.. _command_joint_positions:

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

JointStiffnesses
================

Joint stiffnesses in each motor joint, used both in receiving joint positions,
and commanding joint positions. Msg population is the same as in
:ref:`command_joint_positions`.


.. code-block:: python

    # A list of joint stiffnesses, corresponding to their indexes in the JointIndexes.msg.
    # The message must EITHER have:
    # - Equal length indexes and stiffnesses vectors
    # - Stiffnesses array of length 25 with joint order specified in JointIndexes.msg, and an empty indexes vector

    uint8[] indexes  # See JointIndexes.msg (eg. JointIndexes::HEADYAW)
    float32[] stiffnesses  # 0.0 - 1.0

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

SonarUsage
**********

Command to tell Lola whether to enable/disable the sonar.

.. code-block:: python

    bool left  # Set to true, to use left sonar
    bool right  # Set to true, to use right sonar

.. _std_msgs/ColorRGBA: http://docs.ros.org/en/api/std_msgs/html/msg/ColorRGBA.html