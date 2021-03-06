# Dynamic Precision Scaling

This repository is created to reproduce the results in the paper:

“[Speeding up Convolutional Neural Network Training with Dynamic Precision Scaling and Flexible Multiplier-Accumulator](http://dl.acm.org/citation.cfm?id=2934625),”
Taesik Na and Saibal Mukhopadhyay,
International Symposium on Low Power Electronics and Design (ISLPED), Aug 2016

Please cite our paper in your publications if it helps your research.


### Installing

Please follow the general guideline to install caffe and pycaffe on you local machine.
* [Caffe](https://github.com/BVLC/caffe) - The original Caffe repository


### Running

After you install pycaffe, download mnist data set.

```
cd $CAFFE_ROOT/data/mnist
./get_mnist.sh
cd $CAFFE_ROOT/examples/mnist
./create_mnist.sh
```

And then,

```
cd $CAFFE_ROOT/work/dps/lenet/dynamic_16_32
python learning_fixed_lenet.py
```

This will reproduce the figure 4(b) in our paper.

## Knobs to control DPS

Please feel free to change fixed_lenet_auto_solver.prototxt file to control DPS algorithm.

```
save_loss: 1 for saving loss, smoothed loss and total_bit_width for debugging purpose.
save_loss_prefix: prefix for the file to be saved.
average_loss: moving average window for smoothed loss
target_length: initial target bit width (excluding sign bit)
max_length: maximum allowable bit width (excluding sign bit)
bit_step: unit bit step for DPS
```

Enjoy!
