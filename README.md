# MDP REPRESENTATION

### NAME : KISHORE N
### REG NO : 212222240049

## AIM:

To represent a Markov Decision Process(MDP) problem in the following ways.

1.Text representation

2.Graphical representation

3.Python - Dictonary representation

## PROBLEM STATEMENT:

### Problem Description
An RL agent controls a single intersection’s traffic light to minimize vehicle waiting and avoid congestion. At each decision step it chooses to Wait (keep current phase) or Switch (change phase). Traffic arrivals are stochastic, so outcomes are probabilistic; the agent learns a policy that balances clearing queues and avoiding needless switches.

### State Space
S = {
S0: Low Traffic (few cars waiting),
S1: Medium Traffic (moderate queue),
S2: High Traffic (long queue / risk of jam)
}

### Sample State
S1 (Medium Traffic) — about 6 cars waiting across approaches.

### Action Space
A = {
A0: Wait — keep current light (no immediate change),
A1: Switch — change the green phase to the other approach
}

### Sample Action
From S2 (High Traffic): take Switch (A1) to relieve the congested approach.

### Reward Function
If resulting state is Low → +10.

If resulting state is Medium → +5.

If resulting state is High → -10.

Optionally add a small penalty for switching (e.g., −1) if you want to discourage frequent flips.
(Immediate reward = reward of next state ± action cost.)

### Graphical Representation

<img width="1190" height="1178" alt="traffic_light_rl" src="https://github.com/user-attachments/assets/0408e86a-2471-4a26-b7f7-12364c2680c7" />

## PYTHON REPRESENTATION:
```
P = {
    1: {   # Green State
        0: [(0.8, 1, -1, False), (0.2, 2, +10, False)],  # Stay green or change to yellow
        1: [(1.0, 2, +10, False)]                        # Force change to yellow
    },
    2: {   # Yellow State
        0: [(0.7, 2, -1, False), (0.3, 3, +10, False)],  # Stay yellow or change to red
        1: [(1.0, 3, +10, False)]                        # Force change to red
    },
    3: {   # Red State
        0: [(0.8, 3, -1, False), (0.2, 1, +10, False)],  # Stay red or change to green
        1: [(1.0, 1, +10, False)]                        # Force change to green
    }
}
```

## OUTPUT:
```
{1: {0: [(0.8, 1, -1, False), (0.2, 2, 10, False)], 1: [(1.0, 2, 10, False)]},
 2: {0: [(0.7, 2, -1, False), (0.3, 3, 10, False)], 1: [(1.0, 3, 10, False)]},
 3: {0: [(0.8, 3, -1, False), (0.2, 1, 10, False)], 1: [(1.0, 1, 10, False)]}}
```

## RESULT:
Thus the given real world problem is successfully represented in a MDP form.
