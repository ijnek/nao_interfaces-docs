msgs
####

Accelerometer
*************

.. image:: /images/accelerometer.png

Units are in m/s :sup:`2`

Note that gravity is measured by an accelerometer.
When standing, the robot will measure 9.8 m/s :sup:`2` POSITIVE in the z-direction, since its 
receiving an acceleration upwards from the floor when compared to a freefall state.

.. code-block:: cpp

    float32 x  // m/s/s
    float32 y  // m/s/s
    float32 z  // m/s/s

Angle
*****

.. image:: /images/angle.png

Units are in rad.

.. code-block:: cpp

    float32 x  // rad
    float32 y  // rad

Battery
*******

.. code-block:: cpp

    float32 charge  // 0% - 100%
    float32 status
    float32 current  // in A, negative for discharge, positive for charge
    float32 temperature  // Celcius (°C)

Buttons
*******

.. code-block:: cpp

    bool chest  // true if being pressed
    bool l_foot_bumper_left  // true if being pressed
    bool l_foot_bumper_right  // true if being pressed
    bool r_foot_bumper_left  // true if being pressed
    bool r_foot_bumper_right  // true if being pressed

FSR
***

.. code-block:: cpp

    float32 l_foot_front_left  // kg
    float32 l_foot_front_right  // kg
    float32 l_foot_back_left  // kg
    float32 l_foot_back_right  // kg
    float32 r_foot_front_left  // kg
    float32 r_foot_front_right  // kg
    float32 r_foot_back_left  // kg
    float32 r_foot_back_right  // kg

Gyroscope
*********

.. image:: /images/gyroscope.png

Units are in rad/s.

.. code-block:: cpp

    float32 x  // rad/s
    float32 y  // rad/s
    float32 z  // rad/s

Joints
******

See :ref:`joint_indexes` to see which indexes correspond to which joint

.. code-block:: cpp

    float32[25] angles  // rad
    float32[25] stiffnesses  // 0.0 - 1.0
    float32[25] temperatures  // Celcius (°C)
    float32[25] currents  // Amperes (A)

Sonar
*****

.. code-block:: cpp

    float32 left  // m
    float32 right  // m

Touch
*****

.. code-block:: cpp

    bool head_front  // true if being touched
    bool head_middle  // true if being touched
    bool head_rear  // true if being touched
