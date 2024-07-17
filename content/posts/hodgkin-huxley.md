+++
title = 'The Hodgkin-Huxley Model'
date = 2024-07-17T15:13:49+08:00
draft = false
tags = ['neuroscience']
+++

Most of the following contents comes from [this document](https://www.math.mcgill.ca/gantumur/docs/reps/RyanSicilianoHH.pdf) by Ryan Siciliano. 

## Anatomy Of Neuron

<div align="center">
<img src=/images/Neuron.png width=100% />
</div>

- Neurons receive signals through dendrites located on the main bulk of the cell. 

- From there, the signal is propagated through the body and sent along the axon to the next neuron.

- Neurons send signals to other neurons via action potentials.

- An action potential is an explosion of depolarizing current that travels along the cell.

- For an action potential to occur, the depolarization must reach a minimum threshold voltage.

- Action potentials do not vary in size and will not occur if threshold is not reached.

## Action Potential

Steps:

1. The firing threshold is reached and the action potential begins to fire. The sodium channels are now open and an influx of sodium occurs.
2. The membrane becomes more positive at this point due to sodium entering the cell. The potassium channels open and potassium leaves the cell.
3. At the peak of the action potential, the sodium channels have now become refractory and no more sodium is allowed to enter.
4. The sodium channel is still in its refractory stage and only the potassium ions are passing through the membrane. The membrane potential moves toward the resting value.
5. The potassium channels close and the sodium channels begin to leave the refractory phase and reset to its resting phase.
6. The diffusion of extracellular potassium away from the cell causes a very slight increase in membrane voltage. It finally returns to its resting value.

## Mathematical Model

<div align="center">
<img src=/images/H-H.png width=90% />
</div>

- Membrane functions like a capacitor in an electrical circuit.
- Ion channels allow ions to flow into or out of the neuron, which changes the membrane potential.
- Gates are mechanisms within ion channels that control the opening and closing of the channel.

$$C_m\frac{dV_m}{dt} + I_{ion} = I_{ext}$$

$C_m$: membrance capacitance

$V_m$: membrance potential

$I_{ext}$: external current

$I_{ion}$: ionic currents($I_{ion} = I_{Na} + I_{K} + I_{L}$), sum of currents  through sodium, potassium, and leakage channels

$$I_{Na} = G_{Na}(V_m - E_{Na})$$
$$I_{K} = G_{K}(V_m - E_k)$$
$$I_{L} = G_{L}(V_m - E_L)$$

$G_{Na}$， $G_{K}$， $G_{L}$：the conductances of sodium, potassium, and leakage channels

$E_{Na}$， $E_{K}$， $E_{L}$：the equilibrium potentials for sodium, potassium, and leakage channels

- The conductance $G$ is caused by the opening of many microscopic channels in the membrane.

- Each individual membrane contains many gates.

- When all gates are in the *permissive* state (allows ions to pass through) then the channel is considered to be *open*.

- The probability of a gate being in the permissive state depends on the current value of the membrane voltage.

Conductance equations:
$$\frac{dp_i}{dt}=\alpha_i(V)(1-p_i)-\beta_i(V)p_i$$

$p_i$: the probability of ion $i$'s gate being open, or the fraction of gates that are
in the permissive state.

$\alpha_i$, $\beta_i$: rate constants dependent on the voltage that describe the transient rates of permissive and non-permissive gates.
<p>
$$G_i=\bar{g}_l\prod_{i} p_i$$
</p>
$\bar{g}_l$: normalized constant that determines the maximum conductance when all the channels are open.

Each channel is defined to have a specific amount of gates $p_i$ exchanged with names $m,n,h$:
<p>
$$I_{ion}=\bar{g}_{Na}m^3h(V_m-E_{Na}) + \bar{g}_{K}n^4(V_m-E_{K}) + \bar{g}_{L}(V_m-E_{L})$$ 
</p>

$$\frac{dm}{dt}=\alpha_m(V)(1-m)-\beta_m(V)m$$
$$\frac{dn}{dt}=\alpha_n(V)(1-n)-\beta_n(V)n$$
$$\frac{dh}{dt}=\alpha_h(V)(1-h)-\beta_n(V)h$$