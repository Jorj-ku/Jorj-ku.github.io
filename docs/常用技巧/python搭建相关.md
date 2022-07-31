# 目录
[TOC]


# 1. pip 安装指定  国内源镜像
pip install -i 国内镜像地址 包名

例如： `pip install -i  https://mirrors.aliyun.com/pypi/simple/   numpy`

  常用的  包名:    matplotlib   torch    numpy  Pandas
- [Pandas 中文 (pypandas.cn)](https://www.pypandas.cn/)      
- [NumPy 中文](https://www.numpy.org.cn/)     
- [torch - PyTorch中文文档 ](https://pytorch-cn.readthedocs.io/zh/latest/package_references/torch/)    
- [Matplotlib 中文](https://www.matplotlib.org.cn/)

国内常用源镜像地址：

- 清华：https://pypi.tuna.tsinghua.edu.cn/simple
- 阿里云：http://mirrors.aliyun.com/pypi/simple/
- 中国科技大学:  https://pypi.mirrors.ustc.edu.cn/simple/
- 华中理工大学：http://pypi.hustunique.com/
- 山东理工大学：http://pypi.sdutlinux.org/ 
- 豆瓣：http://pypi.douban.com/simple/

# 2. Anaconda使用相关
## 2.1 Conda常用命令合集
### 1. 获取版本号/帮助

| 功能 | 命令 |
| :------------- | :----------: |
|获取版本号 |  `conda -V,   conda --version` |
| 获取帮助	    |   `conda -h,  conda --help`
|  获取环境相关命令的帮助	    |       `conda env -h`

>（所有 --单词 都可以用 -单词首字母来代替	比如 -version 可以用 -V来代替，只不过有的是大写，有的可能是小写）



### 2. 环境相关

| 功能 | 命令 |
| :------------- | :----------: |
|创建环境	                   |         `conda create -n environment_name`
|进入环境	                    |  `conda activate environment_name`
|退出环境	                     | `conda deactivate`
|删除环境	                    |  `conda remove -n yourname --all`
|列出环境	                    |  `conda env list / conda info -e`
|复制环境	                    |  `conda create --name new_env_name --clone old_env_name`
|指定目录下生成环境yml文件	        |    `conda env export > 目录/environment.yml`
|从yml文件创建环境	            |  `conda env create -n env_name -f environment.yml`
>创建指定python版本下包含某些包的环境	conda create -n environment_name python=3.7 numpy scipy

### 3. 管理包
对包的管理是在某个环境下进行的，先进入特定环境再进行包的操作比较好，不会出现把本该安装在A环境中的包安装在了B环境中这种情况。

| 功能 | 命令 |
| :------------- | :----------: |
|	安装包	                            |    `conda instal package_name`
|	查看当前环境包列表	     |               `conda list`
|	查看指定环境包列表	      |              `conda list -n environment_name`
|	查看conda源中包的信息	   |             `conda search package_name`
|	更新包	                               | `conda update package_name`
|	删除包	                                |`conda remove package_name`
|	清理无用的安装包	             |       `conda clean -p`
|	清理tar包	                            |`conda clean -t`
|	清理所有安装包及cache	     |           `conda clean -y --all`
|	更新anaconda	                      |  `conda update annaconda`

>最后三个清理命令类似于清理手机上的安装包、缓存，不会删除某个库，只是删除已经安装完成的那些安装包。

## 2.2 更换conda源
 1.  更换清华源
windows:
命令行中直接使用以下命令
 `conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/`
 `conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge `
 `conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/`
 设置搜索时显示通道地址
 `conda config --set show_channel_urls yes`

 2. 更换中科大源
`conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/main/`
`conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/`
 `conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/conda-forge/`
 `conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/msys2/`
 `conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/bioconda/`
 `conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/menpo/`
设置搜索时显示通道地址 
`conda config --set show_channel_urls yes`

3. 显示现有安装源
`conda config --show channels`

4. 恢复默认源
`conda config --remove-key channels`

5. 移除某个源
`conda config --remove channels https://mirrors.cloud.tencent.com/anaconda/pkgs/pro/`

# 3. vscode 使用python
 
运行环境查看与配置 :
1. 在vs code选择，查看-》命令面板来打开命令面板或者使用快捷键【ctrl+shift+p】
2. 再选择   "Python :Select Interpreter"   来选择运行环境


# 4. jupyter notebook

1. 安装Jupyter Notebook

 `pip install -i  https://mirrors.aliyun.com/pypi/simple/   jupyter`

2. 默认端口启动
	在终端中输入以下命令： `jupyter notebook`
		   
	执行命令之后，在终端中将会显示一系列notebook的服务器信息，同时浏览器将会自动启动Jupyter Notebook。

3. jupyter notebook特点
  
   允许把代码写入独立的cell中，然后单独执行。用户可以在测试项目时单独测试特定代码块，无需从头开始执行代码   
   
   基于web框架进行交互开发，非常方便
