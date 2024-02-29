# The CNC Router

## [X-Carve](https://shop.inventables.com/products/x-carve-1)

The X-Carve CNC router works on an XY plane with limited Z-depth, with a work envelope of 750mm x 750mm x 100mm. It is best suited for cutting wood, particleboard, and (with special dust collection), hard plastics.

## ⚠️ Safety

1. The machine moves quickly and expects to encounter resistance - your body will not stop it. Always keep the router's door closed when a job is running.
2. Check for potential crashes before every machine movement.
3. Secure your workpiece; if it isn't secure, it could go flying.
4. Secure the tool in the collet.
5. **Never** leave the machine unattended while it's running code. Do not leave the room without pausing the job.
6. Running a CNC machine is a complex process. This document is not sufficient training for safe machine operation. If you haven’t done this before, have somebody walk you through your first run.

## Setup

1. Plug in the main powerstrip (this will start up the raspberry pi). Use one of the big 20A drops so you don't trip something in the middle of a job.
2. Turn on the controller with the toggle switch on top.
3. Go to [](http://cnc.local) or [](http://cnc.local/tablet) to load the cncjs interface.
4. Connect to the controller via the 'Connection' widget on the left side of the screen.
   - the controller is a Grbl type. If it's not showing up, try refreshing the ports. It should connect automatically.
5. Home the machine. This resets the machine coordinate system to the limit switches. Without this step, the soft limits defined in software can't protect against moving outside of the machine envelope (crashing the machine into itself)

## Pre-Cut Checklist

- [ ] Enclosure is clear of miscellaneous tools or materials.
- [ ] Workholding is secure.
- [ ] Tool is correct, and collet is tight.
- [ ] Work zero is set properly for X, Y, and Z. 
- [ ] No potential crashes within job bounds. (take a bounding pass to check)
- [ ] Dust collection scheme is appropriate for the material.
- [ ] Dust shoe clears all work and workholding, and clears the spindle at maximum cutting depth.
- [ ] Dust collector is on and the correct gates are closed.
- [ ] Enclosure is closed.

## During the job

- Stand and watch your job run, ready to slam the E-Stop, extinguish fires, or slaughter zombies as required. If any of the following occur, jam that stop button:
  - Spindle approaches the work but does not start spinning - G-code might be wrong, or the spindle doesn't have power.
  - Spindle leaves the work boundary unexpectedly, especially if it's heading for a clamp.
  - Tool breaks.
  - Workpiece moves.
- Use the pause button in CNCjs to pause the job in non-emergency situations. This allows you to move the dust hose if it's likely to foul, brush off the machine ways if there are chips on them, or to run to the bathroom. the Spindle will continue running, so it's best to pause outside of the work, or withdraw the spindle. 

## Putting Away the Machine

1. Remove all material and workholding from the bed.
2. Home the machine
4. Shut off the controller (toggle switch above E-Stop)
5. Remove the tool and put away
6. Shut down the controller:
   - ssh into the pi from a bash terminal: `ssh cnc@cnc.local`
   - Shut down: `sudo shutdown`
   - Wait for the pi to shut down
7. Unplug power to the machine.

## CAM Information

- The CNC coordinate system is in milimeters.
- The maximum cutting rate of the machine is 2500mm/min.

## Workholding

Workholding is a an extremely complicated topic and is core to achieving accurate parts as well as avoiding damage to parts, the machine, and the operator. The strategies provided below can only scratch the surface of how to succesfully, efficiently, and safely secure work to the machine bed.

### Nesting

In this process, a large panel is secured to the bed, and parts are cut out of the panel. Without a vacuum table, it is difficult to ensure that the part is flat, so this strategy is best suited for 2D work. Set plenty of Z-clearance, and set your Work Z relative to the bed, rather than the top of the work. 

Because this X-Carve has a riser kit, the spindle is generally unable to reach the machine bed, so spoilboards must be used to lift the work to position. These should be well secured down (using #10-24 screws to the threaded holes below, and sufficiently counterbored so that the tool doesn't ever meet those hardened screws) to provide a reliably flat surface.

### Part by Part

This process involves cutting work to gross size before the CNC operation. This strategy is better suited for 3 axis work where pocketting, surface carving, or similar Z-located features are present. Depending on whether access to part edges is required, workholding can take several forms, including combinations of the below:

- Adhere the part to the bed; this provides complete access to all edges. Use a single layer of blue tape to completely cover the matching surfaces of your part and the machine bed, then apply super glue to the tape. Use a super glue activator to help it bind, and stick the part down to the bed. Let it dry for 5-10 minutes before machining.
- Use strap clamps to hold down the edges of the part. This blocks access to the edges, and also creates potential for crashes, but is a quick way to hold work. It's especially well suited to holding a small spoilboard which your part will be secured on top of. For repeated parts and two-sided jobs, you can cut features into the spoilboard to reference your part.
- Attach the part to a spoilboard with brass screws. (Do not screw directly into the printed X-Carve bed). Don't use steel screws as these are more likely to damage tooling in the event of a crash. Use at least two screws to prevent spin.

### Parts Desire Freedom

If any part becomes separated from its surroundings during milling, it will move - usually enough to scrap the part, often enough to fly across the room (hope you closed the machine enclosure!). Keep separate parts immobile with one of the approaches below:

- Separate workholding (use one of the approaches listed above)
- Tabs - leave bits of material behind, and cut them off later on the router table with a bearing-end template bit or trim cutter. Most CAM software has tools for this.
- Extra thickness - use stock that is ~1/16" thicker than your part, and cut the outline only to the part depth instead of through the stock. Then use the planer to cut to thickness, freeing your part. Make sure the part and any scraps are large enough survive the planer.
- Swarf packing - Using a single flute compression end-mill, the full depth outline can be cut in a single pass, and the compacted swarf left in the cut will prevent movement of any free parts. This is a highly efficient strategy for nesting jobs, and should always be tested to ensure that the combination of material, geometry, and workholding is sufficient for proper swarf compaction.

## Setting Work Zero

### X and Y Axes

X and Y are usually set to zero at some position near the front left corner of the stock. CAM can also be configured to use the center of the part. 

#### Approximate method (when none of the stock edges are relevant to the part)

1. Jog the machine to the X and Y location of the desired zero - It is often helpful to choose a large jog distance which will overshoot, and stop the action on the target. 
### Z-Axis

1. Install the desired tool in the spindle collet and tighten fully.
2. Place the touch plate probe on the work or the bed, directly under the spindle. Plug the probe into the probe cable, and connect the ground clamp to the spindle collet.
3. Using the Probe widget in CNCjs, set the touch plate thickness (15mm), check for clashes, and run the probe program.
4. The machine will lower the spindle along Z slowly, stopping when continuity is detected between the spindle and the touch plate, then backing off 4mm (default). Z -zero will be set at the bottom of the touch plate, assuming you've entered the proper thickness.

---