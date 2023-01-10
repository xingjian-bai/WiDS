## 前置软件
1. [安装conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html)


## 在本机建立代码库
1. [在终端中新建一个文件夹，并打开](https://blog.csdn.net/biggercoffee/article/details/50752910)
2. 向下同步git代码库。在终端运行`git clone https://github.com/xingjian-bai/WiDS`
   - 第一次用git指令的时候，需要在终端上配置自己的github账号。[详细教程1](https://www.cnblogs.com/suihung/p/16087899.html), [详细教程2](https://tonyscript.github.io/2017/12/17/2017-12-17-Using-GitHub-In-Terminal/)
3. 同步conda环境`conda env create -f environment.yml`
    - environment.yml是对python环境的描述文件。
4. 激活conda环境`conda activate wids`
5. 测试任务：在代码库里新建一个文档，写几句简单的python代码，然后用wids环境编译它。
   - 可以用vscode做，也可以在终端做。
6. 向上同步git代码库。运行
   1. `git add .` 增添所有修改
   2. `git commit -m "some message"`
   3. `git push`
   4. 遇到问题输出，就google

