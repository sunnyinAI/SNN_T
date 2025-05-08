# TASB-SNN

## Dependencies
- Python 3
- PyTorch, torchvision
- spikingjelly 0.0.0.0.12
- Python packages: `pip install tqdm progress torchtoolbox`


### SLTT
CIFAR-10, CIFAR-100, DVS-CIFAR10, and DVS-Gesture:

    # CIFAR-10
	python train_TASB.py -data_dir ./data -dataset cifar10 -model spiking_resnet18 -amp -T_max 200 -epochs 200 -weight_decay 5e-5
    
    # CIFAR-100
    python train_TASB.py -data_dir ./data -dataset cifar100 -model spiking_resnet18 -amp -T_max 200 -epochs 200 -weight_decay 5e-4
       
    # DVS-CIFAR10
	python train_TASB.py -data_dir ./data/CIFAR10DVS -dataset DVSCIFAR10 -T 10 -amp -drop_rate 0.3 -model spiking_vgg11_bn -lr=0.05 -weight_decay 5e-4 -mse_n_reg
	
	# DVS-Gesture
    python train_TASB.py -data_dir ./data/dvsgesture -dataset dvsgesture -model spiking_vgg11_bn -T 20 -b 16 -amp -drop_rate 0.4 -weight_decay 5e-4


    
### SLTT-K
For DVS-Gesture, DVS-CIFAR10, and ImageNet, please run the following example codes:

    # DVS-Gesture
    python train_TASB.py -K 4 -data_dir ./data/dvsgesture -dataset dvsgesture -model spiking_vgg11_bn -T 20 -b 16 -amp -drop_rate 0.4 -weight_decay 5e-4
    
    # DVS-CIFAR10
	python train_TASB.py -K 2 -data_dir ./data/CIFAR10DVS/ -dataset DVSCIFAR10 -T 10 -amp -drop_rate 0.3 -model spiking_vgg11_bn -lr=0.05 -weight_decay 5e-4 -mse_n_reg


### BPTT
We also provide the BPTT implementation for comparison. For running the BPTT method, please refer directly to the commands for SLTT while changing "train_TASB.py" to "train_BPTT.py". 
We give an example for CIFAR-10 as following.

	python train_BPTT.py -data_dir ./data -dataset cifar10 -model spiking_resnet18 -amp -T_max 200 -epochs 200 -weight_decay 5e-5
    

## Credits

The code for data preprocessing and neuron models is based on the [spikingjelly](https://github.com/fangwei123456/spikingjelly) repo. The code for some utils is from the [pytorch-classification](https://github.com/bearpaw/pytorch-classification) repo.


