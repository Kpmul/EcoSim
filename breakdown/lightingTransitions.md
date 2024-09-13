# Lighting Transitions
 
This section defines the state transitions for controlling two separate lights within the system. 
The transitions handle both turning the lights ON and OFF, and managing the state changes based on 
the overall room conditions and heating system status.

The transitions for turning Light 1 ON are triggered when Light 1 is in the OFF state and various 
system conditions are met. The system ensures that Light 1 turns ON in response to different heating 
and cooling states, including base states and specific heating levels. 

Following the activation of Light 1, state memory transitions are defined to manage the movement from 
the ON state to various heating or cooling states based on room conditions and heating system status. 
These transitions ensure that the system accurately reflects the light's influence on the environment 
and maintains the correct state information.

Similarly, transitions for turning Light 1 OFF are defined to revert the light's state to OFF when 
certain conditions are met. This includes various heating and cooling states, ensuring the system 
accurately tracks when the light is turned OFF and adjusts the state memory accordingly.

The transitions for turning Light 2 ON and OFF are handled in the same manner as Light 1, with specific 
transitions designed to manage Light 2's state changes based on room conditions and heating system status. 
This ensures consistent behavior for both lights, maintaining accurate state management across the system.

Overall, these transitions ensure that lighting control is integrated seamlessly with heating and cooling 
processes, providing a cohesive system for managing energy usage and environmental conditions.

```java
    // Turn lights1 ON
    trans ls1 { heating -> lightsOn1 where (lightsState1 == #OFF); }
    trans ls2 { h1 -> lightsOn1      where (lightsState1 == #OFF); }
    trans ls3 { h2 -> lightsOn1      where (lightsState1 == #OFF); }
    trans ls4 { h3 -> lightsOn1      where (lightsState1 == #OFF); }
    trans ls5 { h4 -> lightsOn1      where (lightsState1 == #OFF); }
    trans ls6 { c4 -> lightsOn1      where (lightsState1 == #OFF); }
    trans ls7 { c3 -> lightsOn1      where (lightsState1 == #OFF); }
    trans ls8 { c2 -> lightsOn1      where (lightsState1 == #OFF); }
    trans ls9 { c1 -> lightsOn1      where (lightsState1 == #OFF); }
    trans ls10 { base -> lightsOn1    where (lightsState1 == #OFF); }

    // State memory after turning lights1 on
    trans ls11 { lightsOn1 -> heating where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ls12 { lightsOn1 -> h1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW
    );}
    trans ls13 { lightsOn1 -> h2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ls14 { lightsOn1 -> h3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET &&
        heatingState == #ON
    );}
    trans ls15 { lightsOn1 -> h4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE &&
        heatingState == #ON
    );}
    trans ls16 { lightsOn1 -> base where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ls17 { lightsOn1 -> c1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ls18 { lightsOn1 -> c2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ls19 { lightsOn1 -> c3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET &&
        heatingState == #OFF
    );}
    trans ls20 { lightsOn1 -> c4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE &&
        heatingState == #OFF
    );}

    // Turn lights1 OFF
    trans ls21 { heating -> lightsOff1 where (lightsState1 == #ON); }
    trans ls22 { h1 -> lightsOff1      where (lightsState1 == #ON); }
    trans ls23 { h2 -> lightsOff1      where (lightsState1 == #ON); }
    trans ls24 { h3 -> lightsOff1      where (lightsState1 == #ON); }
    trans ls25 { h4 -> lightsOff1      where (lightsState1 == #ON); }
    trans ls26 { c4 -> lightsOff1      where (lightsState1 == #ON); }
    trans ls27 { c3 -> lightsOff1      where (lightsState1 == #ON); }
    trans ls28 { c2 -> lightsOff1      where (lightsState1 == #ON); }
    trans ls29 { c1 -> lightsOff1      where (lightsState1 == #ON); }
    trans ls30 { base -> lightsOff1    where (lightsState1 == #ON); }

    trans ls31 { lightsOff1 -> heating where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ls32 { lightsOff1 -> h1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ls33 { lightsOff1 -> h2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ls34 { lightsOff1 -> h3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET &&
        heatingState == #ON
    );}
    trans ls35 { lightsOff1 -> h4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE &&
        heatingState == #ON
    );}
    trans ls36 { lightsOff1 -> base where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ls37 { lightsOff1 -> c1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ls38 { lightsOff1 -> c2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ls39 { lightsOff1 -> c3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET &&
        heatingState == #OFF
    );}
    trans ls40 { lightsOff1 -> c4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE &&
        heatingState == #OFF
    );}

    // Turn lights2 ON
    trans ls41 { heating -> lightsOn2 where (lightsState2 == #OFF); }
    trans ls42 { h1 -> lightsOn2      where (lightsState2 == #OFF); }
    trans ls43 { h2 -> lightsOn2      where (lightsState2 == #OFF); }
    trans ls44 { h3 -> lightsOn2      where (lightsState2 == #OFF); }
    trans ls45 { h4 -> lightsOn2      where (lightsState2 == #OFF); }
    trans ls46 { c4 -> lightsOn2      where (lightsState2 == #OFF); }
    trans ls47 { c3 -> lightsOn2      where (lightsState2 == #OFF); }
    trans ls48 { c2 -> lightsOn2      where (lightsState2 == #OFF); }
    trans ls49 { c1 -> lightsOn2      where (lightsState2 == #OFF); }
    trans ls50 { base -> lightsOn2    where (lightsState2 == #OFF); } 
    // State memory after turning lights2 on
    trans ls51 { lightsOn2 -> heating where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ls52 { lightsOn2 -> h1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW
    );}
    trans ls53 { lightsOn2 -> h2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ls54 { lightsOn2 -> h3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET &&
        heatingState == #ON
    );}
    trans ls55 { lightsOn2 -> h4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE &&
        heatingState == #ON
    );}
    trans ls56 { lightsOn2 -> base where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ls57 { lightsOn2 -> c1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ls58 { lightsOn2 -> c2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ls59 { lightsOn2 -> c3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET &&
        heatingState == #OFF
    );}
    trans ls60 { lightsOn2 -> c4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE &&
        heatingState == #OFF
    );}

    // Turn lights2 OFF
    trans ls70 { heating -> lightsOff2 where (lightsState2 == #ON); }
    trans ls71 { h1 -> lightsOff2      where (lightsState2 == #ON); }
    trans ls72 { h2 -> lightsOff2      where (lightsState2 == #ON); }
    trans ls73 { h3 -> lightsOff2      where (lightsState2 == #ON); }
    trans ls74 { h4 -> lightsOff2      where (lightsState2 == #ON); }
    trans ls75 { c4 -> lightsOff2      where (lightsState2 == #ON); }
    trans ls76 { c3 -> lightsOff2      where (lightsState2 == #ON); }
    trans ls77 { c2 -> lightsOff2      where (lightsState2 == #ON); }
    trans ls78 { c1 -> lightsOff2      where (lightsState2 == #ON); }
    trans ls79 { base -> lightsOff2    where (lightsState2 == #ON); }

    trans ls80 { lightsOff2 -> heating where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ls81 { lightsOff2 -> h1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ls82 { lightsOff2 -> h2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ls83 { lightsOff2 -> h3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET &&
        heatingState == #ON
    );}
    trans ls84 { lightsOff2 -> h4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE &&
        heatingState == #ON
    );}
    trans ls85 { lightsOff2 -> base where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ls86 { lightsOff2 -> c1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ls87 { lightsOff2 -> c2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ls88 { lightsOff2 -> c3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET &&
        heatingState == #OFF
    );}
    trans ls89 { lightsOff2 -> c4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE &&
        heatingState == #OFF
    );}
```