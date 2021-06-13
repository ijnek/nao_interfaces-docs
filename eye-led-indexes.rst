.. _eye_led_indexes:

Eye Led Indexes
###############

.. image:: images/eye_leds.png

The following list is from ``EyeLeds.msg``:

.. code-block:: cpp

  int32 L0=0
  int32 L1=1
  int32 L2=2
  int32 L3=3
  int32 L4=4
  int32 L5=5
  int32 L6=6
  int32 L7=7
  int32 R0=8
  int32 R1=9
  int32 R2=10
  int32 R3=11
  int32 R4=12
  int32 R5=13
  int32 R6=14
  int32 R7=15
  int32 NUM_EYE_LEDS=16

Setting color for one led
**************************

.. code-block:: cpp

    // Set led L0 to red
    nao_interfaces::msg::EyeLeds eye_leds;
    eye_leds.leds[nao_interfaces::msg::EyeLeds::L0].r = 1.0;

Setting color for all leds
**************************

To populate all LEDs to be a certain color, you can iterate over ``nao_interfaces::msg::EyeLeds::NUM_EYE_LEDS``.

.. code-block:: cpp

    // Set all leds to yellow
    nao_interfaces::msg::EyeLeds eye_leds;

    std_msgs/ColorRGBA yellow;
    yellow.r = 1.0;
    yellow.g = 1.0;

    for (unsigned i = 0; i < nao_interfaces::msg::EyeLeds::NUM_EYE_LEDS; ++i)
    {
      eye_leds.leds[i] = yellow;
    }