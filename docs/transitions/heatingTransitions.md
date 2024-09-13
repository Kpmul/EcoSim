 # Heating Transitions

These transitions manage the progression through the heating states for small, medium, and large rooms. The transitions ensure that the system moves through the appropriate states based on the temperature conditions of each room, adjusting as needed when temperatures reach their target ranges (BELOW, TARGET, ABOVE).

The heating process transitions through specific states (heating, h1, h2, h3, h4), reflecting each room's temperature adjustments as they approach their respective targets. Self-transitions handle scenarios where rooms are not yet within their target ranges, maintaining the current state until conditions change.

Additional transitions handle turning the heating system off or initiating it based on the overall state of the heating system and room temperatures, allowing the model to realistically simulate the system's dynamic responses in managing indoor temperatures.

```java    
    // Heating states progression
    trans ht2 { heating -> h1 where (currentTempSmallRoom >= smallRoomTarget - tempTolerance && currentTempSmallRoom <= smallRoomTarget + tempTolerance); }
    trans ht3 { h1 -> h2 where (currentTempMediumRoom >= mediumRoomTarget - tempTolerance && currentTempMediumRoom <= mediumRoomTarget + tempTolerance); } 
    trans ht4 { h2 -> h3 where (currentTempLargeRoom >= largeRoomTarget - tempTolerance && currentTempLargeRoom <= largeRoomTarget + tempTolerance); } 
    trans ht5 { h3 -> h4 where (currentTempLargeRoom > largeRoomTarget + tempTolerance); } 
    // Self Transitions
    trans ht1 { heating -> heating where (currentTempSmallRoom < smallRoomTarget - tempTolerance); }
    trans ht6 { h1 -> h1 where (currentTempMediumRoom < mediumRoomTarget - tempTolerance); }                  
    trans ht7 { h2 -> h2 where (currentTempLargeRoom < largeRoomTarget - tempTolerance); }                  
    trans ht8 { h3 -> h3 where (currentTempLargeRoom < largeRoomTarget + tempTolerance); }    
    trans ht9 { h4 -> h4 where (currentTempSmallRoom > smallRoomTarget + tempTolerance && 
                               currentTempMediumRoom > mediumRoomTarget + tempTolerance&& 
                               currentTempLargeRoom > largeRoomTarget + tempTolerance); }  
    

    // Heating -> System Off
    trans ht10  { heating -> heatingOff where (heatingState == #ON); } 
    trans ht11  { h1 -> heatingOff where (heatingState == #ON); }
    trans ht12  { h2 -> heatingOff where (heatingState == #ON); }
    trans ht13 { h3 -> heatingOff where (heatingState == #ON); }
    trans ht14 { h4 -> heatingOff where (heatingState == #ON); }

    // System On -> Heating
    trans ht15 { heatingOn -> heating where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW
    );}
    trans ht16 { heatingOn -> h1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW
    );}
    trans ht17 { heatingOn -> h2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW
    );}
    trans ht18 { heatingOn -> h3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET
    );}
    trans ht19 { heatingOn -> h4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE
    );}
```
