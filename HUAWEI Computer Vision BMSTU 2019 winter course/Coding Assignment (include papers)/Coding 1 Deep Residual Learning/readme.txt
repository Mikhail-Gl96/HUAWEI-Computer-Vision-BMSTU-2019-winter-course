I used my own PC, so the version of Pytorch was >1.0.0
That's why we are needed in adaptaion of given code to a newest version of Pytorch rules:

In the 'pytorch-classification-master' folder, open 'cifar.py' in text editor and apply tne following changes:

1)	In line 247, change this lines of code:

		if use_cuda:
			inputs, targets = inputs.cuda(), targets.cuda(async=True)
	
	To this lines of code:
	
		if use_cuda:
			inputs, targets = inputs.cuda(), targets.cuda(non_blocking=True)
		
2)	In line 257, change this lines of code:

		losses.update(loss.data[0], inputs.size(0))
		top1.update(prec1[0], inputs.size(0))
		top5.update(prec5[0], inputs.size(0))
   
	To this lines of code:
	
		losses.update(loss.data, inputs.size(0))
		top1.update(prec1, inputs.size(0))
		top5.update(prec5, inputs.size(0))
   
3)	In line 314, change this lines of code:

		losses.update(loss.data[0], inputs.size(0))
		top1.update(prec1[0], inputs.size(0))
		top5.update(prec5[0], inputs.size(0))
   
	To this lines of code:
	
		losses.update(loss.data, inputs.size(0))
		top1.update(prec1, inputs.size(0))
		top5.update(prec5, inputs.size(0))

   
   
   
basic tasks:
python cifar.py -a resnet --depth 20 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar10/part1/20
python cifar.py -a resnet --depth 56 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar10/part1/56
python cifar.py -a resnet --depth 110 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar10/part1/110
python cifar.py -a resnet --depth 20 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar10/part2/20
python cifar.py -a resnet --depth 56 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar10/part2/56
python cifar.py -a resnet --depth 110 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar10/part2/110
python cifar.py -a resnet --depth 20 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar10/part3/20
python cifar.py -a resnet --depth 56 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar10/part3/56
python cifar.py -a resnet --depth 110 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar10/part3/110
python cifar.py -a resnet --dataset cifar100 --depth 20 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar100/part1/20
python cifar.py -a resnet --dataset cifar100 --depth 56 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar100/part1/56
python cifar.py -a resnet --dataset cifar100 --depth 110 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar100/part1/110
python cifar.py -a resnet --dataset cifar100 --depth 20 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar100/part2/20
python cifar.py -a resnet --dataset cifar100 --depth 56 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar100/part2/56
python cifar.py -a resnet --dataset cifar100 --depth 110 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar100/part2/110
python cifar.py -a resnet --dataset cifar100 --depth 20 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar100/part3/20
python cifar.py -a resnet --dataset cifar100 --depth 56 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar100/part3/56
python cifar.py -a resnet --dataset cifar100 --depth 110 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint results_required/cifar100/part3/110

optional 1
python cifar.py -a resnet --dataset cifar10 --depth 20 --lr 1 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-20L-lr1
python cifar.py -a resnet --dataset cifar100 --depth 20 --lr 1 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-206L-lr1
python cifar.py -a resnet --dataset cifar10 --depth 20 --lr 0.5 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-20L-lr0_5
python cifar.py -a resnet --dataset cifar100 --depth 20 --lr 0.5 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-20L-lr0_5
python cifar.py -a resnet --dataset cifar10 --depth 20 --lr 0.2 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-20L-lr0_2
python cifar.py -a resnet --dataset cifar100 --depth 20 --lr 0.2 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-20L-lr0_2
python cifar.py -a resnet --dataset cifar10 --depth 20 --lr 0.01 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-20L-lr0_01
python cifar.py -a resnet --dataset cifar100 --depth 20 --lr 0.01 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-20L-lr0_01
python cifar.py -a resnet --dataset cifar10 --depth 20 --lr 0.02 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-20L-lr0_02
python cifar.py -a resnet --dataset cifar100 --depth 20 --lr 0.02 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-20L-lr0_02
python cifar.py -a resnet --dataset cifar10 --depth 20 --lr 0.05 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-20L-lr0_05
python cifar.py -a resnet --dataset cifar100 --depth 20 --lr 0.05 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-20L-lr0_05
python cifar.py -a resnet --dataset cifar10 --depth 56 --lr 1 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-56L-lr1
python cifar.py -a resnet --dataset cifar100 --depth 56 --lr 1 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-56L-lr1
python cifar.py -a resnet --dataset cifar10 --depth 56 --lr 0.5 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-56L-lr0_5
python cifar.py -a resnet --dataset cifar100 --depth 56 --lr 0.5 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-56L-lr0_5
python cifar.py -a resnet --dataset cifar10 --depth 56 --lr 0.2 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-56L-lr0_2
python cifar.py -a resnet --dataset cifar100 --depth 56 --lr 0.2 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-56L-lr0_2
python cifar.py -a resnet --dataset cifar10 --depth 56 --lr 0.01 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-56L-lr0_01
python cifar.py -a resnet --dataset cifar100 --depth 56 --lr 0.01 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-56L-lr0_01
python cifar.py -a resnet --dataset cifar10 --depth 56 --lr 0.02 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-56L-lr0_02
python cifar.py -a resnet --dataset cifar100 --depth 56 --lr 0.02 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-56L-lr0_02
python cifar.py -a resnet --dataset cifar10 --depth 56 --lr 0.05 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-56L-lr0_05
python cifar.py -a resnet --dataset cifar100 --depth 56 --lr 0.05 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-56L-lr0_05
python cifar.py -a resnet --dataset cifar10 --depth 110 --lr 1 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-110L-lr1
python cifar.py -a resnet --dataset cifar100 --depth 110 --lr 1 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-110L-lr1
python cifar.py -a resnet --dataset cifar10 --depth 110 --lr 0.5 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-110L-lr0_5
python cifar.py -a resnet --dataset cifar100 --depth 110 --lr 0.5 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-110L-lr0_5
python cifar.py -a resnet --dataset cifar10 --depth 110 --lr 0.2 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-110L-lr0_2
python cifar.py -a resnet --dataset cifar100 --depth 110 --lr 0.2 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-110L-lr0_2
python cifar.py -a resnet --dataset cifar10 --depth 110 --lr 0.01 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-110L-lr0_01
python cifar.py -a resnet --dataset cifar100 --depth 110 --lr 0.01 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-110L-lr0_01
python cifar.py -a resnet --dataset cifar10 --depth 110 --lr 0.02 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-110L-lr0_02
python cifar.py -a resnet --dataset cifar100 --depth 110 --lr 0.02 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-110L-lr0_02
python cifar.py -a resnet --dataset cifar10 --depth 110 --lr 0.05 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_1/resnet-cifar10-110L-lr0_05
python cifar.py -a resnet --dataset cifar100 --depth 110 --lr 0.05 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_1/resnet-cifar100-110L-lr0_05
python cifar.py -a resnet --depth 20 --epochs 328 --schedule 162 244 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_2/20
python cifar.py -a resnet --depth 56 --epochs 328 --schedule 162 244 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_2/56
python cifar.py -a resnet --depth 110 --epochs 328 --schedule 162 244 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_2/110
python cifar.py -a resnet --dataset cifar100 --depth 20 --epochs 82 --schedule 41 61 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_2/20
python cifar.py -a resnet --dataset cifar100 --depth 56 --epochs 82 --schedule 41 61 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_2/56
python cifar.py -a resnet --dataset cifar100 --depth 110 --epochs 82 --schedule 41 61 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_2/110

optional 2:

python cifar_optional_1_3-1.2.py -a resnet --depth 56 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_3/resnet-cifar10-56L-1.2
python cifar_optional_1_3-1.2.py -a resnet --depth 110 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_3/resnet-cifar10-110L-1.2
python cifar_optional_1_3-1.5.py -a resnet --dataset cifar100 --depth 56 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_3/resnet-cifar100-56L-1.5
python cifar_optional_1_3-1.5.py -a resnet --dataset cifar100 --depth 110 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_3/resnet-cifar100-110L-1.5

python cifar.py -a resnet --depth 56 --train-batch 256 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_3/resnet-cifar10-56L-batch-256
python cifar.py -a resnet --depth 110 --train-batch 256 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar10/part_3/resnet-cifar10-110L-batch-256
python cifar.py -a resnet --dataset cifar100 --depth 56 --train-batch 64 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_3/resnet-cifar100-56L-batch-64
python cifar.py -a resnet --dataset cifar100 --depth 110 --train-batch 64 --epochs 164 --schedule 81 122 --gamma 0.1 --wd 1e-4 --checkpoint optional_1_results/cifar100/part_3/resnet-cifar100-110L-batch-64