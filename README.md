# Dummy Flask Deploy
An ansible playbook to deploy a flask webapp to an AWS ec2 instance

## Features

* Creates an instance of AWS EC2

## Requirements

* Ansible must be installed on your machine
* You must have an account on AWS and have your access keys
* You must have an AWS key pair as a pem file
* Boto python module must be installed (AWS requirement)


## Configuration

* Make sure your AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY environment 
variables are set. To do so, on an unix machine for exemple, type

```
export AWS_ACCESS_KEY_ID='AK123'
export AWS_SECRET_ACCESS_KEY='abc123'
```

## Deploy

* Go to the directory where you cloned the repository
* The first time you deploy, type

```
ansible-playbook -i hosts deploy-flask-playbook.yml
```
* This will populate the host file with the EC2 instance
* Now deploy the app by using:

```
ansible-playbook -i hosts --skip-tags provision deploy-flask-playbook.yml
```


## Known caveats

* If you stop/terminate the ec2 instance created, you will have to manually 
remove its entry (below ```[launched]```) from the hosts file then re-deploy 
as for the first time.
