# yyuu/pyenv

- 支持你任性的使用指定版本的 Python 环境


## 安装
 
>You can also install pyenv using the Homebrew package manager for Mac OS X.

    $ brew update
    $ brew install pyenv

## 使用

>Some useful pyenv commands are:

   commands  |  List all available pyenv commands 
   ----------|----------------------------------------------------------------
   local     | Set or show the local application-specific Python version
   global    |  Set or show the global Python version
   shell     |  Set or show the shell-specific Python version
   install   |  Install a Python version using python-build
   uninstall |  Uninstall a specific Python version
   rehash    |  Rehash pyenv shims (run this after installing executables)
   version   |  Show the current Python version and its origin
   versions  |  List all Python versions available to pyenv
   which     |  Display the full path to an executable ［执行文件］
   whence    |  List all Python versions that contain the given executable

- 安装执行后要 rehash 一下(重置)
- `pyenv [commands]`

## mac 版本切换

- 查询当前pyenv可用的所有python版本
    - `pyenv versions`
- 查询当前 pyenv 版本
    -` pyenv -v`


