# FlashForge-5M-PRO-CoPrint-Tuned-Config-FIles

Flash Forge Adventurer 5M PRO W/Stock Speed Support/Timelapse Support/Octoeverywhere support

This is a set of config files for the Flash Forge 5M PRO 3D Printer.  These configs are meant to be used in conjuction with the CoPrint KCM kit.

In the config files you will find:
- A custom auto load_filament command created by discord user Mjfsch on the CoPrint discord.
- A MIDI folder containing MIDI melodies that can be played on print action (see cp_macro.cfg)
- A modified [probe] entry in the printer.cfg (do not modify)
- An entry for a Z offset in the Start_Print command under cp_macro.cfg (Enter your Z_offset here, you will see I have a few in there for different materials commented out)
- PiD Calibrations (my own)
- All macro changes needed for the new 8in1 head
- An entry to engage the chamber fan in the start_print macro
- A custom end print macro to "present the print"
- Changes to the cancel print and end print macro, allowing better clearance on retraction
- Set the max print speeds to 600 mm/s and 20000 mm/s^2 for travel (I would not suggest printing at these speeds)
- A custom Unload_Spool Macro for changing out an entire spool

Before you fully deploy this config:
- You will need to create your own bed mesh
- You will need to find your own Z Offset and enter it in the start print macro
- I suggest also you complete your own PID calibrate.  Enter those results manually in the config files
- Add this line to your printer settings in orca under Time Lapse Gcode - TIMELAPSE_TAKE_FRAME

If you wish to setup OctoEverywhere, use a raspi and follow their instructions for a companion device.  Once youve got it installed on your Pi you should be able to select your moonraker port when finalizing the config.  It should then just work out of the box.

If you wish to disable the MIDI melodies, review the cp_macro.cfg file.  I have added comments on what lines to remove to disable this.

The MIDI function works by storing all .mid files in /root/printer_data/config/MIDI.  If you have a custom melody you would like to add, import it into the MIDI folder.  

The command to play a MIDI file is:
PLAY_MIDI FILE="/root/printer_data/config/MIDI/YOURMIDIFILENAMEHERE.mid"
^^This line can also be added to any macro to engadge the buzzer at that point.

THE FORGE X MOD DOES NOT WORK WITH THE KCM KIT - There are issues with the firmware on the coprint equipment
