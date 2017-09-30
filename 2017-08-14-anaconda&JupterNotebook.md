## 安装使用  Anaconda & Jupyter Notebook 

### Question

- 如何查看自己电脑中安装了哪些版本的 Python ？
    - `$ pyenv versions`
- 如何切换、运行不同版本的 Python 呢？
    - 使用版本与包管理工具如 Anaconda,pyenv等来进行管理
        - `$ pyenv local <version>`
        - `$ source activate ~/py27 `
- Python2 和 Python3 对应的开源包、软件包是否可以通用？
    - *不能,下载的开源宝和软件包下载在对应语言文件目录下*
- Anconda 是什么?
    - 包管理
    - 不同版本python环境管理
- Jupyter Notebook是什么?
    - 可运行、可交互的在线工具，可把代码和笔记舒爽地呈现在同一个页面，并导出为 .ipynb .md .py 等格式.借助 nbviewer社会化分享
   

### Action

#### 1. 寻找Anaconda官方文档

- [Installing on macOS | Continuum Analytics: Documentation](https://docs.continuum.io/anaconda/install/mac-os)

#### 2. 安装 Anaconda3

- 两种安装方式:`图形界面安装`与`命令行界面安装`
- 两种版本 `PY2.7` 与 `py3.6`(根据默认环境选择)
- 选择 `命令行界面安装`,`py3.6`版本
   - 01:下载命令行版安装包[macOS installer](https://www.continuum.io/downloads#macos) 
   - 02:[可选]  cryptographic hash verification(哈希值验证)
       -  到达安装包所在文件夹
           -  `$ cd ~/Downloads`
       -  验证安装包的哈希值
           -  下载包的哈希值
    
                   $ md5 Anaconda3-4.4.0-MacOSX-x86_64.sh 
                   
                   MD5 (Anaconda3-4.4.0-MacOSX-x86_64.sh) = 3958ac6cb84731e560dd833256aa5b15
        
               
           - 对比官方文档给出的[哈希值](https://docs.continuum.io/anaconda/install/hashes/Anaconda3-4.4.0-MacOSX-x86_64.sh-hash),一致即可,否则联系官方或者换一个安装包
   - 03:安装到 py3.6
       - `bash ~/Downloads/Anaconda3-4.4.0-MacOSX-x86_64.sh`
   - 04:跟随命令行提示操作
       - 确认 license 内容, yes
       - 确认安装路径,enter
       - 开始安装,需要等待一段时间
       - 出现`Thank you for installing Anaconda3!`即安装成功
   - 05:用命令行运行 `conda`
       - 在命令行中输入
       - `$ export PATH=~/anaconda3/bin:$PATH`
           - Note: 根据下载版本不同路径不同,参考[这里](https://stackoverflow.com/questions/18675907/how-to-run-conda)
       - 为了避免每次重启 shell 都要输入一次 `$ export PATH=~/anaconda3/bin:$PATH`
           - 在 shell 的配置文件中输入该命令
           - 不同 shell 配置文件名称不同
           - zsh 的配置文件为 `.zshrc` 
           - 打开 `.zshrc `

                       $ cd ~ 
                       $ vim .zshrc
           - `i `插入模式下输入 `export PATH=~/anaconda3/bin:$PATH`
           - 重启 shell 即可

   - 06:验证是否安装成功
       
       ```
       $ conda --version
       conda 4.3.21
       ```

#### 3. 使用 Anaconda3

- [Getting started](https://docs.continuum.io/anaconda/user-guide/getting-started)
    
> If you prefer to use a terminal window or command prompt, download the [conda cheat sheet](http://conda.pydata.org/docs/using/cheatsheet.html) , try the [conda test drive](http://conda.pydata.org/docs/test-drive.html) and learn more about [using conda](http://conda.pydata.org/docs/using).
   
- 管理 conda

   ```zsh
   $ conda info             # 显示Anaconda的安装信息
   $ conda list             # 现有环境下的包列表
   $ conda update conda     # 更新 conda
   $ conda update anaconda  # 更新当前环境下所有包(anaconda 上有的)
   ```
   
- 管理 python 版本
   
   ```zsh
    # 创建新的环境
    $ conda create --prefix ~/py27 python=2.7
    # 删除创建的环境
    $ conda remove --prefix ~/py27 --all
    or
    $ rm -rf ~/py27
    
    # 激活某个环境
    $ source activate ~/py27
    # 退出激活的环境
    $ source deactivate ~/py27
   ```
- 管理 packages

   ```
   $ conda search jupyter    # 查找包(jupyter)
   $ conda install jupyter   # 安装包(jupyter)
   $ jupyter-notebook        # 运行安装的包(jupyter)
   
   # 在特定环境下安装/卸载包
   $ conda install --prefix ~/py27 <packagename> <packagename>
   $ conda remove --prefix ~/py27 <packagename> <packagename>
   
   ```

#### 4. 使用 Jupyter Notebook

- Anaconda3 自带 Jupyter Notebook
- 运行 JN, 会自动读取当前文件目录
- 操作

    ```
    $ jupyter-notebook # 运行
    control + C        # 完全退出
    ```

- 快捷键(updating)
    - cmd 模式
    - 编辑 模式
        - Basic navigation: `enter, shift-enter, up/k, down/j`
        - Saving the notebook: `s`
        - Change Cell types: `y, m, 1-6, t`
        - Cell creation: `a, b`
        - Cell editing: `x, c, v, d, z`
        - Kernel operations: `i, 0 (press twice)`
- 社会化分享
    - [nbviewer](https://github.com/jupyter/nbviewer)


### Error

#### E1: Anaconda3 下载成功后,无法在 cmd 中打开

- 1.0 错误信息
    - `zsh: command not found: conda`
    - `bash: command not found: conda`
- 1.1 分析
    - 应该是shell配置哪里没有到位
- 1.2 搜索
    - 1.2.0 关键词: `bash: command not found: conda`
    - 1.2.1 方案01
        - [python - How to run Conda? - Stack Overflow](https://stackoverflow.com/questions/18675907/how-to-run-conda)
        - 输入 `$ export PATH=~/anaconda3/bin:$PATH`
        - 验证 `conda --version`
        - 成功 `conda 4.3.21`

### E2: JPnote md 文件渲染的问题

- 2.0 问题描述
    - 用 jupyter-notebook 打开 `.md ` 文件是乱码的html
- 2.1 搜索:` jupyter notebook md messy code`
    - [Render .md files in Jupyter](https://github.com/jupyter/notebook/issues/2485#issuecomment-305657196)
- 2.3 方案1:[JupyterLab ](https://github.com/jupyterlab/jupyterlab)  (2000+ stars)
    -  2.3.0 这是 Jupyter 的可扩展计算环境
    -  2.3.1 安装 
        - ` conda install -c conda-forge jupyterlab`
        - 网络不好,总是 `read time out`
        - 先放着,时不时试一下
        - {12min}
        - 下午下载完成
    -  2.3.2 运行`jupyter lab` 
        - 成功安装,但发现自己 `犯傻 x 1`
            - W1: 概念错误:jupyterlab 是个集成的电脑环境,和 jupyter-notebook 是两套东西,要解决原来的问题应该寻找类似插件一样的东西
- 2.4 方案2: JupyterNotebook 的插件
    - [jupyter_contrib_nbextensions](https://github.com/ipython-contrib/jupyter_contrib_nbextensions/)
        - 2.4.0 注意 jupyter 版本不同对应的分支不同
        - 2.4.1 安装 Python 包
            - 01 `$ conda config --add channels conda-forge`
            - 02 `$ conda install jupyter_contrib_nbextensions` 
                - 网络不好会提示连接超时,多试几次
        - 2.4.2 激活 Nbextensions
            - [2种激活方式](https://github.com/ipython-contrib/jupyter_contrib_nbextensions/#3-enablingdisabling-extensions),选择第二种:
            - 重新运行 `jupyter-notebook`,点击多的标签:
                - Files | Running | Clusters |`Nbextensions` 
            - 点选自己需要的功能,比如生产目录等,点击某个功能,页面下方会出现详细说明
        - W2:插件效果还是针对 `.ipynb` 类型的文件,对`.md`依然是乱码打开
- 2.5 执念: jupyter-notebook 这种级别的工具没道理无法正常打开md文件,在邮件列表中都有展示
    - [How to link and render a markdown file readme.md from a notebook MyNotebook.ipynb? - Google 网上论坛](https://groups.google.com/forum/#!topic/jupyter/uOe3PyxbcqU)
    - 最新的讨论在[这里](https://github.com/jupyter/notebook/issues/2485)
        - 项目贡献值者 [juhasch](https://github.com/jupyter/notebook/issues/2485#issuecomment-317170034)说确实没有简单地办法来实现这一问题,以后可能会写个插件来实现
        - 项目所有者 [takluyver](https://github.com/jupyter/notebook/issues/2485#issuecomment-323132509)说暂时还没有想好如何将这个功能添加到程序中
- 2.6 方案3:放弃用 jupyter-notebook 打开`.md` 文件 
    - 只用jupyter-notebook 编辑 `.ipynb` 文件,记录周任务探索过程
    - readme.md 用sublime 文本编辑器编辑


### Reference

- [The Jupyter Notebook — Jupyter Notebook 5.1.0rc2 documentation](http://jupyter-notebook.readthedocs.io/en/latest/notebook.html)
- [Jupyter Notebook Viewer](http://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)
- [jupyter_contrib_nbextensions](https://github.com/ipython-contrib/jupyter_contrib_nbextensions/)
* [ipython-contrib/jupyter\_contrib\_nbextensions: A collection of various notebook extensions for Jupyter](https://github.com/ipython-contrib/jupyter_contrib_nbextensions/)
* [Jupyter-contrib/jupyter\_nbextensions\_configurator: A jupyter notebook serverextension providing config interfaces for nbextensions.](https://github.com/Jupyter-contrib/jupyter_nbextensions_configurator)
* [conda-forge/jupyter\_contrib\_nbextensions-feedstock: A conda-smithy repository for jupyter\_contrib\_nbextensions.](https://github.com/conda-forge/jupyter_contrib_nbextensions-feedstock)

### Timelog

- 170813 2h    chrome 下载失败2次,未断点续下,改用迅雷下载
- 170814 1h    安装 Anaconda3 &  解决 E1
- 170814 1h    试验并撰写 anaconda 使用教程/命令表
- 170814 30m   Jupter Notebook 尝试
- 170817 30m   Jupter Notebook md 渲染问题
- 170818 14m   jupyter_contrib_nbextensions 安装,等待时间稍长,暂时搁置 
- 170818 45m   jupyter_contrib_nbextensions 安装配置,未解决问题,放弃.


