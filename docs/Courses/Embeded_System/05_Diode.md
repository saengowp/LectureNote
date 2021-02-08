## Diode

Diode is a semiconductor that will only allow the current to pass
in a certain direction.

```
A diode in forward-bias mode, allowing the current to pass

 + --- |>| ---- -
```

### Basic Knowledge

- $V=IR$
- Kirchhoff's current law
	- Current in = Current out

### Application

#### AC-DC Rectifier

##### Half-wave rectifier

Simply insert diode between AC-source and load

##### Full-wave Rectifier

In center-tapped transformer, the center of the coil tapped to ground causing the upper and lower end of the coil to 
have opposite voltage. Use diode to connect positive output to both end and we will be able to convert on both
positive and negative crest. Note that only half the winding is avalable thus half the transformer output voltage.

In bridge rectifier, we connect the load with 4 diodes, 2 for each half-wave. enabling it to work for both directions.

Bridge rectifier is better than Center-tapped transformer because CTT is expensive to build and only use half the winding
limiting current available.

#### Logic Gate

- OR-gate
	- Connect diodes at the input side so that the inputs can change independently
	- pull down the output
	- When one of the inputs is high, the pull down will be overcome putting output high
- AND-gate
	- Connect diodes at the input side in a open collector pattern
	- pull up the output
	- When all of the outputs are high, the current won't be drained from the pulled-up output, making it high

### Solving circuit

1. Guess the diodes's bias. 
	- if it is forward-biased, assume it to be a closed switch
2. Calculate all the voltages
3. See if it make sense

### Physical Mechanism

In semiconductor, Conduction band and valence band are very close together, causing semiconductor to easily conduct due to
presence of very close, available energy level for kinetic energy of the electron.

In presence of doping, which either partially fill the conduction band (by doping 5 valence atom in group 4 lattice)
making it conduct electron (n-type) or partially removed the valence band (by doping 3 valence atom) creating "hole" (p-type).

When p and n-type are put together in a junction. hole and electron start to combines, leaving *depletion region* which are electric field
that oppose the migration of charges due to charge imbalance between proton and electron. 
(note that this electric field can't be neutralized like in metal because charge-carrier type restriction)

When positive voltage is applied to the p-side, it oppose and override the depletion region's electric field, causing charges to conduct.

### Practical Diode

- There're some resistance
- In forward-bias, there is .7 V voltage drop to overcome barrier.
- When reverse bias voltage exceed breakdown voltage, the diode may conduct or be destroyed
