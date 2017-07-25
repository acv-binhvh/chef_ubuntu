# chef-ubuntu

Chef Solo config for management servers with Ruby/Rack based applications

## Tutorial

Using Chef setup server for rails on Ubuntu 16.04

## Stack
* Ubuntu 16.04
* PostgreSQL or MYSQL
* Redis
* Monit
* RVM
* Node.js
* Nginx
* Ncdu

## Usage

Please add your ssh key to server first then

```bash
cp nodes/machine.ip.json nodes/my_new_node.json
```

Insert machine IP into next files:

```bash
site-cookbooks/chef-nginx/templates/project.conf.erb
```

```bash
nodes/my_new_node.json
```

Replace passwords into base (roles/base.json and data_bags/users/deployer.json) and run:

```bash
bundle exec knife solo bootstrap root@ip nodes/my_new_node.json
```

## Select SQL (Default MYSQL)

If use postgresql, please uncomment settings of postgresql in 

```bash
roles/base.json
```
and block comment 

```bash
"recipe[database]"
```

## SSH to server

Please update your ssh key to 

```bash
data_bags/users/deployer.json
```