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
