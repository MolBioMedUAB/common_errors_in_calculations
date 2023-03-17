# Heating is not successful

## Description

When the heating is not successful in an AMBER MD simulation, either the energy or temperature explode (start to increase to very high values represented as *** or NaN) or the heating stage does not start.

## Raised errors

This has not a unique associated error. Until today, the following errors have been associated:

- `Error: an illegal memory access was encountered launching kernel kNLSkinTest`
- 

## Possible solutions

- Minimise more the initial structure (increase maxcyc and optionally ncyc). Once the minimum is reached, the minimisation is stopped, so do not hesitate to use much higher maxcyc value.
- Increase the restraint weights in `minimisation` and/or in `heating` stages.
- Decrease the timestep in `heating` to 0.001 ps.
- Increase the collision frequency of the thermostat in `heating` (_gamma\_ln_) to 3, 5 or even 10. 

