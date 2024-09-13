
# Lighting States

This section defines the behavior of lighting within the system, focusing on the ON and OFF states for two separate lights. Each light's state is managed through transitions that update the light's status and track energy usage. 

The transitions for Light 1 manage its ON and OFF states. When Light 1 is turned ON, the system records the time of activation and adjusts the global time. When Light 1 is turned OFF, it updates the time of deactivation, calculates the energy consumed during its ON period, and adjusts the global time accordingly.

Similarly, the transitions for Light 2 handle its ON and OFF states in the same manner. This ensures that energy usage is accurately tracked based on the light's operational status, and global time is managed to reflect the light's activity.

The key functions involved include `updateEnergyUsage`, which updates the total energy consumption based on the light's activity and occupancy rate; `calculateLightEnergy`, which computes the energy usage based on the duration the light was ON; and `decrementGlobalTime`, which adjusts the global time to synchronize with the light's state changes.

```java
    normal state lightsOn1 {
        lightsState1 = #ON;
        lightsTimeOn1 = globalTime - timeStep;
        globalTime = decrementGlobalTime(timeStep, globalTime); // Decrement time so as to cancel out time progression for turning on light/appliance
    }

    normal state lightsOff1 {
        lightsState1 = #OFF;
        lightsTimeOff1 = globalTime;
        // Calculate difference between time on and off, multiply by rate of occupancy and update energy usage
        energyUsed = updateEnergyUsage(energyUsed, calculateLightEnergy(lightsTimeOn1, lightsTimeOff1)) * occupancyMultiplier;
        globalTime = decrementGlobalTime(timeStep, globalTime); 
    }

    normal state lightsOn2 {
        lightsState2 = #ON;
        lightsTimeOn2 = globalTime - timeStep;
        globalTime = decrementGlobalTime(timeStep, globalTime); 
    }

    normal state lightsOff2 {
        lightsState2 = #OFF;
        lightsTimeOff2 = globalTime;
        energyUsed = updateEnergyUsage(energyUsed, calculateLightEnergy(lightsTimeOn2, lightsTimeOff2)) * occupancyMultiplier;
        globalTime = decrementGlobalTime(timeStep, globalTime); 
    }
```