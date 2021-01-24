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
    
# Bubble column
1 inlet turbulence matters when the inlet velocity is low or the area is large. But it is not the decisive factor. Pay a bit attention to it and comply the ansys help wrt the boundary condition.
2 Use very fine mesh seems to give a very stable solution for two D problem. When the y+ is about 1, The k-e, k-w and RSM model all generate the similar results. But fine mesh seems not work for 3D problem to generate stable solution.
3 For 3D problem, use transient to start the simulation, and switch to steady state when the bubble emerges (sometimes when the air flowrate is very low, it may take hundred iterations). Normally, you will get a stable solution if the wall function is correctly considered, and most of the time, if a coarse mesh is used. But if the steady state simulation didn't give a stable solution, then switch to transient again after a psuedo steady state reached. But this is tricky because almost the flow didn't change after switch back to transient again for any cases.
    
# Initialization for industrial project
1 velocity direction and magnitude should be identical to the high velocity region, such as inner pipes, pumps
2 Body size should be follow the following: 20-40 layers of mesh along the height, should always define for each major bodies' size even the global size is defined.

# Initialization methods
1 define a proper inlet turbulent parameter (k, e is the most appropriate inlet boundary). Set a higher Turbulent Viscosity Ratio (can be 10-100 for internal flow) at the inlet boundary, the smaller the specific dissipation rate at initialization console will appear while the Turbulent Kinetic Energy will remain the same. On the other hand, Turbulent Intensity (5% is normally suitable) at the inlet is positively correlated to both the Turbulent Kinetic Energy and specific dissipation rate at initialization console.  

2 initial start from the inlet, give a run. And see what happens. If the residuel stay high and steady, you can change the initial turbulent values, and give another run.

3 If the step 2 didn't work, switch to transient simulation, and wait until the residuel decrease and keep steady.

4 Mesh: Polyhedral mesh is less stable than hex mesh; inlet flow direction need not spacial refinement especially the inlet flowrate is small, but a inflation may be good for tex mesh cases.

# Wall treatment and wall functions



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
deactivate

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

3 New knowledge
(1) There are three types of variables commonly used: string, number, and boolean variable True/False.

(2) String is awesome. Pay attaition to string_name.index("a"), string_name.replace("a","b"), and string_name[0]. The first gives the index number of the a in the string, the second replaces a with b, the third the latter gives the first letter of the string.

(3) Numbers is awesome. Use from math import * to get access to mathmatic functions such as sqrt, floor, sin.

(4) Variables type is defined using int(a), float(b), double(c)...

(5) Use Input("user information") to input user information.

(6) Build a calculator. A calculator normally is the main part of a function.

(7) Mad lib game.

(8) List and list functions， List_name[]. List_name.append(), List_name.remove(), List_name.extend(), List_name.append(), List_name.count(), List_name.sort(), List_name.reverse(), List_name.copy()

(9) Tuples, tuple_name(). Tuple is inmutable, it can't be changed. It is usually used to list that don't need to be changed.

(10) Function, def (parameters).

(11) If statement, if condition:. The content followed by the If statement should have indentation. The line without indentation will be regarded as out of the function.
 
(12) Function + if statement to build a smarter calculator. The user input the number and operator, the function to calculate the formula.

(13) Dictionary is awesome to assign parameters.

(14) While loop. Build a guessing game.

(15) For loop is awesome. Loop over different arrays, numbers. Build a exponent function.

(16) 2D lists & nested loops. you can name the variables in the for loop.

(17) Inherentance. 

(18) Python interpretor. It used to quick test a few script instead of using a text editor.

(17) Build a translator. while loop + for loop. Understand the variables in the for loop and while loop. .lower, .isupper are given by Python. 

(18) Read and write files.

(19) Module and pip.

(20) Class and objects is super useful, class is a data type that used in almost every language. Object is the name of the data type. Creat your own data type.

(21) Create a quiz game. class + loop functions.

(22) Object function.
