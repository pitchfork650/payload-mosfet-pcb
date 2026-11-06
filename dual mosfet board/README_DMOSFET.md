First edition of payload electromagnet release mechanism pcb, energizing two 5V 2A electromagnets using 5V logic signals. 

Contents: 
* kicad files - schematic(sch), pcb(pcb)
* Dual n channel irlz34npbf low side mosfet switch circuit, with 3 pin jst data, 2 pin electromagnet, 2 pin power
* 1mm power traces, 0.5mm data traces
* made as small as possible for tht lol

side note: release mechanism as of making of pcb - permanent magnets attached to the top of the payload, electromagnets of opposing polarity attached on the bottom of the release mechanism (permanent magnets will mate with the iron core of the emagnet). emagnet switches on for a split second, cancelling the magnetic field of the permanent magnets, and payload will drop. 
will be two payloads in total, and one electromagnet for each payload, so therefore two mosfets. gates of mosfets are attached to the data lines, sources of mosfets attached to gnd, and being a low-side mosfet, the drain will be attached to lower potential end of the electromagnet pins.

emagnets are rated for 5V and a MAXIMUM of 2A. payloads will be dropped separately, so only a maximum of 10W will be drawn at the given ~250ms of emagnets turning on. 
