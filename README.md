# terraform_devoxx

## Video

[![Terraform Devoxx](http://img.youtube.com/vi/6tgpv2-dEMM/0.jpg)](http://www.youtube.com/watch?v=6tgpv2-dEMM "Terraform Devoxx")

## keygen

```
ssh-keygen -t rsa -C "aws_instance_rsakey" -P '' -f ssh/aws_instance_rsakey
```

## terraform cmd

```
alias terraform='docker run --rm -it -v $HOME/.aws/credentials:/credentials:ro -v $(pwd):/data --workdir=/data hashicorp/terraform:0.8.6'
```

```
terraform plan
terraform apply
terraform show
terraform destroy
```

## inventory

```
docker run --rm --workdir=/data -v $(pwd):/data ansible terraform-inventory --inventory > terraform101.inventory
```

## ansible cmd

```
alias ansible='docker run --rm -v $(pwd)/terraform101.inventory:/etc/ansible/hosts:ro -v $(pwd)/ssh/aws_instance_rsakey:/id_rsa:ro ansible:dev ansible -e "ansible_python_interpreter=/usr/bin/python3" --private-key /id_rsa -u ubuntu'
alias ansible-playbook='docker run --rm -v $(pwd)/goapp:/goapp:ro -v $(pwd)/ansible/playbook.yml:/data/playbook.yml -v $(pwd)/terraform101.inventory:/etc/ansible/hosts:ro -v $(pwd)/ssh/aws_instance_rsakey:/id_rsa:ro ansible:dev ansible-playbook -e "ansible_python_interpreter=/usr/bin/python3" --private-key /id_rsa'
```

```
ansible-playbook /data/playbook.yml
```
