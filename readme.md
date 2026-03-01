# Balanced Multi-Vehicle Routing Problem (VRP) using Genetic Algorithms
This repository contains a Python script that solves a simplified, workload-balanced Multi-Vehicle Routing Problem (VRP) using a Genetic Algorithm (GA). The algorithm is implemented using the DEAP (Distributed Evolutionary Algorithms in Python) framework.
## Overview

The script aims to find the optimal delivery routes for a fleet of vehicles starting and ending at a central depot. It assigns a set of randomly generated delivery locations to the vehicles while optimizing for two main objectives:

1.Minimizing total travel distance: Reducing the overall distance covered by the entire fleet.

2.Balancing the workload: Minimizing the standard deviation of the distances traveled by each vehicle so that no single vehicle does all the work.

## Dependencies
1.Deap

2.Numpy

3.Pandas

4.Random

5.Matplotlib

# How It Works
## Problem Setup
Depot: The starting and ending point for all vehicles is fixed at coordinates (40, 40).

Locations: Generates 10 random coordinates (ranging from 0 to 100 on both X and Y axes) to represent delivery addresses.

Vehicles: The fleet consists of 3 vehicles.

## Route Assignment Strategy
The algorithm represents an individual (a potential solution) as a permutation of the location indices (0 through 9). To assign locations to specific vehicles, the script uses a round-robin slicing method. For example, Vehicle 0 gets indices 0, 3, 6, 9, Vehicle 1 gets 1, 4, 7, and Vehicle 2 gets 2, 5, 8 from the permuted list.

## Genetic Algorithm Configuration
Fitness Evaluation: A multi-objective minimization function (-1.0, -1.0). It calculates both the total distance and the standard deviation of distances between vehicles (the balance penalty).

Crossover: Partially Matched Crossover (cxPartialyMatched), which is ideal for permutation-based representations to prevent duplicate or missing locations.

Mutation: Shuffle Indexes (mutShuffleIndexes) with a 5% independent probability of mutating an attribute.

Selection: Tournament Selection (selTournament) with a tournament size of 3.

Evolution: Runs for 300 generations with a population size of 300, a crossover probability of 70%, and a mutation probability of 20%.

# Output
## When you run the script, it will:

Print the evolutionary statistics (minimum and average fitness values) for each generation to the console.

Open a matplotlib window displaying the optimal route found by the Hall of Fame. The depot is marked as a red square (rs), the delivery locations as blue dots (bo), and the routes of the 3 vehicles as continuous lines.