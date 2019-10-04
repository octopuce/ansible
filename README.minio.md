# How to use

Choose a list of hosts to apply the playbook on, and run ansible-playbook:

    ansible-playbook -i host1,host2,host3 ./minio-server.yml

For a single host, add a trailing comma:

    ansible-playbook -i host1, ./minio-server.yml

