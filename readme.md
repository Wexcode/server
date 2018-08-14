[![Build Status](https://travis-ci.org/Wexcode/server.svg?branch=travis-ci)](https://travis-ci.org/Wexcode/server)

# Personal Server

## Terraform

### Setup

We will copy our public keys to terraform so that we can reference it instead of copying the contents directly in.

```bash
cd terraform
cp ~/.ssh/id_rsa.pub .
terraform init
```

### Run

```bash
cd terraform
terraform apply
```

### Issues encountered

#### Missing default AWS VPC

If you're account was created pre 2013, your region may not have a default VPC.
It's possible to create one by opening a ticket with AWS but the short term solution is to try a newer region like us-east-2.

#### AWS variables poluting the environment

AWS keys saved in the environment will override the profile setting in the configuration.
This can be checked by running:

```bash
env | grep AWS
```

If you see AWS variables here, they can be temporarily removed with:

```bash
env -u AWS_ACCESS_KEY_ID -u AWS_SECRET_ACCESS_KEY terraform apply
```

## Ansible

```bash
cd ansible
ansible-playbook -i inventory playbook.yml
```
