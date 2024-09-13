 # Heating States

These states manage the heating process for small, medium, and large rooms, 
adjusting each room's temperature based on its specific heating rate, insulation (R-value), 
and the external temperature. The system progresses through these states depending on 
the temperature conditions of the rooms (TARGET, BELOW, ABOVE).

Each state updates the global time, tracks energy usage, and calculates the current 
temperature for each room, so that the simulation accurately reflects the heating dynamics over time. This modular approach allows the heating behavior to adapt as rooms transition between different temperature conditions, supporting a realistic and responsive model of indoor climate control.

```java
    normal state heatingOn {
        heatingState = #ON; // Set ENUM to ON
    }

    normal state heating {
        smallRoomState = #BELOW;
        mediumRoomState = #BELOW;
        largeRoomState = #BELOW;
        globalTime = incrementGlobalTime(timeStep, globalTime);
        energyUsed = updateEnergyUsage(energyUsed, heatingEnergyUnit);
        // Heat all sized rooms
        currentTempSmallRoom = heatRoom(currentTempSmallRoom, heatingRateSmallRoom, rValue, outsideTemp, timeStep);
        currentTempMediumRoom = heatRoom(currentTempMediumRoom, heatingRateMediumRoom, rValue, outsideTemp, timeStep);
        currentTempLargeRoom = heatRoom(currentTempLargeRoom, heatingRateLargeRoom, rValue, outsideTemp, timeStep);
    }

    normal state h1 {
        smallRoomState = #TARGET;
        mediumRoomState = #BELOW;
        largeRoomState = #BELOW;
        globalTime = incrementGlobalTime(timeStep, globalTime);
        energyUsed = updateEnergyUsage(energyUsed, heatingEnergyUnit);

        currentTempSmallRoom = heatRoom(currentTempSmallRoom, heatingRateSmallRoom, rValue, outsideTemp, timeStep);
        currentTempMediumRoom = heatRoom(currentTempMediumRoom, heatingRateMediumRoom, rValue, outsideTemp, timeStep);
        currentTempLargeRoom = heatRoom(currentTempLargeRoom, heatingRateLargeRoom, rValue, outsideTemp, timeStep);
    }

    normal state h2 {
        smallRoomState = #ABOVE;
        mediumRoomState = #TARGET;
        largeRoomState = #BELOW;
        globalTime = incrementGlobalTime(timeStep, globalTime);
        energyUsed = updateEnergyUsage(energyUsed, heatingEnergyUnit);

        currentTempSmallRoom = heatRoom(currentTempSmallRoom, heatingRateSmallRoom, rValue, outsideTemp, timeStep);
        currentTempMediumRoom = heatRoom(currentTempMediumRoom, heatingRateMediumRoom, rValue, outsideTemp, timeStep);
        currentTempLargeRoom = heatRoom(currentTempLargeRoom, heatingRateLargeRoom, rValue, outsideTemp, timeStep);
    }

    normal state h3 {
        smallRoomState = #ABOVE;
        mediumRoomState = #ABOVE;
        largeRoomState = #TARGET;
        globalTime = incrementGlobalTime(timeStep, globalTime);
        energyUsed = updateEnergyUsage(energyUsed, heatingEnergyUnit);

        currentTempSmallRoom = heatRoom(currentTempSmallRoom, heatingRateSmallRoom, rValue, outsideTemp, timeStep);
        currentTempMediumRoom = heatRoom(currentTempMediumRoom, heatingRateMediumRoom, rValue, outsideTemp, timeStep);
        currentTempLargeRoom = heatRoom(currentTempLargeRoom, heatingRateLargeRoom, rValue, outsideTemp, timeStep);
    }

    normal state h4 {
        smallRoomState = #ABOVE;
        mediumRoomState = #ABOVE;
        largeRoomState = #ABOVE;
        globalTime = incrementGlobalTime(timeStep, globalTime);
        energyUsed = updateEnergyUsage(energyUsed, heatingEnergyUnit);

        currentTempSmallRoom = heatRoom(currentTempSmallRoom, heatingRateSmallRoom, rValue, outsideTemp, timeStep);
        currentTempMediumRoom = heatRoom(currentTempMediumRoom, heatingRateMediumRoom, rValue, outsideTemp, timeStep);
        currentTempLargeRoom = heatRoom(currentTempLargeRoom, heatingRateLargeRoom, rValue, outsideTemp, timeStep);
    }

    normal state heatingOff {
        heatingState = #OFF;    // Sewt ENUM to OFF
    }
```
