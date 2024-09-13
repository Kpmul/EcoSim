 # Goal Section


This section defines the goal of the simulation, setting up, as an example, a specific path through the configuration nodes to represent a residential home scenario with medium insulation, low occupancy, pump heating, LED lighting, mild outdoor conditions, and medium appliance usage.
   
The 'residentialHome' path outlines this specific setup from entry to INIT, providing a target configuration that the model aims to achieve.

The assert statement checks whether both the first lighting and the second appliance states are OFF, and that the total energy used is below 2.00 units, enforcing constraints on the simulation to ensure energy efficiency under these specific conditions.

The 'check' command is used to verify if a path exists from 'residentialHome' with certain conditions applied: ensuring that the heating is toggled ON and OFF within a set range, while lights and appliances are also toggled ON briefly. The goal is to reach a state (h3) within 20 steps, without triggering (h4), confirming the system's ability to maintain the desired state transitions efficiently.

Uncommenting the 'enumerate' command would allow the system to explore all possible paths that meet the conditions to reach (h3), which could be useful for finding optimized paths but may be memory intensive due to the exhaustive nature of the search.

```java
    goal {

        let residentialHome = entry -> smallBuilding -> medInsulation -> lowOccupancy -> pumpHeating -> LED -> mild -> medUsage -> INIT;

        assert (lightsState1 == #OFF && applianceState2 == #OFF) && (energyUsed < 2.00);

        // Check if path exists
        check for 20 condition (residentialHome && !h4 && heatingOn^{0:2} && heatingOff^{0:2} && lightsOn1^{0:1} && applianceOn1^{0:1}) reach (h3) 

        // Example of enumerating over paths to find optimisation (memory instenive):
        // enumerate for 20 condition (residentialHome && !h4 && heatingOn^{0:2} && heatingOff^{0:2} && lightsOn1^{0:1} && applianceOn1^{0:1}) reach (h3)
    }
```
