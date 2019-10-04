#main : thibault 06 09 2019

#description : 
  Rôle pour déployer des vhosts Apache

#prerequis :
  Les soft installés, cocher les cases panel

#variables :

  # variables qui vont templater le ports.conf d'apache
  
  listen:
    port: 8000
    ip: '127.0.0.1'
  
  # variables qui vont templater les différents hosts d'apache
  
  domain.name: suffixe du FQDN
  
  will loop for each hostname in hostnames:
  hostname:
  	name: sous-partie du FQDN
  	root: DocumentRoot + va create un dossier correspondant détenu par www-data
  	fpm: va templater une conf de vhost pour php_fpm (avec FilesMatch et SetHandler)
  	fpm_proxy: required if fpm is True
  		permet de mettre le bon path à SetHandler
  	valid: active ou non le site ds sites-enabled
  
  
  domain:
    name: octopuce.fr
    hostnames:
      - { name: cairnint1, root: /data/www/sites/prod/cairn-int, valid: True, fpm: True, fpm_proxy: php7.2-fpm-cairnint.sock }
      - { fpm_proxy: php5.6-fpm-aquarium.sock, fpm: True, root: /var/www/aquarium, name: aquarium, proxy: 'http://127.0.0.1:8000', valid: yes, generate_certs: True }
  
  #### le second example mêle des var utilisés ds les rôles nginx ET apache :)
