# Instructions

To setup, run:
```bash
python setup.py
```
Then start the application with:
```bash
p4app run .
```
and in a different terminal window, start the periodic filter reset with:
```bash
bash filter_reset.sh
```

The heavy hitter filter drops packets of heavy hitter flows when they go over their budget.
The filter currently allows 1000 bytes/sec (you can change that value in setup.py).

In the minigraph window, you can try:
```
h1 ping -s 80 -i 0.1 h2
```
With this command h1 sends a packet with a total IP length of 100 bytes every 100 ms.
When you run this command, you shouldn't see any drops. If on the other hand you run:
```
h1 ping -s 80 -i 0.05 h2
```
h1 sends a packet every 50 ms, which puts the flow above the filter limit. In this case you will 
observe that about half of the packets send by h1 are being dropped at the switch.
