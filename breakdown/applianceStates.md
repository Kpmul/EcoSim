# Appliance States


These states define the ON/OFF behavior for different appliances within the EcoSim model. Each appliance has corresponding states to track its activity duration and calculate energy usage.

The states utilise functions to adjust the global time, track the time appliances are either ON or OFF, and update the total energy consumption accordingly. 
The occupancyMultiplier factor is applied to reflect variations in energy usage based on occupancy levels.

Adding More Appliances:
Additional appliances with different settings can easily be incorporated by creating new states similar to those shown below. Simply define the ON and OFF states with corresponding variables and adjustments for the new appliance. This modular approach allows for the flexible expansion of the EcoSim model to accommodate various appliance types and energy scenarios.

```java
normal state applianceOn1 {
        applianceState1 = #ON;
        applianceTimeOn1 = globalTime - timeStep;
        globalTime = decrementGlobalTime(timeStep, globalTime); 
    }

    normal state applianceOff1 {
        applianceState1 = #OFF;
        applianceTimeOff1 = globalTime;
        energyUsed = updateEnergyUsage(energyUsed, calculateLightEnergy(applianceTimeOn1, applianceTimeOff1)) * occupancyMultiplier;
        globalTime = decrementGlobalTime(timeStep, globalTime); 
    }
    normal state applianceOn2 {
        applianceState2 = #ON;
        applianceTimeOn2 = globalTime - timeStep;
        globalTime = decrementGlobalTime(timeStep, globalTime); 
    }

    normal state applianceOff2 {
        applianceState2 = #OFF;
        applianceTimeOff2 = globalTime;
        energyUsed = updateEnergyUsage(energyUsed, calculateLightEnergy(applianceTimeOff2, applianceTimeOff2)) * occupancyMultiplier;
        globalTime = decrementGlobalTime(timeStep, globalTime); 
    }
```