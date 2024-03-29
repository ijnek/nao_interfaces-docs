.. nao_interfaces documentation master file, created by
   sphinx-quickstart on Thu May  6 14:00:20 2021.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Nao Interfaces
==============

.. warning::

   This package is deprecated as of ROS 2 J-turtle (and ROS 2 Rolling).
   A drop-in replacement for the interface packages are provided by the `Nao LoLA repository`_, please use that instead.

This is a `ROS2 interface package`_ for the Aldebaran NAO robot.
Custom message types specific to the NAO robot are defined in
this package, and are explained in these docs.

The project is hosted on `Github`_.

:ref:`sensor_msgs` page explains all msgs that can be used to read sensor information, such as joint angles,
sonar readings, etc.

:ref:`command_msgs` page explains all msgs that can be used to command the robot, to move joints,
light up leds, etc.

:ref:`joints` page explains in detail, how to read sensor information and write commands for the NAO's joints, along
with some examples.

:ref:`leds` page describes in detail, the name and position of each led on the robot,
with examples on how to set the intensity and color for them.

.. toctree::
   :hidden:
   :maxdepth: 2

   sensor-msgs
   command-msgs
   joints
   leds
   related-ros2-packages

.. _ROS2 interface package: https://docs.ros.org/en/galactic/Tutorials/Custom-ROS2-Interfaces.html
.. _Github: https://github.com/ijnek/nao_interfaces
.. _NAO LoLA repository: https://nao-lola.readthedocs.io/
