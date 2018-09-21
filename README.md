# pytorch-installation
Installing pytorch on a remote machine + all dependencies and useful libraries 

Assuming you have python3.6 or higher already. 

### Anaconda 

First get Anaconda from [here](https://www.anaconda.com/download/#linux). 
Then run 
``` 
sh Anaconda3-5.2.0-Linux-x86_64.sh 
```

and follow the prompts. The defaults are generally good.


To install python 

```
conda create --name py36 python=3.6
```

Otherwise create a virtual environment for pytorch 

```
conda create --name pytorch 
```
To activate this environment, use:

 ```
source activate pytorch
```

To deactivate an active environment, use:
 ```
 source deactivate
 ```
 
 ### Pytorch
 Now install pytorch in this environment. First activate your environment. Then run (for cuda 9) 
 
 ```
 conda install pytorch torchvision -c pytorch
 ``` 
 Change this based on the cuda version you have, using the command from the [pytorch page](https://pytorch.org/get-started/locally/#anaconda)
 
