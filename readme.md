## Pre-requisite
1. [Install conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html)


## Build codebase locally
1. [Add a folder using the terminal, and open it](https://blog.csdn.net/biggercoffee/article/details/50752910)
2. `git clone https://github.com/xingjian-bai/WiDS`
   - Setting up Github account on terminal [tutorial 1](https://www.cnblogs.com/suihung/p/16087899.html), [tutorial 2](https://tonyscript.github.io/2017/12/17/2017-12-17-Using-GitHub-In-Terminal/)
3. `conda env create -f environment.yml`
    - environment.yml is the description file of the env。
4. `conda activate wids`
5. Pushing the repo.
   1. `git add .` 
   2. `git commit -m "some message"`
   3. `git push`

## Download data
- Download file from Kaggle, and put it into the root directory