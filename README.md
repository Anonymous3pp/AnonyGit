# LatVision
Prediction for Tail Lateny in SSD.

NOTE: Please read the README first before running the workflows.

This package contains following files:
Data contains data collection scripts.
Models include modules for implementing, training, and predicting modules.
Requirements include packages that need to be installed in advance.

This artifact is designed to be run LatVision. Specifically, it will conduct the following steps:
Firstly, the name of disk to be tested is /dev/nvme0n1.
1. Data collection: Run load and synchronously obtain the data from kernel.
   sudo ./Data/writer /dev/sde 'testTraces/testdrive.trace'
   
2. Choose a model for training, which will last for 30-60 minutes. Taking MobileNet as an example.
   cd Models/mobilenet
   python train.py ../Data/testTraces/testdrive.trace
   
3. Make predictions during system operation.
   nohup sudo ../replayer_fail /dev/sde ../Data/testTraces/testdrive.trace
   python predict.py ../result/

 
