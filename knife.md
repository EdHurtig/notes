# Knife Notes

> Knife is a command line tool for managing a chef enviornment

## Creating Servers

> This Assumes you are using the `knife-ec2` plugin

### Create a new server and apply a recipe

`knife ec2 server create -E staging -N test-server-1 -s subnet-xxx -f c3.large -g sg-xxx -r "recipe[my_recipe]"`

Explained...

`knife ec2 server create -E <enviornment> -N <Node Name> -s <Subnet AV Specific> -f <Instance Type> -g <Security Groups,Comma Delim> -r "<Recipes, Comma Delim, all in quotes>"`


## Deleting Servers

This will delete the EC2 Instance and purge the node/client from the chef server

`knife ec2 server delete i-xxxxxxxx -P -N test-server-1`

Exmplained...

`knife ec2 server delete <Instance ID> -P -N <Chef Node Name>`



## Concurrent SSH

Run a command on all servers matching some criteria

`knife ssh 'name:test-server-*' 'sudo chef-client'`

> This will converge all servers named with the `test-server-` convention that are managed by chef.  So test-server-1, test-server-2, test-server-bleah will all be converged

Explained...

`knife ssh '<field (name)>:<regex>' 'sudo chef-client'`


## Other cheffy things

> Often your first convergence will fail because something broke.  To rerun the first convergence you need to SSH to the EC2 Instance and run the following

### Manually retry First Run Chef
sudo chef-client -E <Enviornment> -N <Node Name> -j /etc/chef/first-boot.json 
