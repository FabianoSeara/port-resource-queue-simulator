# 🚛 Resource Queue Simulator for Port Operations

Simulation for port operations: trucks arrive requiring a specific type of equipment (RTG or Reach Stacker), and the system automatically allocates a compatible available equipment. When no equipment is free, the truck enters a waiting queue (FIFO) and is served automatically as soon as an equipment of the correct type is released.

This project was born from my practical experience as a crane operator at a port terminal, where allocating equipment to serve trucks is a real daily process. The goal was to model this logic in code, applying data structures and business rules.

## Features

- **Automatic equipment allocation:** finds the first available equipment matching the truck's required type (RTG or RS).
- **Automatic departure time calculation:** based on the arrival time and estimated service duration.
- **FIFO waiting queue:** trucks without available equipment wait; when an equipment is released, the first compatible truck in the queue is processed automatically.
- **Equipment release:** simulates the equipment finishing a service and becoming available again.
- **Statistics report:** total trucks served, waiting, sum, and average service time.

## Technologies

- Python 3 (no external dependencies)
- `datetime` / `timedelta` (standard library for time calculations)

## Project Structure

```text
port-resource-queue-simulator/
├── dados.py      # Sample data: list of equipment and trucks
├── logica.py     # Business logic: allocation, release, queue, and report
├── main.py       # Runs the complete simulation and prints the reports
└── README.md


How the logic works (summary)

Each truck has a required equipment type (equipment_needed).

find_available_equipment looks for a free equipment of that type.

If found, process_truck allocates the equipment and calculates the truck's departure time.

If not found, the truck remains waiting (departure_time: None).

When an equipment is released (release_equipment), process_queue_after_release automatically checks if any truck is waiting for that type and processes it (FIFO).


How to run

No dependencies to install — just Python 3.

git clone https://github.com/FabianoSeara/port-resource-queue-simulator.git
cd port-resource-queue-simulator
python main.py


Example Output

truck ABC1234 allocated equipment 2 (RTG)
truck AXF 3333 allocated equipment 5 (RS)
truck GHI9012 allocated equipment 3 (RTG)
Truck JKL3456 waiting, no RS available.
Truck DEF5678 waiting, no RTG available.
============================================================
FINAL REPORT
============================================================
served trucks: 3
waiting trucks: 2
total trucks: 5
total duration sum: 75
average service time: 25.0

--- Simulating equipment 2 release ---
Found Truck DEF5678 waiting for RTG
truck DEF5678 allocated equipment 2 (RTG)
...
served trucks: 5
waiting trucks: 0


## Next Steps

□ Real-time simulation (clock ticking minute-by-minute) instead of manual releases
□ Random test data generation (more trucks, more equipment)
□ Export final report to CSV

---

Project developed by Fabiano Seára as part of my portfolio for transitioning to a software development career, with AI (Claude) assistance in the learning process.
