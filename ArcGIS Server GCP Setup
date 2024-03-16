1) Create project in GCP console - Project list (top) > new project. Name it.
2) Enable Compute Engine API from console (if needed) - APIs and Services (left) > Enabled APIs and services
2.1) Note Compute Engine Console accessible from left menu
3) Create new virtual machine - Compute Engine > VM Instances > Create instance (top)
3.1) Configure VM:
  Name (used arcgisserver-geom99)
  Set server region and zone (left defaults of us-central1 and us-central1-a)
  Allocate CPU and RAM (left default of e2-medium for this project, but allocate enough for ArcGIS Server recommended requirements in real world uses)
  Set boot disk (Debian default, used Shawn's custom image in this case)
    To set custom boot disk, Change > Custom Images > Change (next to "source project for images") > All > Shawn's ArcGIS Server. Select most recent image in image dropdown. Shawn's custom settings: Balanced persistent disk, 50gb
  Open firewall to HTTP and HTTPS traffic (check boxes)
  Click create - machine takes several minutes to be created
4) Set Windows password - Compute Engine > VM Instances > arrow next to "RDP" > Set Windows password. Enter username ("student" in this case). After hitting "set", Windows password will be displayed
  <b>Write this down! This is the only time it is displayed!</b> To reset, just re-run process again.
5) Alter VM firewall rules:
  Fleming IT blocks default remote desktop port (3389), so configure VM to accept traffic from 444. Possibly not required in real world environment.
    From VM instances, click "set up firewall rules" > "create firewall rule" (top)
    Set rule name (flemingrdp444)
    Targets > "All instances in the network" (applies rule to all VMs)
    Set source filter to IPv4 ranges, then enter IP addresses that can connect to the VM
      Fleming on-campus: 142.237.0.0/16
      Anywhere else: use personal IP or 0.0.0.0/0 for no restrictions at all (possible security risk)
    Protocols and ports > check TCP > enter 444 as port
    Create rule
  Allow ArcGIS server management ports (6443, 6080)
    From VM instances, click "set up firewall rules" > "create firewall rule" (top)
    Set rule name (arcgisserveradmin)
    Targets > "All instances in the network" (applies rule to all VMs)
    Set source filter to IPv4 ranges, then enter IP addresses that can connect to the VM
      Fleming on-campus: 142.237.0.0/16
      Anywhere else: use personal IP or 0.0.0.0/0 for no restrictions at all (possible security risk)
    Protocols and ports > check TCP > enter 6443,6080 as ports
    Create rule
6) Remote desktop into VM
  Open remote desktop connection program and paste in VM's external IP (located in VM instances under Compute Engine console). Add :444 to prevent use of default 3389 port, which is blocked at Fleming.
  Enter username and password for Windows machine (select "more choices > use a differnet account" if needed)
  Connect despite certificate error
7) Set Windows Firewall rule to allow ArcGIS Server management ports
  Start menu on remote desktop > Windows Defender Firewall with Advanced Security
  Inbound rules > new rule (on right)
  Select port, then TCP and apply rule to ports 6443 and 6080
  Allow the connection, apply rule for domain, private, and public
  Name ArcGIS Server Admin Ports > finish
8) Test REST Services directory - enter https://[vm external ip]/arcgis/rest/services. Bypass security warning (under advanced or "thisisunsafe")
9) Shut down server - Either use start menu in remote desktop or select "stop" in dot menu next to VM in GCP console. Same menu can be used to turn on server.
