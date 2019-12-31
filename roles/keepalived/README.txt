#main : thibault 17 12 2019

#description : 
  Rôle pour installer et déployer des ip virtuelles ( == VIP ) keepalived

#prerequis :
  Cocher les cases panel

#variables :

  will loop for each ip in ips:
  ips:
    id: [int] 0 < id < 100
    name: [string] le nom de la VIP
    interface: [string] l'interface pour la VIP ( attention, sera la même pour la source du ping )
    timeout: [int] le temps ( secondes ) de down que keepalived accepte avant de basculer la VIP
    vip: [string] la vip (cidr v4 ou v6)
    master: [string] l'ip du master (v4 ou v6)
    slave: [string] l'ip du master (v4 ou v6)
    attached_ips : {opt}[list] listes des vip attachées ( le cas utile est d'attacher la v6 ou v4 correspondante à la vip, histoire de basculer les deux )
      - [string] ip (cidr v4 ou v6)

#exemple

ips:
  - { id: 53, name: web, interface: eth0, timeout: 5, vip: 185.34.32.53/32, master: 185.34.32.50, slave: 185.34.32.51, attached_ips : ['2001:67c:288:32:0:0:0:53/128'] }
  - { id: 42, name: db, interface: eth1, timeout: 5, vip: 10.1.32.53/32, master: 10.1.32.51, slave: 10.1.32.50, attached_ips : [] }

