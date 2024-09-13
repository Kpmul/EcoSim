# Cooling States

These states manage the cooling process for the small, medium, and large rooms, 
adjusting each room's temperature based on its specific cooling rate, insulation (R-value), and the external temperature. The system progresses through these states depending on the temperature conditions of the rooms (TARGET, BELOW, ABOVE).

Each state updates the global time and calculates the current temperature for each room, ensuring the simulation reflects accurate thermal dynamics over time. This modular approach allows the cooling behavior to adapt as rooms transition between different temperature conditions, supporting a realistic and responsive model of indoor climate control.

```java
    normal state c1 {
        smallRoomState = #TARGET;
        mediumRoomState = #BELOW;
        largeRoomState = #BELOW;
        globalTime = incrementGlobalTime(timeStep, globalTime);

        currentTempSmallRoom = coolRoom(currentTempSmallRoom, coolingRateSmallRoom, rValue, outsideTemp, timeStep);
        currentTempMediumRoom = coolRoom(currentTempMediumRoom, coolingRateMediumRoom, rValue, outsideTemp, timeStep);
        currentTempLargeRoom = coolRoom(currentTempLargeRoom, coolingRateLargeRoom, rValue, outsideTemp, timeStep);
    }

    normal state c2 {
        smallRoomState = #ABOVE;
        mediumRoomState = #TARGET;
        largeRoomState = #BELOW;
        globalTime = incrementGlobalTime(timeStep, globalTime);

        currentTempSmallRoom = coolRoom(currentTempSmallRoom, coolingRateSmallRoom, rValue, outsideTemp, timeStep);
        currentTempMediumRoom = coolRoom(currentTempMediumRoom, coolingRateMediumRoom, rValue, outsideTemp, timeStep);
        currentTempLargeRoom = coolRoom(currentTempLargeRoom, coolingRateLargeRoom, rValue, outsideTemp, timeStep);
    }

    normal state c3 {
        smallRoomState = #ABOVE;
        mediumRoomState = #ABOVE;
        largeRoomState = #TARGET;
        globalTime = incrementGlobalTime(timeStep, globalTime);

        currentTempSmallRoom = coolRoom(currentTempSmallRoom, coolingRateSmallRoom, rValue, outsideTemp, timeStep);
        currentTempMediumRoom = coolRoom(currentTempMediumRoom, coolingRateMediumRoom, rValue, outsideTemp, timeStep);
        currentTempLargeRoom = coolRoom(currentTempLargeRoom, coolingRateLargeRoom, rValue, outsideTemp, timeStep);
    }

    normal state c4 {
        smallRoomState = #ABOVE;
        mediumRoomState = #ABOVE;
        largeRoomState = #ABOVE;
        globalTime = incrementGlobalTime(timeStep, globalTime);

        currentTempSmallRoom = coolRoom(currentTempSmallRoom, coolingRateSmallRoom, rValue, outsideTemp, timeStep);
        currentTempMediumRoom = coolRoom(currentTempMediumRoom, coolingRateMediumRoom, rValue, outsideTemp, timeStep);
        currentTempLargeRoom = coolRoom(currentTempLargeRoom, coolingRateLargeRoom, rValue, outsideTemp, timeStep);
    }
```
