# how to run the libradtran example with ubuntu 20.04

0) clone the repo

        git clone https://github.com/phaustin/isofit_docker.git
        git checkout -b dashboard origin/dashboard

1) use conda to install ansible
  
         conda install ansible

2) use ansible to create user isofit with uid 1000.  Replace `password` with your sudo password

         cd isofit_docker/ansible
         ansible-playbook -i hosts.yaml  playbook.yml   --extra-vars "ansible_become_pass=password"

3) make sure that `isofit_docker/libradtran_examples` is owned by user isofit,
   has group write permission and belongs to your group

        sudo chown -R isofit_docker/libradtran_examples
        sudo chgrp -R mygroup docker/libradtran_examples
        sudo chmod -R g+w docker/libradtran_examples

4) start a docker session in a terminal

        cd isofit_docker
        docker run --name dashboard isofit

5) you should now have the host directory `isofit/libradtran_examples` bind mounted
   inside the container as `/analysis_scripts/libradtran_examples`

6) run libradtran inside the container

        cd /analysis_scripts/libradtran_examples
        (/libRadtran-2.0.2/bin/uvspec < uvspec_thermal_high.inp > results.txt) >& errors.txt

7) inspect the output on the host
 
        cd isofit/libradtran_examples
        cat results.txt
        cat errors.txt
