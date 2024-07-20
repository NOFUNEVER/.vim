# .vim
vimrc and plugins

Installation:
    
 CLONE REPO:   
    git clone https://github.com/NOFUNEVER/.vim.git

Create symlinks:

    ln -s ~/.vim/vimrc ~/.vimrc
    ln -s ~/.vim/gvimrc ~/.gvimrc
    
   If Fails:
        
        rm ~/.vimrc
        and try again
    
Switch to the `~/.vim` directory, and fetch submodules:

    cd ~/.vim


    sudo git submodule update --init --recursive
    git submodule foreach --recursive git submodule update --init

Remember YCM-Generator may need to be deleted to complete this :(

    delete relevant section from .gitmodules file
    git add .gitmodules
    delete from .git/config
    git rm--cached path/to/submodule
    rm -rf .git/modules/path/to/submodule
    git commit -m "removed a module"
    delete local folder
    rm -rf path/to/submodule. 	 


To add new plugins:

    cd ~/dotfiles
    git submodule init
    git submodule add https://github.com/vim-airline/vim-airline.git vim/pack/shapeshed/start/vim-airline
    git add .gitmodules vim/pack/shapeshed/start/vim-airline
    git commit
    
To update packages is also just a case of updating git submodules. try

    sudo git submodule update --init --recursive
    git submodule foreach --recursive git submodule update --init
  or
    git submodule update --remote --merge
    git commit
Removing a package

Removing a package is just a case of removing the git submodule.

    git submodule deinit vim/pack/shapeshed/start/vim-airline
    git rm vim/pack/shapeshed/start/vim-airline
    rm -Rf .git/modules/vim/pack/shapeshed/start/vim-airline
    git commit

To update an individual plugin enter the root folder of the plugin and:
    
    git pull origin master

Upgrading all bundled plugins:
       
    git submodule foreach git pull origin master
     
 

   
Remember YCM-Generator must but just cloned no submodule.
YCM NEEDS BINARIES COMPILED:
    
   
    sudo git submodule update --init --recursive
  

Compiling YCM with semantic support for C-family languages:

    cd ~/.vim/pack/jkl-plugins/start/YouCompleteMe
    sudo ./install.py --clang-completer
 
      
    
-----------------------------------------------------------------------------------------------------------
PER PROJECT REQUIREMENTS
sudop    
    
To make make YCM see entire project:

    Run ./config_gen.py PROJECT_DIRECTORY, where PROJECT_DIRECTORY is the root directory of your project's build system (i.e. the one       containing the root Makefile, etc.)
    You can also invoke it from within Vim using the :YcmGenerateConfig or :CCGenerateConfig
    
To make clang-format work in your project:
    
    clang-format -style=google -dump-config > .clang-format

