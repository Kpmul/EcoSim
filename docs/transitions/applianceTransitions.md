
# Appliance Transitions

    This section defines the transitions for controlling appliances within the EcoSim model.These transitions ensure that appliances can be turned ON or OFF at any time during a simulation, demonstrating the flexibility and real-time responsiveness of the system to varying environmental factors and energy requirements.

    All appliance states are designed to be reachable from any active node within the system. This approach guarantees that appliances can be controlled (turned ON or OFF) from all relevant operational states, whether the system is in a heating or cooling phase, or when transitioning between different room states. 
    By ensuring full reachability, these transitions provide seamless integration with the broader simulation, allowing the system to make real-time adjustments to appliance states without being constrained by specific pathways or node limitations. This design choice enhances the model's capacity to simulate realistic, adaptive control over energy usage, catering to real-world scenarios where appliance activity must adapt instantly to changing conditions.

    Transitions are defined to turn appliances ON when specific states are active 
    After turning an appliance ON, additional transitions are used to maintain state memory, ensuring that the system accurately tracks which appliances are active.Similar transitions exist to turn appliances OFF, allowing for dynamic control of energy usage in response to changing room states or system conditions.

```java
    // Turn appliance1 ON
    trans ap1 { heating -> applianceOn1 where (applianceState1 == #OFF); }
    trans ap2 { h1 -> applianceOn1      where (applianceState1 == #OFF); }
    trans ap3 { h2 -> applianceOn1      where (applianceState1 == #OFF); }
    trans ap4 { h3 -> applianceOn1      where (applianceState1 == #OFF); }
    trans ap5 { h4 -> applianceOn1      where (applianceState1 == #OFF); }
    trans ap6 { c4 -> applianceOn1      where (applianceState1 == #OFF); }
    trans ap7 { c3 -> applianceOn1      where (applianceState1 == #OFF); }
    trans ap8 { c2 -> applianceOn1      where (applianceState1 == #OFF); }
    trans ap9 { c1 -> applianceOn1      where (applianceState1 == #OFF); }
    trans ap10 { base -> applianceOn1    where (applianceState1 == #OFF); }

    // State memory after turning appliance1 on
    trans ap11 { applianceOn1 -> heating where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ap12 { applianceOn1 -> h1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW
    );}
    trans ap13 { applianceOn1 -> h2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ap14 { applianceOn1 -> h3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET &&
        heatingState == #ON
    );}
    trans ap15 { applianceOn1 -> h4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE &&
        heatingState == #ON
    );}
    trans ap16 { applianceOn1 -> base where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ap17 { applianceOn1 -> c1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ap18 { applianceOn1 -> c2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ap19 { applianceOn1 -> c3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET &&
        heatingState == #OFF
    );}
    trans ap20 { applianceOn1 -> c4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE &&
        heatingState == #OFF
    );}

    // Turn appliance1 OFF
    trans ap21 { heating -> applianceOff1 where (applianceState1 == #ON); }
    trans ap22 { h1 -> applianceOff1      where (applianceState1 == #ON); }
    trans ap23 { h2 -> applianceOff1      where (applianceState1 == #ON); }
    trans ap24 { h3 -> applianceOff1      where (applianceState1 == #ON); }
    trans ap25 { h4 -> applianceOff1      where (applianceState1 == #ON); }
    trans ap26 { c4 -> applianceOff1      where (applianceState1 == #ON); }
    trans ap27 { c3 -> applianceOff1      where (applianceState1 == #ON); }
    trans ap28 { c2 -> applianceOff1      where (applianceState1 == #ON); }
    trans ap29 { c1 -> applianceOff1      where (applianceState1 == #ON); }
    trans ap30 { base -> applianceOff1    where (applianceState1 == #ON); }

    trans ap31 { applianceOff1 -> heating where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ap32 { applianceOff1 -> h1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ap33 { applianceOff1 -> h2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ap34 { applianceOff1 -> h3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET &&
        heatingState == #ON
    );}
    trans ap35 { applianceOff1 -> h4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE &&
        heatingState == #ON
    );}
    trans ap36 { applianceOff1 -> base where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ap37 { applianceOff1 -> c1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ap38 { applianceOff1 -> c2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ap39 { applianceOff1 -> c3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET &&
        heatingState == #OFF
    );}
    trans ap40 { applianceOff1 -> c4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE &&
        heatingState == #OFF
    );}

    // Turn appliance2 ON
    trans ap41 { heating -> applianceOn2 where (applianceState2 == #OFF); }
    trans ap42 { h1 -> applianceOn2      where (applianceState2 == #OFF); }
    trans ap43 { h2 -> applianceOn2      where (applianceState2 == #OFF); }
    trans ap44 { h3 -> applianceOn2      where (applianceState2 == #OFF); }
    trans ap45 { h4 -> applianceOn2      where (applianceState2 == #OFF); }
    trans ap46 { c4 -> applianceOn2      where (applianceState2 == #OFF); }
    trans ap47 { c3 -> applianceOn2      where (applianceState2 == #OFF); }
    trans ap48 { c2 -> applianceOn2      where (applianceState2 == #OFF); }
    trans ap49 { c1 -> applianceOn2      where (applianceState2 == #OFF); }
    trans ap50 { base -> applianceOn2    where (applianceState2 == #OFF); } 

    // State memory after turning appliance2 on
    trans ap51 { applianceOn2 -> heating where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ap52 { applianceOn2 -> h1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW
    );}
    trans ap53 { applianceOn2 -> h2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ap54 { applianceOn2 -> h3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET &&
        heatingState == #ON
    );}
    trans ap55 { applianceOn2 -> h4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE &&
        heatingState == #ON
    );}
    trans ap56 { applianceOn2 -> base where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ap57 { applianceOn2 -> c1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ap58 { applianceOn2 -> c2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ap59 { applianceOn2 -> c3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET &&
        heatingState == #OFF
    );}
    trans ap60 { applianceOn2 -> c4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE &&
        heatingState == #OFF
    );}

    // Turn appliance2 OFF
    trans ap70 { heating -> applianceOff2 where (applianceState2 == #ON); }
    trans ap71 { h1 -> applianceOff2      where (applianceState2 == #ON); }
    trans ap72 { h2 -> applianceOff2      where (applianceState2 == #ON); }
    trans ap73 { h3 -> applianceOff2      where (applianceState2 == #ON); }
    trans ap74 { h4 -> applianceOff2      where (applianceState2 == #ON); }
    trans ap75 { c4 -> applianceOff2      where (applianceState2 == #ON); }
    trans ap76 { c3 -> applianceOff2      where (applianceState2 == #ON); }
    trans ap77 { c2 -> applianceOff2      where (applianceState2 == #ON); }
    trans ap78 { c1 -> applianceOff2      where (applianceState2 == #ON); }
    trans ap79 { base -> applianceOff2    where (applianceState2 == #ON); }

    trans ap80 { applianceOff2 -> heating where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ap81 { applianceOff2 -> h1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ap82 { applianceOff2 -> h2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW &&
        heatingState == #ON
    );}
    trans ap83 { applianceOff2 -> h3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET &&
        heatingState == #ON
    );}
    trans ap84 { applianceOff2 -> h4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE &&
        heatingState == #ON
    );}
    trans ap85 { applianceOff2 -> base where (
        smallRoomState == #BELOW &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ap86 { applianceOff2 -> c1 where (
        smallRoomState == #TARGET &&
        mediumRoomState == #BELOW &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ap87 { applianceOff2 -> c2 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #TARGET &&
        largeRoomState == #BELOW &&
        heatingState == #OFF
    );}
    trans ap88 { applianceOff2 -> c3 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #TARGET &&
        heatingState == #OFF
    );}
    trans ap89 { applianceOff2 -> c4 where (
        smallRoomState == #ABOVE &&
        mediumRoomState == #ABOVE &&
        largeRoomState == #ABOVE &&
        heatingState == #OFF
    );}
```
