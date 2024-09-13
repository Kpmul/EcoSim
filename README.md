# EcoSim: Energy-Saving Optimisation for Homes and Buildings

## Overview
EcoSim was developed as part of a Master's dissertation project at Maynooth University, using Cyclone, a specification language designed around graph theory for system modelling and testing, developed by Hao Wu at Maynooth University. The goal of the project is to create a tool that helps optimise energy usage in homes and buildings by modelling key components such as heating systems, appliances, and lighting, with consideration of real-world variables.

## Features
- **Comprehensive Modeling:** Models heating systems, appliances, and lighting to reflect various residential and commercial settings.
- **Energy Optimisation:** Analyzes different configurations to recommend the most efficient energy usage.
- **Real-World Variables:** Considers parameters like insulation rates, system capacities, and building characteristics to simulate realistic scenarios.

## Project Structure
- **Main File:** `EcoSim.cyclone` - The full implementation of the energy optimization model using Cyclone.

- **Components:** Although Cyclone operates as a single-file system, conceptual breakdowns are provided for better understanding:
  
- **States:**
 - `heatingStates.md` - Explanation of heating system states.
 - `applianceStates.md` - Explanation of appliance states.
 - `lightingStates.md` - Explanation of lighting system states.
 - `coolingStates.md` - Explanation of cooling system states.
 - `initStates.md` - Initialization states.
   
- **Transitions:**
  - `heatingTransitions.md` - Details on heating system transitions.
  - `applianceTransitions.md` - Details on appliance transitions.
  - `lightingTransitions.md` - Details on lighting system transitions.
  - `coolingTransitions.md` - Details on cooling system transitions.
  - `entryNodes.md` - Overview of entry nodes.
  - `entryNodeTransitions.md` - Details on transitions for entry nodes.
    
- **General:**
  - `functions.md` - Overview of functions used in the model.
  - `initVariables.md` - Initialization variables.
  - `goal.md` - Description of the goal for the model.
