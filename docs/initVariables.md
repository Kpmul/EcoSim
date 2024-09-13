    
# Program Start / Init Variables
 
```java
option-trace=true;                 
```

If set to true, Cyclone will produce a trace file that contains concrete values of each variable in each state/node of the path discovered. If there is no model, no trace file will be generated. By default, this option is disabled (false). The trace of a specification file is stored in directory named trace that normally is under your current directory.          

```java
machine EcoSim {    
```
Can set model to be either a machine or graph - In general, 
a graph described by Cyclone contains four sections: a set of nodes, 
a set of edges, a set of invariants, and a goal to be achieved. 
A Machine will use similar tools but names will more closely represent 
a Deterministic Finite Automata.
    
```java
    // Room states
    enum{BELOW, TARGET, ABOVE} smallRoomState;
    enum{BELOW, TARGET, ABOVE} mediumRoomState;
    enum{BELOW, TARGET, ABOVE} largeRoomState;
    // System states
    enum{ON, OFF} heatingState;
    enum{ON, OFF} lightsState1;
    enum{ON, OFF} lightsState2;
    enum{ON, OFF} applianceState1;
    enum{ON, OFF} applianceState2;
    // State variables
    real globalTime = 0;
    real lightsTimeOn1 = 0;
    real lightsTimeOff1 = 0;
    real lightsTimeOn2 = 0;
    real lightsTimeOff2 = 0;
    real applianceTimeOn1 = 0;
    real applianceTimeOff1 = 0;
    real applianceTimeOn2 = 0;
    real applianceTimeOff2 = 0;
    real energyUsed = 0;
    // Adjustable User settings
    real timeStep = 30; // Can be set to represent passage of time depending on user's needs
    const real tempTolerance = 0.6; 
    // Entry variables
    real rValue = 0;
    real occupancyMultiplier = 0;
    real buildingSize = 0;
    real heatingEnergyUnit = 0;
    real lightingEnergyUnit = 0;
    real outsideTemp = 0;
    real applianceEnergyUnit = 0;
    // Target temperatures
    const real smallRoomTarget = 20;
    const real mediumRoomTarget = 20.5;
    const real largeRoomTarget = 21;
    // Current temperatures
    real currentTempSmallRoom = 19;
    real currentTempMediumRoom = 18;
    real currentTempLargeRoom = 17;
    // Heating rates - Represent the size of the room and the rate at which it natually heats
    const real heatingRateSmallRoom = 0.66;
    const real heatingRateMediumRoom = 1;
    const real heatingRateLargeRoom = 1.3;
    // Cooling rates - Represent the size of the room and the rate at which it natually cools
    const real coolingRateSmallRoom = 0.66;
    const real coolingRateMediumRoom = 1;
    const real coolingRateLargeRoom = 1.3;
    // These 'init' variables are set to represent a basic setup for the EcoSim model. 
}
```