# Graduate2021
vagrant up
ansible-playbook java-playbook.yml, docker_playbook.yml, maven.yml, jenkins_playbook.yml

Playbook-ul de jenkins trebuie rulat de mai multe ori deoarece nu face mereu conexiunea pentru unele pachete si plugin-uri.

In jenkins trebuie configurate manual credentialele de docker hub si maven tool-ul.
Pe masina de jenkins trebuie rulata comanda "sudo chmod 777 /var/run/docker.sock" pentru a ii permite userului jenkins sa ruleze comenzi de docker. Cheile id_rsa* trebuie create in jenkins@jenkins si copiata cea publica pe masina de productie + adaugat la authorized pentru a putea rula ssh de pe masina de jenkins din pipeline.

Pipeline-ul cloneaza dintr-un repository aplicatia de spring boot, ii face build cu maven, creeaza o imagine de docker pe baza unei imagini de open-jdk in care copiaza .jar-ul creat si il ruleaza cu comanda java -jar. Imaginea de docker este urcata pe docker hub cu credentialele din jenkins, se sterge de pe local. Iar in final se sterg containerele de pe masina de productie si se genereaza containerul creat pe baza imaginii de docker de pe hub.
Conexiunea catre aplicatia de spring boot se face pe adresa masinii producite (192.168.50.22) pe portull 8001. 