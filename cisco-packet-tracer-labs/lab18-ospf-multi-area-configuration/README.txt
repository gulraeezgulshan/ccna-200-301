!!!Configuring R1
!
enable
configure terminal
!
int s0/0
ip add 10.0.0.1 255.0.0.0
no shut
!
int f0/0
ip add 192.168.1.100 255.255.255.0
no shut
!
exit
!
router ospf 1
network 192.168.1.0 0.0.0.255 area 10
network 10.0.0.0 0.255.255.255 area 10
end
!
write
!

!!!Configuring R2
!
enable
configure terminal
!
int s0/0
ip add 10.0.0.2 255.0.0.0
no shut
!
int s0/1
ip add 11.0.0.1 255.0.0.0
no shut
!
int f0/0
ip add 192.168.2.100 255.255.255.0
no shut
!
exit
!
router ospf 1
network 192.168.2.0 0.0.0.255 area 0
network 10.0.0.0 0.255.255.255 area 10
network 11.0.0.0 0.255.255.255 area 20
end
!
write
!


!!!Configuring R3
!
enable
configure terminal
!
int s0/1
ip add 11.0.0.2 255.0.0.0
no shut
!
int f0/0
ip add 192.168.3.100 255.255.255.0
no shut
!
exit
!
router ospf 1
network 192.168.3.0 0.0.0.255 area 20
network 11.0.0.0 0.255.255.255 area 20
end
!
write
!