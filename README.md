# ansible-aws
A simple pedagogic project to explore provisionning aws ressources with Ansible

## Setup with aws academy

Start the devcontainer associated with this repository.

Then, start your lab in aws academy lms, once started go to AWS Details and copy AWS CLI credentials

Paste the content directly in credential file as follow :

```
echo "[default]
aws_access_key_id=[...]" > .aws/credentials
```

Be care it's `.aws/credentials` and not `~/.aws/credentials`

To be sure all is working correctly, run this command :

```
aws ec2 describe-instances
```

You can now try to create an ec2 instance :

```
ansible-playbook create-start-1-vm.yml
```


