# MigitePad
MigitePad! A Numpad/Nav Cluster with Kailh Hotswap/OLED/Rotary Encoder! 
Even reversable for you crazies who want a backwards Numpad!*
*OLED will need to be trace cut and bodged if you want it to work backwards

Material needed:
31x Kailh Hotswap Sockets (Technically optional, hotswap through holes are plated)
31x 1N4148 or SOD-123F Diodes
31x MX style switches
1x MJTP1117 Reset Switch
1x Pro Micro or equivilant (Pro Micro chip side up for normal orientation, bottom side up for reversed.)
3x 2u stabilizers
1x EC11 Rotary Encoder
1x SSD1306 OLED (Optional)

For the 3D Printable Case:
6x 6mm M2 standoffs
12x M2 4mm or 5mm screws

OLED and Rotary Encoder code would need to be added to the end of your keymap.c. Still working on a more official OLED config. Example borrowed and tested as working from the RoMac+:

void encoder_update_user(uint8_t index, bool clockwise) {
    switch (index) {
        /* Top-right encoder (scanning) */
        case 0:
            tap_code(clockwise ? KC_VOLD : KC_VOLU);
            break;
    }
}

#ifdef OLED_DRIVER_ENABLE
oled_rotation_t oled_init_user(oled_rotation_t rotation) {
    return OLED_ROTATION_270;  // flips the display 180 degrees if offhand
}
void oled_task_user(void) {
  // Host Keyboard Layer Status
  oled_write_P(PSTR("Let's\nbuild\nsome-\nthing\nto-\nget-\nher!"), false);
  switch (get_highest_layer(layer_state)) {
    case BASE:
      oled_write_ln_P(PSTR(""), false);
      break;
    case FN:
      oled_write_ln_P(PSTR("FN"), false);
      break;
    default:
      // Or use the write_ln shortcut over adding '\n' to the end of your string
      oled_write_ln_P(PSTR("Undef"), false);
  }

  // Host Keyboard LED Status
  uint8_t led_usb_state = host_keyboard_leds();
  oled_write_P(IS_LED_ON(led_usb_state, USB_LED_NUM_LOCK) ? PSTR("NLCK ") : PSTR("     "), false);
  oled_write_P(IS_LED_ON(led_usb_state, USB_LED_CAPS_LOCK) ? PSTR("CAPS ") : PSTR("       "), false);
  oled_write_P(IS_LED_ON(led_usb_state, USB_LED_SCROLL_LOCK) ? PSTR("SCRLK") : PSTR("       "), false);
}
#endif


