## Installing Python

You can install Python in different ways. Since I am using Mac, I explored only installing in Mac. Few options I had heard about was 'pip' and 'virtualenv'. Both are used for different purposes. 

virtualenv can help you maintain isolated python installations. For eg: for your work you can an official version of python and packages while for some exploration you can keep a different python version and related packages using virtualenv. 

pip is used to install specific packages. Its similar to rpm in linux. 

## pip not able to download via CORP firewall
If you are like me and sitting behind a corporate firewall and cannot access an python outside repository and received an invalid certifcate error, you might want to add most common python repositories to the trusted host list in pip.conf or on command line. 
                                            
## What I did
### virtualenv
I seemed to have a virtualenv installed earlier itself. I reused that. 
### pip 
my pip.conf looks like this 

    cat $HOME/.config/pip/pip.conf
  
    [global]
    trusted-host = pypi.python.org
                   pypi.org
                   files.pythonhosted.org
               

### packages for parquet               
Using pip I installed pandas etc. 

    python -m pip install numpy
    python -m pip install pandas
    python -m pip install pyarrow
    

