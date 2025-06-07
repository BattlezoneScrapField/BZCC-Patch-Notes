<p align="center">
  <img width="80%" src="./BZCC.png">
</p>

# File Updates
A list of files that were updated since `2.0.185.0`:
| Filename             | Change |
|----------------------|-----------------|
| `Gameprefs.ini`      | Restored a bunch of Gameprefs options that were previously in BZ2 1.3. Updated `Gameprefs.ini` with new (and old) options. |
| `launch.ini`         | Added command line argument `/modid`. If set to a Workshop ID, it initializes the game’s `launch.ini` to that mod, activating it on startup. |
| `localization_table.csv` | Variety of localization updates. |
| `bzgame_init.cfg`    | Split up `bzgame_init.cfg` into 4 new cfgs: `bzgame_init_color.cfg`, `bzgame_init_cursor.cfg`, `bzgame_init_font.cfg`, and `bzgame_init_sound.cfg`. These 4 are called from the root `bzgame_init.cfg`. Commented out the lines in the stock `bzgame_init.cfg` |
| `bzshell_loadbar.cfg`    | Added support for LoadBar to be configurable by cfg. |
| `bzgame_moves.cfg`   | Removed deprecated config `bzgame_moves.cfg` and commented out unused variables in `Gameprefs.ini`. |
| `bzgame_satellite.cfg` | Added Center Base and Center Player buttons to SatellitePanel UI, and also set them to use style "RIGHTTAB".|
| `sprayeffect.odf`   | The system still uses dusttrail.odf for ground, and spraypuff.odf for water. Created a new odf to calibrate the dust system, `sprayeffect.odf`. |
| `g_fflash.xsi`       | Added missing mesh `g_fflash.xsi` used for muzzle flash effects. |
| `flash.tga`          | Referenced in relation to `g_fflash.xsi` for muzzle flash texture usage. |
| `cursor.tga` | Made new Cursor image `cursorHD.tga`, and made a compatible version of `cursor.tga` for existing addons / non-scaling cursors to use. |
| `BackStarField.tga`  | Fixed missing `BackStarField.tga` call in Single Player and Instant Action debrief screens. |
| `Dark6.tga`          | Fixed incorrect diffuse texture for `Dark6.tga` (was using an old BZ2 texture). |
| `vsmoke2.tga` | Fixed missing Alpha channel on `vsmoke2.tga` used in effects. |
| `vsmoke3.tga` | Made a copy of vsmoke_interface.tga, named `vsmoke3.tga` and pointed stock render Fx to use that. |
| `ring.tga` | Fixed incorrect blend mode on some explosions that used `ring.tga`, that caused black squares around it on the ground. |