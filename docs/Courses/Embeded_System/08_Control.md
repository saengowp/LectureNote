# Control and Feedback

Determine and maintains state of the system despite variation in environment.

## Type

### Open-loop

The system output based on user's input goal. eg. driving. cooker with no temperature feedback.

### Closed-loop

User set the goal and the system constantly monitor the state and output accordingly. eg. temperature-controlled air-conditioner.

```
Input (X_i) --> Substractor -- (error signal) --> Forward Path (g) --> Output
               ^                                          |
	       |----------- Feedback Path (h) <----------------
```

[SKIPPED Frequency, Gain bandwidth]

# PID Control for Embedded Systems

PID (Proportional, Integral, Derivative) control, is a feedback control.

In simple feedback control where we actuate to counter the deviation immediately,
when the sensing or actuating element is delayed. the state will oscillate due to overcorrection.

In porportional control, the output is `Kp * error`, This may still underdamp or overdamp the system.


