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

## Adjusting for alternative bottom row layouts

The default layout uses three 1u keys on the bottom left and a big bar (6.25u).
The PCB offers two optional alternatives:
- (a) Two 1.5u keys on the bottom left
- (b) Split bar layout: 1u, 2u, 2.25u, 1u

To make your firmware conform to whatever layout you want to use, you'll have to change the following line in the file `config/boards/shields/padavan/padavan.overlay`:
```
        zmk,matrix_transform = &default_transform; // Change this line to the layout you want to use!
```
Here, exchange `&default_transform` for the appropriate layout:
- Default (no a, no b):  
  `&default_transform` for using three 1u bottom-left keys with 6.25u space bar
- Alt Bottom (yes a, no b):  
  `&alt_bottom_big_bar_transform` for using two 1.5u bottom-left keys with 6.25u space bar
- Split Bar (no a, yes b):  
  `&split_bar_transform` for using three 1u bottom-left keys with split bars
- Alt Bottom Split Bar (yes a, yes b):  
  `&alt_bottom_split_bar_transform` for using two 1.5u bottom-left keys with split bars
- Everything everywhere all at once:  
  `&everything_transform` for having all the options in the same firmware (mileage may vary)


## Troubeshooting

On macOs you might get an error stating that the `operation can’t be completed unexpected error 100093`. You can circumvent this by copying the file from your terminal:

- move the `padavan-nice_nano_v2-zmk.uf2` to your root directory
- copy the file onto the padavan volume: `cp -X padavan-nice_nano_v2-zmk.uf2 ../../Volumes/<volume_name>/`
