---
title: 
tags:
---
Volume (managed by docker):
- Anonymous Volume
	- automatically created by docker when specify VOLUME ["/path/to/folder"] or -v s</path/to/folder> 
	- remove when the container is stopped
	- great for temp data and outsource the data storage to the host file system to increase performance
- Named Volume
	- specify -v <volume_name>:</path/to/folder> 
	- the volume persist after the container is stopped 
	- great for data which should be persistent but which you don't need to edit directly
	- can be shared to/ re-used by multiple containers
- Bind Mounts (managed by you) 
	- share your file/ folder in the local system to the containers
	- great for editable data, allows for instant updates without restarting the container
	- specify -v <abs/path/to/local/folder>:</path/to/folder> 
	- NOT USED FOR PRODUCTION
	- can be shared to/ re-used by multiple containers