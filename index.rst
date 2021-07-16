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

The :ref:`msgs` page explains all msg classes.

The :ref:`joints` page explains how to handle NAO joints in detail.

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