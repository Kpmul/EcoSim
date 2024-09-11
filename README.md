# EcoSim: Energy-Saving Optimisation for Homes and Buildings

## Overview
EcoSim was developed as part of a Master's dissertation project at Maynooth University, using Cyclone, a specification language designed around graph theory for system modelling and testing, developed by Hao Wu at Maynooth University. The goal of the project is to create a tool that helps optimize energy usage in homes and buildings by modelling key components such as heating systems, appliances, and lighting, with consideration of real-world variables.

## Features
- **Comprehensive Modeling:** Models heating systems, appliances, and lighting to reflect various residential and commercial settings.
- **Energy Optimisation:** Analyzes different configurations to recommend the most efficient energy usage.
- **Real-World Variables:** Considers parameters like insulation rates, system capacities, and building characteristics to simulate realistic scenarios.

## Project Structure
- **Main File:** `EcoSim.cyclone` - The full implementation of the energy optimization model using Cyclone.
- **Components:** Although Cyclone operates as a single-file system, conceptual breakdowns are provided for better understanding:
  - `heating_system.cyclone.md` - Explanation of heating system modelling.
  - `appliances.cyclone.md` - Details on appliance energy usage modelling.
  - `lighting.cyclone.md` - Insights into lighting system integration.
