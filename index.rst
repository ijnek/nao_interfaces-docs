.. nao_interfaces documentation master file, created by
   sphinx-quickstart on Thu May  6 14:00:20 2021.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Nao Interfaces
==============

This is a `ROS2 interface package`_ for the Softbank NAO robot.
Custom message types specific to the NAO robot are defined in
this package, and are explained in these docs.

The project is hosted on `Github`_.

:ref:`nao_sensor_msgs` page explains all msgs that hold sensor information, such as joint angles,
sonar readings, etc.

:ref:`nao_command_msgs` page explains all msgs to command the robot, to move joints,
light up leds, etc.

:ref:`joints` page explains how to handle NAO joints in detail.

:ref:`leds` page describes the name and position of each led on the robot,
and how to set the intensity and color for them.

.. toctree::
   :hidden:
   :maxdepth: 2
   :caption: Contents:

   nao-sensor-msgs
   nao-command-msgs
   joints
   leds
   related-ros2-packages

.. _ROS2 interface package: https://docs.ros.org/en/foxy/Tutorials/Custom-ROS2-Interfaces.html
.. _Github: https://github.com/ijnek/nao_interfaces