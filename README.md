# whapmagoostui-kuujjuarapik-archetypes
This folder contains the set of six residential building archetypes referred to in the article "An archetype-based energy modeling approach for a remote, subarctic community". Each of the six subfolders contains all of the files required for simulation and is made up of the following:
- The multizone building model (.b18)
- The TRNSYS project file (.tpf)
- A weather file for the CWEC20 typical meteorological year (.epw)
- Text files which are read as an input by the TRNSYS project file

The TRNSYS project file was developed in TRNSYS version 18.02. It contains the following components:
- Building characteristics (Equation Block): the set of unique characteristics for the archetype
- EquipCons (Equation Block): calculates the daily power consumption of each appliance, hot water consumption, and the latent and sensible gains of sinks, baths and showers from Building America Protocols
- Lighting (Type 9): reads an input file with the hourly lighting energy use fractions for a year (lighting.txt)
- Hrly Usage Multiplier (Type 9): reads an input file with the hourly fractions for equipment energy use, occupancy and hot water draws, as well as the heating setpoint (equip_schedule.txt)
- EquipSched (Equation Block): calculates the hourly values for power consumption of appliances and lighting, occupancy, hot water draws and the associated latent and sensible gains
- Weather (Type 15): reads the input weather file (CAN_QC_KUUJJUARAPIK-A_7103537_CWEC2020.epw)
- Type2260: takes the wind speed at the weather station height given in the weather file and extrapolates it to the height of the building for use in the Sherman-Grimsrud infiltration model
- Type75b: calculates the infiltration air changes per hour for the building using the Sherman-Grimsrud method
- Type760: calculates the properties of supply and exhaust air in the heat recovery ventilator
- Slab Temp (Type 9) - only in WBG-Duplex, WBG-SF and WSG-SF: reads an input file of soil node temperatures adjacent to the foundation of the building (these temperatures were calculated in a preprocessing simulation using the Type1244 ground coupling component and typical soil temperatures from Whapmagoostui-Kuujjuarapik over a 20-year period)
- Building (Type 56): a multizone building model containing the building geometry, envelope characteristics, and zone internal gains
- PostProc (Equation Block): calculates default simulation outputs
- Summary (Printegrator): prints the monthly summaries of heating, hot water and electricity loads
