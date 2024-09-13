
# Init States
 

The INIT state sets the initial conditions of the system, initializing all relevant enums to their 
starting values. It sets the heating, lighting, and appliance states to OFF, and establishes the 
initial temperature states for small, medium, and large rooms as BELOW their targets. This ensures 
that the simulation begins from a consistent and controlled baseline.

The base state represents the main simulation loop, where global time is incremented at each step 
using the defined time step. This state acts as the core of the simulation, keeping the system 
running and continuously updating the time to reflect ongoing processes. Together, these states 
lay the foundation for the system's dynamic behavior and progression.

```java
    normal state INIT { // Initialise ENUMS
        heatingState = #OFF;
        lightsState1 = #OFF;
        lightsState2 = #OFF;
        applianceState1 = #OFF;
        applianceState2 = #OFF;
        smallRoomState = #BELOW;
        mediumRoomState = #BELOW;
        largeRoomState = #BELOW;
    }

    normal state base {
        globalTime = incrementGlobalTime(timeStep, globalTime); // Increment Time
    }
```