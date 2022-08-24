hostname R1

no ip domain-lookup

service password-encryption

banner motd #
unauthorized login prohibited #




enable password class

line console 0
password cisco
login


line vty 0 4
password cisco 
login


line console 0 
logging synchronous
exec-timeout 0 0

########################


interface s0/0/0
ip address 10.0.0.1 255.255.255.252
no shutdown


#########################

int loopback number
ip address 192.168.x.x 255.255.255.x
no shutdown


#########################

interface range fa0/3-24
shutdown


#########################

interface s0/0/0
ip address 10.0.0.1 255.255.255.252

#########################

int vlan 1 
ip adress 192.168.x.x
no shutdown 
#######################
ip defalut-gateway 192.168.x.x

###########################


vlan 10
name ____

interface f0/2 
switchport mode access
switchport access vlan number


int vlan 1 192.168.1.1 255.255.255.0

####################################################################


router ospf 1
network 192.168.1.0 0.0.0.255 area 0 

auto-cost reference-bandwidth 1000



interface s0/0/0
bandwidth 128
ip ospf cost 7500
ip ospf hello-interval 15
ip ospf dead-interval 60


###################################################################


service dhcp 
ip dhcp excluded-address 192.168.2.1 192.168.2.99
ip dhcp pool pool1
network 192.168.x.x 255.255.255.x
default-router 192.168.x.x


###################################################################

int g0/0
ip nat insid
ip nat inside 
exit
int s0/0/0
ip nat outside
exit 
ip nat inside source static (local-device-ip) 10.0.0.x

######################################################################
int tunnel 0 
tunnel mode gre ip 
ip address 192.168.15.1 255.255.255.0
no shut
tunnel source g0/0
tunnel destination 192.168.1.1

#######################################################################

$$$$$$$$$$$$$$$$$$$$$$$$$$$
show ip interface brief

show vlan

Show ip route 

Show ip eigrp/ospf neighbor

Show IP EIGRP TOPOLOGY 

show controllers serial 0

show ip nat tr
$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$







	1. Interface se -/- (ent) , clock rate 64000
	2. Disable dns lookup : no ip domain-lookup
	3. Change device name: hostname
	4. Encrypt plain text passwords:  service password-encryption
	5. MOTD banner: banner motd # 
	6. EXEC mode passwords: enable password secret321
	7. Consle password: line con 0 , password secret , login , end.
	8. Vty password: line vty 0 , password secret , login , end .
	9. Loopback:  int loopback name , ip address ip mask 
	
	10. Vlan 1 ip address : int vlan 1 (ent), ip adress ip mask (ent) , no shutdown 
	11. Default gateway in switch: ip defalut-gateway ip address
	
	12. Pagp: int range fast 0/nr-nr (ent) ,  swittchport mode trunk (ent) , channel-protocol pagp (ent) , channel-group 1 mode (auto eller desirable).  On both switches.
	13. Pagp: int range fast 0/nr-nr (ent) ,  swittchport mode trunk (ent) , channel-protocol lacp (ent) , channel-group 1 mode (active eller passive).  On both switches.
	
	14. Spaning-tree mode rapid-pvst.
	
	15. Bpduguard och portfast: Int fa -/- (ent) , swtichport mode access (ent), spaning-tree portfast (ent), spaning-tree bpduguard enable, (ent).
	
	16. Hsrp: int f-/- (ent) , standby 1  ip 0.0.0.0 (ent) , stadnby 1 priorety nr (ent), standby preempt. 
	
	17. Config eigrp :Router eigrp 1 (ent) , network 0.0.0.0 wildcardmask (ent), for all network and interfaces.
	
	18. Advanced config eigrp:
	19. Bandwidth:  conf t (ent) , int fa -/- (ent) bandwidth 128 
	20. Hello-interval: int g -/- (ent) , ip hello-interval eigrp area sec. 
	21. Hold-time: int g -/- (ent) , ip hold-time eigrp area sec.
	22. Bandwidth percent : int -/- (ent) , ip bandwidth-percent eigrp 1 70

	1. Ppp encap with chap: conf t (ent), username Rx password cisco (ent) , int -/- enacp ppp
	(ent), ppp authentication chap. På båda routrar.  

	
	
	
	

