# thibault 06 09 2019

#ATTENTION: not tested, will likely fail and need basic fixes, maybe do not use if can't debug ansible code, or thibault's not here
#ATTENTION2 : le fichier host ne doit avoir exactement 2 hôtes renseignés

Mysql réplication

Rôle pour déployer une réplication Mysql circulaire croisée

Variables à passer :

replication:
  user: 'replication'
  password: 'XXXXXXXX'

# si aucune n'est renseignée, la réplication s'effectuera sur toutes les tables
do_dbs : [ 'doing', 'these', 'dbs' ]
do_NOT_dbs : [ 'useless', 'skipping' ]

node1:
  host: '1.1.1.1'
  serverid: 1

node2:
  host: '8.8.8.8'
  serverid: 8
