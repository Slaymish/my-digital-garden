# EEEN Transparent D Latch

Here is the truth table for a transparent D latch:


D    EN    Q
0     0     Q(t)
0     1      0
1     0     Q(t)
1     1     D


Where:

- `D` is the data input
- `EN` is the enable input
- `Q` is the output
- `Q(t)` is the previous output state (at time t)

This truth table shows that if the enable input (EN) is low (0), the output (Q) will maintain its previous state, regardless of the data input (D). If the enable input is high (1), then the output will follow the data input.


***

Sure! Here's the truth table for an edge-triggered D flip-flop:

```
D     CLK    Q(t)    Q(t+1)
-----------------------------
0     0      Q       Q
0     1      Q       Q
1     0      Q       Q
1     1      Q       D
```

Where `D` is the input signal, `CLK` is the clock signal, `Q(t)` is the current output state of the flip-flop, and `Q(t+1)` is the next output state of the flip-flop after the active edge of the clock signal.