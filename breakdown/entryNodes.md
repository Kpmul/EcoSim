# Entry Nodes

These entry nodes define the initial configuration settings for the simulation, establishing the baseline parameters for building size, insulation quality, occupancy levels, heating types, lighting options, outdoor temperatures, and appliance usage rates. 

Each category has multiple states representing different conditions or choices (e.g., small, medium, and large building sizes; low, medium, and high insulation). 
These states are crucial for setting up the simulation environment, allowing for a 
flexible and customizable system that can adapt to a wide range of scenarios. 

The functionality of Cyclone allows the system to either simulate realistic conditions of an existing real-life house or building or else perform optimization analyses, to enhance the utility in energy efficiency modeling and decision-making.
```java
    normal start state entry {}
    // Building Size
    normal state smallBuilding {
        buildingSize = 1.0;
    }
    normal state mediumBuilding {
        buildingSize = 2.0;
    }
    normal state largeBuilding {
        buildingSize = 3.0;
    }
    // Insulation
    normal state lowInsulation {
        rValue = 0.7;
    }
    normal state medInsulation {
        rValue = 1.0;
    }
    normal state hiInsulation {
        rValue = 1.3;
    }
    // Occupancy 
    normal state lowOccupancy {
        occupancyMultiplier = 1 * buildingSize;
    }
    normal state medOccupancy {
        occupancyMultiplier = 2 * buildingSize;
    }
    normal state hiOccupancy {
        occupancyMultiplier = 3 * buildingSize;
    }
    // Heating
    normal state electricHeating {
        heatingEnergyUnit = 1.5 / (60 / timeStep);
    }
    normal state gasHeating {
        heatingEnergyUnit = 1.2 / (60 / timeStep);
    }
    normal state pumpHeating {
        heatingEnergyUnit = 0.4286 / (60 / timeStep);
    }
    // Lighting
    normal state CFL {
        lightingEnergyUnit = (0.015 * 4) / (60 / timeStep);
    }
    normal state LED {
        lightingEnergyUnit = (0.01 * 4) / (60 / timeStep);
    }
    normal state LCD {
        lightingEnergyUnit = (0.02 * 4) / (60 / timeStep);
    }
    // Outdoor Temp
    normal state hot {
        outsideTemp = 30;
    }
    normal state mild {
        outsideTemp = 15;
    }
    normal state cold {
        outsideTemp = 5;
    }
    // Appliances
    normal state lowUsage {
        applianceEnergyUnit = 0.5 / (60 / timeStep);
    }
    normal state medUsage {
        applianceEnergyUnit = 1.0 / (60 / timeStep);
    }
    normal state hiUsage {
        applianceEnergyUnit = 1.5 / (60 / timeStep);
    }
```