# how to run the libradtran example with ubuntu 20.04

0) clone the repo

 

1) use conda to install ansible

   `conda install ansible`

2) use ansible to 

   `cd ansible`
   `ansible-playbook -i hosts.yaml  playbook.yml   --extra-vars "ansible_become_pass=password"`

(/libRadtran-2.0.2/bin/uvspec < uvspec_thermal_high.inp > results.txt) >& errors.txt

`docker-compose run isofit`

`cd /isofit/example/20171108_Pasadena`

`./run_example_libradtran.sh`


