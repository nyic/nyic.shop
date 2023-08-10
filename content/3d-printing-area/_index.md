# 3D Printing Area

There is a white desk with two 3D printers: a Form 2 (SLA) and a Prusa MKS+ (FDM). It also contains 3D printing supplies, tools, and a few related pieces of equipment.

---

## FDM Printer - Prusa MK3S+

The Prusa MK3S+ is our FDM (fused deposition modeling) printer. It can print PLA, ABS, PETG, and a host of other plastics. It has a heated bed, a Raspberry Pi that runs OctoPrint, and is generally very reliable.

### ⚠️ Safety:

- Please be very cautious during any interaction with the ​printer​. This printer is an electrical device with moving parts and hot-temperature areas.
- Do not let the preheated printer idle. When a printer is preheated and non-printing, material in an extruder degrades over time - it may cause the nozzle to jam up.
  Usage Information:
- Put a thin layer of the Dimafix printing adhesive pen on the bed before beginning to print. This will ensure your piece stays onto the bed during printing.
- The bed auto levels before each print. Please do not attempt to level the bed unless you absolutely need to.
- The bed has a removal metal plate for taking your prints on and off. To remove a print, remove the bed cover first so you don’t damage the print bed.
- The plastic loaded on and under the printer is available for use. Should you bring your own filament, make sure to take it off after use or someone else might use it.
- It’s okay to leave prints going overnight but please remove them as soon as possible. Someone else may remove your print if you leave it on. When in doubt, communicate it out.

### Printing Instructions:

- Use the Prusa Slicer to set up your print. Download it onto your Mac or PC if you have not done so already. This will convert your .stl file into .gcode.
  - If this is your first time using Prusa Slicer with this printer, select the Printer Settings tab at the top of the screen. Click on the drop down and select Add/Remove Printers. Scroll down to the MK3 Family and select the 0.4 mm nozzle for Original Prusa i3 MK3S & MK3S+ MMU2S. Click next on the bottom right until you’ve reached the Filaments Profiles Selection, select the filament(s) that are loaded into the printer. Select Finish. Go to the Plater tab, and select the print settings, filament, and printer you are using.
  - If you have used the Prusa slicer with this printer before, go to the Plater tab, and select the print settings, filament, and printer you are using.
  - Select a brim or supports as needed before converting into .gcode.. (A brim is recommended in general for the piece to stay adhered to the bed and supports are recommended for any hangover angles or openings in the piece)
- Open the OctoPrint UI which is available at [http://prusa.local] when on the shop wifi network. You’ll need the OctoPrint API key to print remotely via Prusa Slicer. The API key is in the settings of the OctoPrint UI after logging in. Use the credential below to login in order to upload a file and print. The login is in the top right part of the screen.
  - Username: pi
  - Password: fortunefavors
- After logging in and uploading your file, be sure to select the drop down bar next to Target in the Temperature tab. Here you can select PLA or ABS temperature settings. Wait for the actual temperatures to match the target temperatures before selecting print.
  - If you are printing with a filament other than PLA or ABS, select the wrench tab on the top right, open the Temperatures tab under PRINTER and add the proper presents for the filament you are using. This will be specified on the roll itself or can be researched online.
- Watch the first few printed layers to be sure ​filament​ has attached to the bed properly​ (5 to 10 minutes).

---

## 3D Resin Printer (MelodicMunia) - Formlabs Form 3 / Formlabs Wash Station / Formlabs Cure Station

The Formlabs Forms 3 is a high resolution SLA 3D printer. There are a variety of engineering-grade printing materials in numerous colors and special properties (such as flexibility or high heat deflection). The build area of the machine is 145 x 145 x 185 mm. The resin options available at the NYIC Shop are:

- Clear Resin V4
- Rigid Resin V1
- Black Resin V4
- White Resin V4
- Draft Resin V2
- Gray Resin
- Flexible 80A
- High Temp Resin V2
- Tough 1500 V1 (Replacement will be shipped in soon 05/09/2023)

After printing, the piece can be washed in the agitated bath of isopropyl alcohol (IPA, concentration of 90% or higher) in the Formlabs Wash Station to clean off residual resin. The Formlabs Cure Station is a UV-curing oven used to “post-process” certain materials that may benefit from or require further curing. Here is a quick video with an overview of the designing and printing process. The default mode of the wash/cure stations is on sleep mode to close the tops. The Forms 3 can be closed by hand with the black cover placed back on.

### ⚠️ Safety:

- Do not leave resin tanks or trays in it when not being used (The failure mode for old trays is that they start leaking which will damage the printer).
- Be careful and DO NOT touch the film on the bottom (metallic) surface of the tray.

### Printing Instructions:

1. Launch Preform. Download it onto your Mac or PC if you have not done so already. Under Material, choose the correct resin type with default settings and select Fastest Print or 100 or Highest Resolution if it applies to your print.
2. Click on the object and move it closer to the center to get the best results. If your object has overhangs, holes, channels/tunnels, lips, or other problematic parts you will need to add in supports. You can just select the One Step Print icon under Files, which will automatically add in supports.
3. The resin tank and resin cartridge need to be placed into the printer. Choose the cartridge of the resin you are using and the coordinating tank. If there is not a coordinating tank, open an unused tank from below the white table. Label the box with the resin it will be used with and store on the shelf above after printing.
4. Once you have selected the printer on Preform make sure it is ready to print. All three icons should be colored blue. If the platform icon is red, go to the clean build platform bin and retrieve a clean platform. Raise the orange printer door, unlock the handle by pulling it up, slide the platform and lock it in place, the icon should then turn green. If the cartridge icon is red, make sure the cartridge is not empty and check to make sure the cap of the cartridge is loose or pressed all the way down to allow for resin to pour onto the tank. After that is done, it should turn blue. And lastly, make sure the tank is secured in place, which would turn the tank icon blue. It should click into place.
5. Then press print!

### Post-printing Instructions:

1. Once the print is ready raise the Formlabs printer door up, unlock the platform handle, and remove the build platform.
2. Place the cartridge back in its designated box with the cap closed. Make sure the excess resin at the bottom is wiped down before being stored. Place the resin tank back in its storage container (with the orange lid) and back into the cardboard box for storage.
3. Once the platform with the print is unlocked and removed, turn it right side up to prevent any liquid resin spillage. Bring it to the Form Wash Station. Wash for at least 10 minutes in isopropyl alcohol (IPA, concentration of 90% or higher)
4. To prepare for curing, slide the build platform onto the handle for stability to remove the resin print.
5. Remove the model away from your body gently with a metal scraper for the best results. To prevent damaging the print, begin by lifting the print little by little all around the platform.
6. Determine the proper cure time and temperature settings using this sheet. Cure the piece with supports still in place.
7. After curing, follow by removing supports with pliers (if needed) and sand (if needed).

### Cleaning Instructions:

After printing on the build platform, wipe it clean with alcohol with a microfiber towel.

---

## Ultrasonic Cleaner

The Ultrasonic cleaner was installed on 2022-12-14. It can be used to clean all sorts of parts by filling the tank with a cleaning fluid and submerging parts in the tank.

### ⚠️ Safety:

- Never use flammable liquids, such as solvents, in the tank. Cleaning fluids include water (preferably distilled), mixtures of water and dish soap, and mixtures of water and industrial cleaners such as Simple Green.
- Always wear rubber/nitrile gloves while using cleaning fluids.
  Usage Information:
- Do not use the heating element on the ultrasonic cleaner; it was used while the tank was empty and was damaged. Instead, heat water in the tea kettle in the kitchen and pour that water into the ultrasonic cleaner prior to cleaning.
- The basket can be used for small parts, but note that it will reduce the cleaning effectiveness.
  Cleaning Information:
- After using:
  - Parts should generally be washed after ultrasonic cleaning.
  - Always unplug the device when you’re done using it. Dispose of any cleaning fluid appropriately, and wash + wipe the tank clean.

---

## Finishing - XTC-3D High Performance Print Coating

XTC-3D is a protective coating for smoothing and finishing 3D printed parts. It can be found in the finishing shelf of the red flammables closet. It can be applied onto the following filaments:

- SLA
- SLS
- PLA
- ABS
- Laywood filament
- Powder printed parts

It can also be used to coat EPS, EPDM, and urethane foam as well as wood, plaster, fabric, cardboard, and paper.

### Usage Information:

Work time is about 10 minutes and drying time is about 4 hours depending filament and surface area.
