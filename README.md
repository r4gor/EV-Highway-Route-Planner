# EV Highway Route Planner

Final project for **Algorithms and Data Structures** at Politecnico di Milano (A.Y. 2022–2023), written in C.
**Grade: 30 cum laude / 30.**

A highway is a line of service stations, each renting electric cars with different ranges. The program reads a
stream of commands (add or demolish a station, add or scrap a car, plan a route) and, for each route request,
finds the path between two stations **with the fewest stops**, breaking ties in favour of stops closer to the
start of the highway. It must work in both directions and pass strict time and memory limits.

## How it works

- **Stations in an AVL tree** keyed by distance, so inserts, deletes and in-order neighbour lookups stay
  O(log n). Each node keeps its fleet and its maximum range, so the planner never scans every car.
- **Route search** explores reachable stations with a priority queue (binary heap), walking the tree with
  successor and predecessor instead of building a full graph. Each station records its step count and the
  previous stop, so the path is rebuilt at the end with the tie-break rule applied.
- Plain C with no dependencies, in a single file: [`18.c`](18.c).

## Run

```bash
gcc -O2 -o planner 18.c
./planner < input.txt
```

The original problem statement (in Italian) is in [`Testo Prova Finale 2023.pdf`](Testo%20Prova%20Finale%202023.pdf).
