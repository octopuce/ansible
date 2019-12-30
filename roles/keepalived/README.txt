#main : thibault 17 12 2019

#description : 
  Rôle pour installer et déployer des ip virtuelles ( == VIP ) keepalived

#prerequis :
  Cocher les cases panel

#variables :

  will loop for each ip in ips:
  ips:
    name: [string] le nom de la VIP
    interface: [string] l'interface pour la VIP ( attention, sera la même pour la source du ping )
    timeout: [int] le temps ( secondes ) de down que keepalived accepte avant de basculer la VIP
    vip: [string] la vip (cidr v4 ou v6)
    master: [string] l'ip du master (v4 ou v6)
    slave: [string] l'ip du master (v4 ou v6)
    attached_ips : {opt}[list] listes des vip attachées ( le cas utile est d'attacher la v6 ou v4 correspondante à la vip, histoire de basculer les deux )
      - [string] ip (cidr v4 ou v6)

