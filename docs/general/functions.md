# EcoSim Functions

This file contains all the functions used in the EcoSim model for energy-saving optimization.These functions handle time management, heating, cooling, lighting energy calculations, and appliance energy usage. 

```java
    // Time Functions
    function incrementGlobalTime:real(increment:real, globalTime:real) {
        return globalTime + increment;  // Time increment
    }
    function decrementGlobalTime:real(decrement:real, globalTime:real) {
        return globalTime - decrement; // Time decrement
    }
```
These functions manage the global time in the simulation. 
The `incrementGlobalTime` function adds a specified increment 
to the current global time, simulating the passage of time. 
The `decrementGlobalTime` function subtracts a specified 
decrement from the current global time, allowing for adjustments 
or time rewinding within the simulation.
```java
    //Heating Function
    function heatRoom:real(currentTemp:real, rate:real, rValue: real, outsideTemp: real, timeStep: real) {
    real tempDiff = currentTemp - outsideTemp;  
    real heatGain = (rate * rValue) * (1 - (tempDiff / 100));  
    return currentTemp + (heatGain * timeStep / 60);  
    }
```
Increases the current temperature of a room over the defined time step.
The heating rate is influenced by the room's size, insulation (rValue), 
and the difference between current and outside temperatures.
```java
    // Cooling Function
    function coolRoom:real(currentTemp:real, rate:real, rValue: real, outsideTemp: real, timeStep: real) {
    real tempDiff = outsideTemp - currentTemp; 
    real coolRate = (rate * rValue) * (1 - (tempDiff / 100));  
    return currentTemp - (coolRate * timeStep / 60);    
    }
```
Decreases the current temperature of a room over the defined time step.
The cooling rate is influenced by room size, insulation (rValue), 
and the difference between outside and current temperatures.
```java
    // Lighting Function
    function calculateLightEnergy:real(onTime:real, offTime:real) {
        return (((offTime - onTime) / timeStep) * lightingEnergyUnit); // Find how long light was on * rate of energy unit
    }
```
Calculates the energy used by lighting systems based on 'on' and 'off' times. 
The function uses the defined lighting energy unit to quantify usage.
```java
    // Appliance Function
    function calculateApplianceEnergy:real(onTime:real,offTime:real) {
        return (((offTime - onTime) / timeStep) * applianceEnergyUnit); // Find how long appliance was on * rate of energy unit
    }
```
Calculates the energy used by appliances based on 'on' and 'off' times.
The function uses the defined appliance energy unit to quantify usage.
```java
    // Energy Function
    function updateEnergyUsage:real(energyUsed:real, energyType:real) { // Update overall energy usgae
        return energyUsed + energyType;
    }
Updates the total energy usage by adding the new energy type to the current total.
```
