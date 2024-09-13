# Appliance States


These transitions define the behavior of the cooling process within the system, 
ensuring rooms cool down sequentially based on their current temperatures relative to their target values with a specified tolerance. The states progress from c4 to c1 
as each room approaches its target temperature, and move to a base state once all rooms are below their target temperatures.

Self-transitions (cl5 to cl8) are used to maintain the cooling state of each room 
when temperatures are above or below target thresholds, providing stability in the simulation.

Transitions cl9 to cl13 handle switching from cooling to heating when the heating system is off, allowing interaction between cooling and heating processes in response to changing environmental conditions.

Transitions cl14 to cl18 manage the memory of the room states when shifting from heating to cooling, ensuring the system retains the correct state information even as it transitions between heating and cooling modes, thereby maintaining a consistent environmental control strategy.

```java
    // Cooling Process
    trans cl1 { c4 -> c3   where (currentTempLargeRoom > largeRoomTarget - tempTolerance && currentTempLargeRoom <= largeRoomTarget + tempTolerance); }
    trans cl2 { c3 -> c2   where (currentTempMediumRoom > mediumRoomTarget - tempTolerance && currentTempMediumRoom <= largeRoomTarget + tempTolerance); }
    trans cl3 { c2 -> c1   where (currentTempSmallRoom > smallRoomTarget - tempTolerance && currentTempSmallRoom <= smallRoomTarget + tempTolerance); }
    trans cl4 { c1 -> base where (currentTempSmallRoom < smallRoomTarget &&
                                    currentTempMediumRoom < mediumRoomTarget &&
                                    currentTempLargeRoom < largeRoomTarget ); }
    // Self Transitions
    trans cl5 { c4 -> c4 where (currentTempLargeRoom > largeRoomTarget + tempTolerance); }
    trans cl6 { c3 -> c3 where (currentTempMediumRoom > mediumRoomTarget + tempTolerance); }
    trans cl7 { c2 -> c2 where (currentTempSmallRoom > smallRoomTarget + tempTolerance); }
    trans cl8 { c1 -> c1 where (currentTempSmallRoom < smallRoomTarget - tempTolerance); }

    // Cooling -> System On
    trans cl9 { base -> heatingOn where (heatingState == #OFF ); }
    trans cl10 { c1 -> heatingOn where (heatingState == #OFF ); }
    trans cl11 { c2 -> heatingOn where (heatingState == #OFF ); }
    trans cl12 { c3 -> heatingOn where (heatingState == #OFF ); }
    trans cl13 { c4 -> heatingOn where (heatingState == #OFF ); }

    // System Off -> Cooling
    trans cl14 { heatingOff -> base where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW
    );}
    trans cl15 { heatingOff -> c1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW
    );}
    trans cl16 { heatingOff -> c2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW
    );}
    trans cl17 { heatingOff -> c3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET
    );}
    trans cl18 { heatingOff -> c4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE
    );}
```