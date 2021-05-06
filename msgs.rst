msgs
####

Accelerometer
*************

.. code-block:: cpp

    float32 x
    float32 y
    float32 z

Angle
*****

.. code-block:: cpp

    float32 x
    float32 y

Battery
*******

.. code-block:: cpp

    float32 charge
    float32 status
    float32 current
    float32 temperature

Buttons
*******

.. code-block:: cpp

    bool chest
    bool l_foot_bumper_left
    bool l_foot_bumper_right
    bool r_foot_bumper_left
    bool r_foot_bumper_right

FSR
***

.. code-block:: cpp

    float32 l_foot_front_left
    float32 l_foot_front_right
    float32 l_foot_back_left
    float32 l_foot_back_right
    float32 r_foot_front_left
    float32 r_foot_front_right
    float32 r_foot_back_left
    float32 r_foot_back_right

Gyroscope
*********

.. code-block:: cpp

    float32 x
    float32 y
    float32 z

Joints
******

.. code-block:: cpp

    float32[25] angles
    float32[25] stiffnesses
    float32[25] temperatures
    float32[25] currents

Sonar
*****

.. code-block:: cpp

    float32 left
    float32 right

Touch
*****

.. code-block:: cpp

    bool head_front
    bool head_middle
    bool head_rear
