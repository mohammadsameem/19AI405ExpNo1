# ExpNo 1: Developing AI Agent with PEAS Description

**Name:** Mohamed Sameem
**Register Number:** 212225040242
**Date:** 20/10/2026

---

## AIM

To find the PEAS description for the given AI problem and develop an AI agent.

## Theory

### Medicine prescribing agent

This agent prescribes medicine for fever (greater than 98.5 degrees), which we consider here as unhealthy, based on the user's temperature input. The environment is the rooms in a hospital (two rooms). The agent has to consider two factors: the room location, and an unhealthy patient in a random room. The agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing the performance for each treatment; each time after treating in one room, it has to check the other room, and this movement reduces its performance. Hence, the agent prescribes medicine to the unhealthy.

---

## PEAS Description

| Agent Type | Performance | Environment | Actuators | Sensors |
|---|---|---|---|---|
| Medicine prescribing agent | Treating unhealthy, agent movement | Rooms, Patient | Medicine, Treatment | Location, Temperature of patient |

---

## Design Steps

### Step 1: Identifying the input
Temperature from patients, Location.

### Step 2: Identifying the output
Prescribe medicine if the patient in a random room has a fever.

### Step 3: Developing the PEAS description
The PEAS description is developed from the performance measure, environment, actuators, and sensors of an agent.

### Step 4: Implementing the AI agent
Treat unhealthy patients in each room, and check for unhealthy patients in a random room.

### Step 5: Measuring the performance parameters
For each treatment, performance is incremented; for each movement, performance is decremented.

---

## Program

```python
import random

class MedicinePrescribingAgent:
    def __init__(self):
        self.rooms = {
            "Room 1": random.uniform(97.0, 102.5),
            "Room 2": random.uniform(97.0, 102.5)
        }
        self.performance = 0
        self.current_room = random.choice(list(self.rooms.keys()))

    def sense(self):
        """Sense current room and patient's temperature."""
        temperature = self.rooms[self.current_room]
        print(f"\nAgent is in {self.current_room}")
        print(f"Patient Temperature: {temperature:.1f}°F")
        return temperature

    def prescribe_medicine(self, temperature):
        """Treat patient if temperature is above 98.5°F."""
        if temperature > 98.5:
            print("Patient has fever.")
            print("Medicine Prescribed.")
            self.performance += 1
        else:
            print("Patient is healthy.")
            print("No medicine required.")

    def move(self):
        """Move to the other room."""
        previous_room = self.current_room
        self.current_room = "Room 2" if self.current_room == "Room 1" else "Room 1"
        print(f"\nMoving from {previous_room} to {self.current_room}")
        self.performance -= 1

    def run(self):
        print("=== Medicine Prescribing Agent ===")
        temperature = self.sense()
        self.prescribe_medicine(temperature)
        self.move()
        temperature = self.sense()
        self.prescribe_medicine(temperature)
        print("\nFinal Performance:", self.performance)

agent = MedicinePrescribingAgent()
agent.run()
```

## Output

<img width="545" height="536" alt="image" src="https://github.com/user-attachments/assets/f1559574-3d58-4be1-b49d-fb7502a63b87" />


## Result

Thus, the PEAS description for the given AI problem was found and an AI agent was developed.
