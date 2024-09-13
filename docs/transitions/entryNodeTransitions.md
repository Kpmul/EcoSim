# Entry Node Transitions

    
These transitions guide the simulation from the initial entry state through a series of configuration nodes, setting up the various aspects of the building's energy model.

The process begins with the selection of the building size (small, medium, or large), followed by the insulation level (low, medium, or high). Next, it moves through occupancy levels (low, medium, or high), determining the demand based on the number of occupants.

The heating type is then selected (electric, gas, or pump), which directly influences energy consumption patterns. After the heating configuration, lighting options are set (CFL, LED, or LCD), further refining the model based on lighting efficiency and usage.

Outdoor temperature states (hot, mild, cold) are then determined, affecting the heating and cooling demands. Finally, appliance usage levels (low, medium, high) are configured, completing the model's setup for a realistic or optimized energy usage scenario.

The configuration concludes with a transition to the INIT state, from which the actual simulation can begin by moving to the base state. This sequential setup ensures a comprehensive and flexible configuration that reflects various real-world scenarios or optimises for specific energy-saving goals.
```java
    // Transitions from entry through configuration nodes
    trans z0 { entry -> smallBuilding }
    trans z1 { entry -> mediumBuilding }
    trans z2 { entry -> largeBuilding }

    trans x0 { smallBuilding -> lowInsulation }
    trans x1 { mediumBuilding -> lowInsulation }
    trans x2 { largeBuilding -> lowInsulation }
    trans x3 { smallBuilding -> medInsulation }
    trans x4 { mediumBuilding -> medInsulation }
    trans x5 { largeBuilding -> medInsulation }
    trans x6 { smallBuilding -> hiInsulation }
    trans x7 { mediumBuilding -> hiInsulation }
    trans x8 { largeBuilding -> hiInsulation }

    trans y0 { lowInsulation -> lowOccupancy }
    trans y1 { lowInsulation -> medOccupancy }
    trans y2 { lowInsulation -> hiOccupancy }
    trans y3 { medInsulation -> lowOccupancy }
    trans y4 { medInsulation -> medOccupancy }
    trans y5 { medInsulation -> hiOccupancy }
    trans y6 { hiInsulation -> lowOccupancy }
    trans y7 { hiInsulation -> medOccupancy }
    trans y8 { hiInsulation -> hiOccupancy }

    trans w0 { lowOccupancy -> electricHeating }
    trans w1 { lowOccupancy -> gasHeating }
    trans w2 { lowOccupancy -> pumpHeating }
    trans w3 { medOccupancy -> electricHeating }
    trans w4 { medOccupancy -> gasHeating }
    trans w5 { medOccupancy -> pumpHeating }
    trans w6 { hiOccupancy -> electricHeating }
    trans w7 { hiOccupancy -> gasHeating }
    trans w8 { hiOccupancy -> pumpHeating }

    trans v0 { electricHeating -> CFL }
    trans v1 { electricHeating -> LED }
    trans v2 { electricHeating -> LCD }
    trans v3 { gasHeating -> CFL }
    trans v4 { gasHeating -> LED }
    trans v5 { gasHeating -> LCD }
    trans v6 { pumpHeating -> CFL }
    trans v7 { pumpHeating -> LED }
    trans v8 { pumpHeating -> LCD }

    trans u0 { CFL -> hot }
    trans u1 { CFL -> mild }
    trans u2 { CFL -> cold }
    trans u3 { LED -> hot }
    trans u4 { LED -> mild }
    trans u5 { LED -> cold }
    trans u6 { LCD -> hot }
    trans u7 { LCD -> mild }
    trans u8 { LCD -> cold }

    trans q0 { hot -> lowUsage}
    trans q1 { hot -> medUsage}
    trans q2 { hot -> hiUsage}
    trans q3 { mild -> lowUsage}
    trans q4 { mild -> medUsage}
    trans q5 { mild -> hiUsage}
    trans q6 { cold -> lowUsage}
    trans q7 { cold -> medUsage}
    trans q8 { cold -> hiUsage}
    // End of configuration -> INIT
    trans z3 { lowUsage -> INIT }
    trans z4 { medUsage -> INIT }
    trans z5 { hiUsage -> INIT }
    // Enums get assigned INIT -> base - simulation begins
    trans t0 { INIT -> base }
    trans t1 { base -> base where (heatingState == #OFF); }
```
