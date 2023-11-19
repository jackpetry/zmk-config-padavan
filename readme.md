# Padavan ZMK firmware

_A minivan keyboard with small numpad and wireless capabilities._

## HOW TO USE

- fork this repo
- `git clone` your repo, to create a local copy on your PC (you can use the [command line](https://www.atlassian.com/git/tutorials) or [github desktop](https://desktop.github.com/))
- adjust the padavan.keymap file (find all the keycodes on [the zmk docs pages](https://zmk.dev/docs/codes/))
- `git push` your repo to your fork
- on the GitHub page of your fork navigate to "Actions"
- scroll down and unzip the `firmware.zip` archive that contains the latest firmware
- connect the padavan to your PC, press reset and hold the boot key during reset
- the keyboard should now appear as a mass storage device
- drag'n'drop the `padavan-nice_nano_v2-zmk.uf2` file from the archive onto the storage device

## Troubeshooting

On macOs you might get an error stating that the `operation can’t be completed unexpected error 100093`. You can circumvent this by copying the file from your terminal:

- move the `padavan-nice_nano_v2-zmk.uf2` to your root directory
- copy the file onto the padavan volume: `cp -X padavan-nice_nano_v2-zmk.uf2 ../../Volumes/<volume_name>/`
