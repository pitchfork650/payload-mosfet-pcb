
Second edition of payload electromagnet release mechanism pcb, energizing one 5V 2A electromagnet using 5V logic signals.
built upon the dual mosfet board

Contents:

kicad files - schematic(sch), pcb(pcb)
N channel irlz34npbf low side mosfet switch circuit, with 3 pin jst data, 2 pin electromagnet, 2 pin power
1mm power traces, 0.5mm data traces
made as small as possible for tht lol
side note: release mechanism as of making of pcb - permanent magnets attached to the top of the payload, electromagnets of opposing polarity attached on the bottom of the release mechanism (permanent magnets will mate with the iron core of the emagnet). emagnet switches on for a split second, cancelling the magnetic field of the permanent magnets, and payload will drop. will be two payloads in total, and one electromagnet for each payload, so therefore two mosfets. gates of mosfets are attached to the data lines, sources of mosfets attached to gnd, and being a low-side mosfet, the drain will be attached to lower potential end of the electromagnet pins.


emagnets are rated for 5V and a MAXIMUM of 2A. payloads will be dropped separately, so only a maximum of 10W will be drawn at the given ~250ms of emagnets turning on.


Post creation notes: 
- N Channel MOSFET: uses electrons, source is typically LOW side (drain connected to load, source connected to GND or LOW)
        - best for loads typically off, need positive V_GS to turn on MOSFET
- P Channel MOSFET: uses holes, source is typically HIGH side (drain is connected to load which is connected to gnd, source connected to higher potential)
        - best for loads typically on, 0 V_GS to turn off MOSFET
- Flywheel diodes: prevents flyback when Vsource is attached/detached
        - attach parallel to load, biased TOWARDS source, as CLOSE to load as possible
- Two types of R_GS resistors (prevents false triggering of MOSFET, place CLOSE TO MOSFET)
    - Pull-down resistor:
        - small enough to optimize power draw, large enough to block current
        - allows the MOSFET gate voltage potential to bleed to ground, making sure MOSFET gate potential is 0V when data is disconnected
        - typically for N channel MOSFETS, for load typically off
          - works for P channel too, if you want a load typically on
    - Pull-up resistor:
        - large enough to minimize current leakage
        - allows MOSFET gate voltage to always equal to source when data is disconnected (keeps V_GS at 0V)
        - literally pulls the voltage of the gate up
        - typically for P channel MOSFETS, for load typically on
          - works for P channel too, for load typically off



11/11/2026 eleven eleven V3 edit:
Moving to SMD to save space and cost and small spec differences. Everything is relocated.

- Mosfet changed to N channel SSM3K339R,LF   -> footprint: Package_TO_SOT_SMD:SOT-23_Handsoldering
  (https://www.digikey.com/en/products/detail/toshiba-semiconductor-and-storage/SSM3K339R-LF/4781036)
    allows for lower Vgs (1.2 vs 2V), lower gate charge (2.4nC vs 25nC). tradeoffs: higher Rds (185mohm @1A vs 35mOhm @16A), lower max Vds (40V vs 55V), lower max current (2A vs 30A)
- Resistors changed to 0603 SMD package, Resistor_SMD:R_0603_1608Metric_Pad0.98x0.95mm_HandSolder
    hand solder size so we dont need a hotplate or heat gun
- Electromagnets have been changed to 24V from 5V, allowing for less current draw.
    power usage still roughly 2.4-5W per magnet, energized for a split second. 
    power trace length changed from 1mm to 0.5mm (current passed changed from 1-2A to 0.1-0.2A, and clearance reasons), now consistent with data trace width
- Connectors changed to Adafruit JST-PH 2-Pin SMT right angle connectors
  (https://www.adafruit.com/product/1769?srsltid=AYCX9vKmg7AnkadIvNh6u-C9kYsipoDEGgflLF5kSu7d5kptqncLCG7TtIA)
    consistent with SMD, slightly smaller package. 
    rated for 100V, 2A



