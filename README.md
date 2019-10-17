# Ansible playbooks for new infrastructures

# outdated

## Quick use
### Run
Si tous les fichiers de configuration sont déjà renseignés, éditer les 3 premières variables des la commande suivante et l'éxecuter
```
client='' && cluster='' && myplaybook='' && cd /usr/local/share/ansible/ && ansible-playbook  -i /infra/$client/ansible/$cluster/hosts -e var_file=/infra/$client/ansible/$cluster/vars.yml $myplaybook.yml
```
Exemple :
```
client='mylittleparis' && cluster='prodfront6' && myplaybook='keepalived' && cd /usr/local/share/ansible/ && ansible-playbook  -i /infra/$client/ansible/$cluster/hosts -e var_file=/infra/$client/ansible/$cluster/vars.yml $myplaybook.yml
```

### Configure
Si non, créer la configuration nécessaire.  
Créer le répertoire si besoin.
``̀ 
mkdir /infra/$client/ansible/$cluster
``̀ 
Créer le fichier host avec comme contenu.
```
[nodes]
IP1
IP2
`̀``
Copier le fichier template des variables et l'éditer au besoin.
`̀``
cp /usr/share/local/ansible/vars.yml /infra/$client/ansible/$cluster/.
vim /infra/$client/ansible/$cluster/vars.yml
`̀``
Executer la commande du chapiter "### Run".

### NOOP
--check

### Debug
-vvvv

## Usage 

* You MUST build a host file containing an IP per host 
* You MUST build a vars file containing the variables required by the ansible playbooks
* Run `ansible-playbook -i /infra/INFRA/ansible/prod.host -e "var_file=/infra/INFRA/ansible/vars.yml" PLAYBOOK.yml`
  - Eventually, `ansible-playbook -i /some/infra/hosts --limit somegroup PLAYBOOK.yml`
