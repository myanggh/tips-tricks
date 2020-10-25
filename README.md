# tips-tricks
use a vnc to approach a remote desktop
1. install putty
2. define and save a session: hostname, port, X11, tunnels, etc.
3. define a vncserver use the number defined in tunnels, e.g., localhost:5927
4. then you have the desktop, e.g., eraser

commonly used commands:
1. htop username, e.g., htop myang, to monitor the activities of a specific user
2. unexpectedly killed some process and can't log in vnc, try:
    $ vncserver kill :27
    $ vncserver :27
    
    or try:
    replace exec startxfce 4 by dbus-launch xfce4-session, to do so, you first get the terminal of Putty, find the xstartup file under /home/data/myang/.vnc/
    $ vim xstartup
    then comment exec /usr/bin/startxfce4 &
    and then
    uncomment #dbus-launch /usr/bin/startxfce4
    
    Boundary condition:
    Ambient layer should be symmetry
    
    Multiphase model:
    Mixture is more stable
    
# Initialization for industrial project
1 velocity direction and magnitude should be identical to the high velocity region, such as inner pipes, pumps
2 Body size should be follow the following: 20-40 layers of mesh along the height, should always define for each major bodies' size even the global size is defined.

# Fluent Eulerian + Multi-fluid VOF model
1 Use the transient model.
2 Use coupled scheme for pressure-velocity coupling
2 Select anisotropic-drag for free surface (there is higher drag in the normal direction to the interface and lower drag in the tangential direction to the interface).  
3 Volume fraction scheme choose Geo-Reconstruct for interface sharpening schemes
4 use set/model/mp-mfluid-aniso-drag text command to specify the input parameters for anisotropic drag if needed (https://ansyshelp.ansys.com/account/secured?returnurl=/Views/Secured/corp/v193/flu_ug/flu_ug_sec_use_ifm.html)

# Automation examples:
Fluent journal scripts for different type of projects
CFDpost state files
Structured slides
Python scripts for data handling (pre/post)
Geometry templates
Mesh recording
Templates in general 

Showcases:
Fluent journal: hpc, naming in meshes to make consistent cases
Mesh: Min 
Python scripts: Giacomo
CFDpost: python
Geometry: SCDM
Communication: make system bullet prrof check with sales team for tips & tricks, Doublt, communicate wisely, check list

# Learn PYTHON
#Import problem:

1 How does python find packages? https://leemendelowitz.github.io/blog/how-does-python-find-packages.html

2 Unable to import a module that is definitely installed https://stackoverflow.com/questions/14295680/unable-to-import-a-module-that-is-definitely-installed

3 Python中模块(Module)和包(Package）的区别 https://www.cnblogs.com/JetpropelledSnake/p/8905727.html

#Vertual environment
Even there is a lot of pakeages in system level python environment, the virtual enviroment is necessary for every single python project to install some specific packeages through pip command. 

1 anaconda environment
#conda method in anaconda
conda create -n kernelname python=xx.xx
activate kernelname


#check environment
import sys
print '\n'.join(sys.path)

#Installing a Python Kernel to Jupyter
pip install ipykernel
python -m ipykernel install --user -name kernelname


2 command prompt environment
Youtube channel: https://www.youtube.com/watch?v=APOPm01BVrk

#pip method in command prompt
pip list #Time 2:13
python -m venv project_env #Time 2:29
project_env\Scripts\activate.bat #Time 3:24
where python #Time 3:46
pip install requests #Time 4:48
pip install pytz #Time 5:00
pip list #Time 
pip freeze #Time 5:47
 --#Time copy information 'pip freeze'
 --#Time create requirements.txt #Time 6:37
 --#Time paste information there
deactivate #Time 7:16
rmdir project_env /s #Time 7:33

mkdir my_project #Time 8:48
python -m venv my_project\venv #Time 8:55
my_project\venv\Scripts\activate.bat
pip install -r requirements.txt #Time 9:46
cd my_project #Time 10:50
 --#Time create new file 'script.py'
deactivate #Time 
rmdir venv /s #Time
python -m venv venv --system-site-packages #Time 13:30
venv\Scripts\activate.bat #Time 
pip list #Time
pip install SQLAlchemy
pip list --local


