## Installing Python

You can install Python in different ways. Since I am using Mac, I explored only installing in Mac. Few options I had heard about was 'pip' and 'virtualenv'. Both are used for different purposes. 

virtualenv can help you maintain isolated python installations. For eg: for your work you can an official version of python and packages while for some exploration you can keep a different python version and related packages using virtualenv. 

pip is used to install specific packages. Its similar to rpm in linux. 
### Issues
#### pip not able to download via CORP firewall
If you are like me and sitting behind a corporate firewall and cannot access an python outside repository and received an invalid certifcate error, you might want to add most common python repositories to the trusted host list in pip.conf or on command line. 
                                            
### What I did
#### virtualenv
I seemed to have a virtualenv installed earlier itself. I reused that. 
#### pip 
my pip.conf looks like this 

    cat $HOME/.config/pip/pip.conf
  
    [global]
    trusted-host = pypi.python.org
                   pypi.org
                   files.pythonhosted.org
               

#### packages for parquet               
Using pip I installed pandas etc. 

    python -m pip install numpy
    python -m pip install pandas
    python -m pip install pyarrow
 
## How to know current site-packages 
site-packages directory is where python modules gets installed. Though you can know the version of a given python using other commands, you can easily browse different packages, their source code if you know the site packages directory. 

    #Get System level site packages directory
    python -m site

    #Get User level site packages directory
    python -m site --user-site
    
    #Another option
    python3 -c 'import sysconfig; print(sysconfig.get_paths()["purelib"])'


## List all installed packages
    
    pip list

## Access python3
Since python has moved onto python3 and it is available only as python3, it may be handy to create an alias like this. 
It can be added in ~/.bash_profile

    alias python="python3"
