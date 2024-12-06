# ansible-aws
A simple pedagogic project to explore provisionning aws ressources with Ansible

## Setup with aws academy

Start the devcontainer associated with this repository.

Then, start your lab in aws academy lms, once started go to AWS Details and copy AWS CLI credentials

Paste the content directly in credential file as follow (should reproduce this step every time you restart your lab):

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
ansible-playbook create-start-vms.yml
```

Now configure your private SSH key, downloading pem from interface into .ssh/labsuser.pem

Set correct permissions as follow :

```
chmod 600 .ssh/labsuser.pem
```

You should now be able to ping the VM using :

```
vscode ➜ /workspaces/ansible-aws (main) $ ansible -m ping mavm
[WARNING]: Platform linux on host ec2-34-201-62-113.compute-1.amazonaws.com is using the discovered Python interpreter at
/usr/bin/python3.12, but future installation of another Python interpreter could change the meaning of that path. See
https://docs.ansible.com/ansible-core/2.18/reference_appendices/interpreter_discovery.html for more information.
ec2-34-201-62-113.compute-1.amazonaws.com | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3.12"
    },
    "changed": false,
    "ping": "pong"
}
```
