# Pearlboards ZMK Firmware (ZeusPad, Pearl 40% R2, Atlas65, Zeus TKL)

This is the ZMK firmware for all Pearlboards boards.
You can find more info on our projets here [Pearlboards](https://pearlboards.net/) here [Discord](https://discord.gg/SMuBMmPY) and here [CadlabCNC](https://cadlabcnc.com).
  <br>
  <br>
## Getting Started
### Thank you
- A huge thanks to the entire ZMK team for making all of this possible
### Overview
- By leveraging ZMk and GitHub Actions, this repo will automatically build a flashable firmware file for your PCB whenever a commit is pushed to it.
- For example, if you change your keymap and commit your changes, this repo will build your new firmware file which you can then flash.
### Setup
- If you have not already done so, create a GitHub account.
- Fork this repo.
- Enable GitHub Actions on your forked repo.
- More info here, but not necessary to proceed [ZMK Instructions](https://zmk.dev/docs/user-setup#summary).
  <br>
  <br>
## Building the firmware with GitHub Actions on your forked Repo
- Push a commit to trigger the build.
- Notice a 'firmware.zip' artifact from your latest hopefully successful Github Actions run for the build.
  <br>
  <br>
## Flashing the firmware
- Download the 'firmware.zip' artifact from your latest successful Github Actions run for the build.
- Unzip it and you should see a .uf2 file named after your specific PCB.
- Plug the PCB into your computer
    - Double press in quick succession the physical RESET button on your pcb
    - Right after ou should see the board mount as a USB device 'NRF52BOOT' (or similar if using a different controller) on your computer
    - Open that USB device in your file explorer, and copy or drag and drop the .uf2 for the right side into it
    - DO NOT WORRY IF IT FAILS WITH a '1 Interrupted Action' dialog popping up, asking you to Try Again, Skip or Cancel, as it has most likely been flashed at this point.
    - Once copied the devie will automatically disconnect and flash itself, most likely displaying the message above.
  <br>
  <br>
## Modifying your keyboards keymap
- You can edit the keymap in '/zmk-config/config/boards/arm/<keyboard>/<keyboard>.keymap' to suit your needs, and then build it with the instructions above.
    - For example, if you wanted to modify Pearls keymap, edit '/zmk-config/config/boards/arm/pearl/pearl.keymap'.
    - The encoder functionality (if supported on that PCB) can be changed in the keymap file as well
- All ZMK Keycodes found [here](https://zmk.dev/docs/codes).
  <br>
  <br>
## Specifying how many keyboards firmwares get built
- You can edit '/zmk-config/build.yaml' to include or exclude whichever keyboards you want.
- By default, all of the Pearlboards keyboards are set to build at once whenever a commit is pushed.
  <br>
  <br>
## Other ZMK configurations
- Feel free to poke around all the other board files and enable or disable whatever things you want.
    - This can be things such as underglow, debug logging, sleep timeouts etc..
 - If your build is not successfull at this point please do not blame me lol
 - More help can be found [here](https://discord.gg/jFzBGF6u5Q)
  <br>
  <br>
## Understanding ZMK Bluetooth keycodes and functionality
### Overview
- Generally upon being powered by USB or an internal battery, your keyboard will advertise itself as connectable via Bluetooth.
- Its at this point which you can pair it, and whatever 'profile number' is selected (defaults to 0) will be used up and connected to that specific device.

