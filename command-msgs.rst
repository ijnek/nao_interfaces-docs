.. _command_msgs:

Command Msgs
############

.. warning::

   This package is deprecated as of ROS 2 J-turtle (and ROS 2 Rolling).
   A drop-in replacement for the interface packages are provided by the `Nao LoLA repository`_, please use that instead.

The package **nao_command_msgs** defines msgs used to send commands to the underlying
NAO hardware.

.. _command_joints:

Joints
******

JointPositions
==============

By being able to specify the indexes, we can have different nodes sending
partial joint position commands.

.. code-block:: python

    # Message to specify positions for the NAO's motor joints.
    #
    # Each joint is uniquely identified by its index (See JointIndexes.msg)
    #
    # The two arrays in this message should have the same size, where the first item
    # in indexes, corresponds to the first item in positions, etc.

    uint8[] indexes  # See JointIndexes.msg (eg. JointIndexes::HEADYAW)
    float32[] positions # radians

JointStiffnesses
================

By being able to specify the indexes, we can have different nodes sending
partial joint stiffness commands.

.. code-block:: python

    # Message to specify stiffnesses for the NAO's motor joints.
    #
    # Each joint is uniquely identified by its index (See JointIndexes.msg)
    #
    # The two arrays in this message should have the same size, where the first item
    # in indexes, corresponds to the first item in stiffnesses, etc.

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
.. _NAO LoLA repository: https://nao-lola.readthedocs.io/
