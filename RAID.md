[[NAS]]
for redundancy 
performance
RAID 0 : stripe | parallel | performance | no redundancy
RAID 1 : mirror | redundancy | no stripe thus no performance 
RAID 5 : stipe | - 1 HD | performance 
RAID 6 : stipe | - 2 HD | performance x2 - x8 | 4 - 10
RAID 10 : stipe | mirror | 50% capacity| redundancy | 2x performance | min 4 HD

## Thick vs Thin volume
- Thin volume
	- consume as data come 
	- format on the go
- Thick volume
	- fixed size
	- advance format

## Storage Protocol
- block : controlled by OS | RDBMS
	- like an local disk
	- network interface and register as host 
- file or share : controlled by Qnap Turbo Storage (QTS ) | media
	- NFS: linux
	- Sift: windows

### 2 pools from 100%
- 50% for share
- 50% for black | Thick or Thin