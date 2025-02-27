# Introduction
Here, we proposed GraphEC, a geometric graph learning-based EC number predictor established on the active sites and predicted structures. Specifically, the enzyme active sites were first identified because of their critical role in enzyme function. Guided by the active sites, GraphEC was trained using the geometric graph learning with the ESMFold-predicted protein structures. To augment the features, informative sequence embeddings were generated using a pre-trained language model (ProtTrans). Finally, a label diffusion algorithm was utilized to further improve the prediction by incorporating homology information. Additionally, the optimum pH of enzymes was predicted to reflect the enzyme-catalyzed reactions. 
![figure1](https://github.com/YidongSong/GraphEC/assets/42714970/a4bbacbe-72d3-4884-9d94-7924f63a8aea)

# System requirement
GraphEC is developed under Linux environment with:
Python 3.8.16, numpy v1.24.3, pyg v2.3.0, pytorch v1.13.1, biopython v1.81, debugpy v1.6.7, decorator v5.1.1, filelock, v3.12.1, gmp v6.2.1, idna v3.4, ipython v8.12.0, openfold v1.0.1, scipy 1.10.1, and six v1.16.0

# Install and run the program
**1.** Clone this repository by `git clone https://github.com/YidongSong/GraphEC.git`. 
      
**2.** Install the packages required by GraphEC. The [ESMFold](https://github.com/facebookresearch/esm) and [ProtTrans](https://github.com/agemagician/ProtTrans) can be installed, followed by their official tutorials. The pre-trained ProtT5-XL-UniRef50 model can be downloaded [here](https://zenodo.org/record/4644188) .   
      
**3.** Run GraphEC with the following command:    
      
```
bash run.sh --task EC_number --fasta ./Data/fasta/EC_number.fasta --gpu 0
```
where ```--task``` represents the prediction task; ```--fasta``` represents the data needed to be predicted in fasta format; and ```--gpu``` represents the GPU used to complete the prediction.   
      
The results can be found in ```./EC_number/results```, including the full predictions and top K predictive scores (K is defaulted to 5).   

**4.** Run GraphEC-AS by the following command:

```
bash run.sh --task ActiveSite --fasta ./Data/fasta/Active_sites.fasta --gpu 0
```

The results are saved in ```./Optimum_pH/results```

**5.** Run GraphEC-pH by the following command:

```
bash run.sh --task Optimum_pH --fasta ./Data/fasta/optimum_pH.fasta --gpu 0
```

      
# Dataset and model   
**1.** EC number prediction    
The training set is provided in ```./EC_number/data/datasets/Training_set.csv```, with the two independent tests located in ```./EC_number/data/datasets/NEW-392.csv``` and ```./EC_number/data/datasets/Price-149.csv```   
The trained models are saved in ```./EC_number/model```     
       
**2.** Active site prediction   
The training set is saved in ```./Active_sites/data/datasets/train.pkl```, and the test set is saved in ```./Active_sites/data/datasets/test.pkl```    
The trained models can be found in  ```./Active_sites/model```

**3.** Optimum pH prediction   
The training set can be found in ```./Optimum_pH/data/datasets/train.pkl```, and the test set can be found in ```./Optimum_pH/data/datasets/test.pkl```     
The trained models are saved in ```./Optimum_pH/model```     

# Citation and contact
Citation: preparing

Contact: 
Yidong Song (songyd6@mail2.sysu.edu.cn)  
Yuedong Yang (yangyd25@mail.sysu.edu.cn)






