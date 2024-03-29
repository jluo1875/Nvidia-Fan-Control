# Nvidia GPU Fan Control
Fan Control for Nvidia GPUs for Linux. It gives control back to the driver after work is finished, can be used as standalone Python script. It was a passion project of mine, being a learning experience into how drivers and fan curves work. 

# How to Setup
Controlling nvidia gpu fan requires an `X` server to be running and be on Linux.

Follow these commands to set up the X server. 

```
$ nvidia-xconfig --enable-all-gpus --cool-bits=7 --connected-monitor=Monitor0 --allow-empty-initial-configuration --force-generate
```
```
$ xinit &
```
```
$ pip install gpufan
```
# How to Use
You can use command line script:

```
$ gpufan constant -g 0 -s 60
```

Or in a python script:

```python
import gpufan

first_gpu = 0
gpufan.constant(first_gpu, 60)
```
The above script, puts GPU 0 in `constant` mode with 60% speed. You can use `aggressive` or `driver` modes too.

In aggressive mode, a small increase in temperature causes a large increase in fan speed.
```
gpufan.aggressive(second_gpu)
```

The bottom commands give control back to the driver manually. Please note that after execution is finished, this line is automatically called so you don't have to.
```
gpufan.driver(first_gpu)
gpufan.driver(second_gpu)
```
