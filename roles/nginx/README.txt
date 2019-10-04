#main :  thibault 06 09 2019

#description : 
  Rôle pour déployer des vhost Nginx

#prerequis :
  Les soft installés, cocher les cases panel
  Bien penser à ce que l'IP doit pointer vers la bonne machine si vous voulez les certs TLS



#variables :

  Les variables de domain sont utilisées de la même manière que les Variables de hostname. pour pouvoir créer une configuration de base pour domain.com par exemple.
  
  domain
  	name: suffixe du FQDN
  
  will loop for each hostname in hostnames:
  hostname:
  	name: sous-partie du FQDN
  	valid: active ou non le site ds sites-enabled
  	generate_certs:  will comment out ssl paths, then generate certs, then uncomment ssl paths
  	proxy: who to proxy to ( usually an Apache or Varnish or etc )
  	whitelist: list of CIDR to be whitelisted, none will allow everyone
  
  domain:
    name: givav.fr
    proxy: https://givav.fr
    whitelist: [ '1.1.1.1/30' ]
    hostnames:
      - { name: www, whitelist: [ '1.1.1.1', '8.8.8.8/24' ], proxy: 'https://www.givav.fr', valid: 'yes' }
      - { name: wiki, proxy: 'https://wiki.givav.fr', generate_certs: false }
      - { name: mobile, proxy: 'https://mobile.givav.fr', generate_certs: true }
      - { name: forum, proxy: 'https://forum.givav.fr' }
      - { name: club, proxy: 'https://club.givav.fr' }
      - { name: admin, proxy: 'https://admin.givav.fr' }
  
  
