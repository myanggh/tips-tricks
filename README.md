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

 