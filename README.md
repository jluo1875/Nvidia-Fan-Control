# NvidiaGPUFanControl
Fan Control for Nvidia GPUs.

# Setup
Controlling nvidia gpu fan requires an `X` server to be running.

Setup x config in a shell like below. You may need to use `sudo`.

```
$ nvidia-xconfig --enable-all-gpus --cool-bits=7 --connected-monitor=Monitor0 --allow-empty-initial-configuration --force-generate
```
```
$ xinit &
```
```
$ pip install gpufan
```
# Usage
```
$ gpufan constant -g 0 -s 60
```
The above script, puts GPU 0 in `constant` mode with 60% speed. You can use `aggressive` or `driver` modes too.
In aggressive mode, a small increase in temperature causes a large increase in fan speed.

gpufan.aggressive(second_gpu)

The bottom commands give control back to the driver manually. Please note that after execution is finished, this line is automatically called so you don't have to.

gpufan.driver(first_gpu)
gpufan.driver(second_gpu)
```
