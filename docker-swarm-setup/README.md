# Docker Swarm Setup

Hi, here I am going to setup Docker Swarm in Ubuntu 22.04 machines.
One machine will be Docker swarm manager and another as Docker swarm worker.

**Manager Machine** is manager1.local (IP - 10.168.1.1).  

**Worker Machine** is worker1.local (IP - Dynamic).  

## Initialize Docker Swarm 

`docker swarm init`

After successful execution of above command, it will give the output as below

```
To add a worker to this swarm, run the following command:

    docker swarm join --token SWMTKN-1-5w4u4nzhwx8hxeqaueb4lbe65xi07sw1mmf9htcdpg09mda7ul-cyh0z060ho28fsfyjage8kixo 10.168.1.1:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
```

You can now join new nodes in the Docker swarm as worker nodes or additional manager nodes using command provided in the output.

Now this maachine is the **Swarm manager** in this cluster.

##  Add worker node to swarm

Run the following command on the **worker node** to add that node as worker in the Docker swarm

```
docker swarm join --token SWMTKN-1-5w4u4nzhwx8hxeqaueb4lbe65xi07sw1mmf9htcdpg09mda7ul-cyh0z060ho28fsfyjage8kixo 10.168.1.1:2377
```

## Checking nodes in swarm

`docker node ls`

You will see output as below -

```
ID                            HOSTNAME                STATUS    AVAILABILITY   MANAGER STATUS   ENGINE VERSION
i8rkp2144ajpllq8h9n7pfa94     worker1.local          Ready     Active                          27.4.1
3z3yocel9o6dta9iz4evc992p *   manager1-linux         Ready     Active         Leader           27.2.1
```

The asterisk sign shows that it is the **manager** of the cluster.

Now you can add as many workers to the cluster as you want, and also additional manager nodes.
The setup is ready to serve as a Docker swarm.