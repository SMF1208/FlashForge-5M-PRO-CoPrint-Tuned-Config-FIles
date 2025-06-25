# FlashForge-5M-PRO-CoPrint-Tuned-Config-FIles

Flash Forge Adventurer 5M PRO W/Stock Speed Support/Timelapse Support/Octoeverywhere support

This is a set of config files for the Flash Forge 5M PRO 3D Printer.  These configs are meant to be used in conjuction with the CoPrint KCM kit.

In the config files you will find:
- A custom auto load_filament command created by discord user Mjfsch on the CoPrint discord.  ALL CREDIT TO THEM FOR THE MACRO AND EVERYTHING ABOUT IT
- A MIDI folder containing MIDI melodies that can be played on print action (see macro.cfg)
- A modified [probe] entry in the printer.cfg (keep this at 0 for now)
- An entry for a Z offset in the Start_Print command under cp_macro.cfg (Enter your Z_offset here, you will see I have a few in there for different materials commented out)
- PiD Calibrations (my own)
- All macro changes needed for the new 8in1 head
- An entry to engage the chamber fan in the start_print macro
- A custom end print macro to "present the print"
- Changes to the cancel print and end print macro, instead of cutting the filament and retracting, it calls for a set_filament command instead which basically does just that however it seems to get the positioning better
- Set the max print speeds to 600 mm/s and 20000 mm/s^2 for travel (DO NOT RUN THE PRINTER AT THESE SETTINGS, ITS PURELY FOR THE CONFIG)
- A custom Unload_Spool Macro for changing out an entire spool.  The filament must be in the retracted set_filament position before you run this macro

Before you fully deploy this config:
- You will need to complete your own bed_mesh_calibrate
- You will need to find your own Z Offset
- I suggest also you complete your own PID calibrate.  You wont be able to save_config but can enter those results manually in the config files
- Make all the changes in Orca listed here
- Add this line to your printer settings in orca under Time Lapse Gcode - TIMELAPSE_TAKE_FRAME

If you wish to setup OctoEverywhere, use a raspi and follow their instructions for a companion device.  Once youve got it installed on your Pi you should be able to select your moonraker port when finalizing the config.  It should then just work out of the box.  I am planning on writing a separate guide for that as right now there is no native remote monitoring for this setup.

If you wish to disable the MIDI melodies, review the cp_macro.cfg file.  I have added comments on what lines to remove to disable this.

The MIDI function works by storing all .mid files in /root/printer_data/config/MIDI.  If you have a custom melody you would like to add, import it into the MIDI folder.  

The command to play a MIDI file is:
PLAY_MIDI FILE="/root/printer_data/config/MIDI/YOURMIDIFILENAMEHERE.mid"
^^This line can also be added to any macro to engadge the buzzer at that point.

I am going to continue to update this as I work out the final kinks.  Currently there are few things left, including potentially getting the Forge-X mod to work.
