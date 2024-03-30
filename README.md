# EDGE5G Infra Testbed

Sobre aaa...

## Configurando o ambiente da máquina hospedeira.
Certifique-se que os seguintes pacotes:
- ssh
- git
- vim
- ansible

Execute o seguinte comando para instalar todos os pacotes necessário para rodar o testbed.
```sh
$ sudo apt install ssh git ansible vim
```

Inicie o serviço do OpenSSH da máquina hospedeira.
```sh
$ sudo systemctl enable --now ssh
```

Crie as chaves pública e privada para o SSH, caso já possua esse passo não é necessário.
```sh
$ ssh-keygen
```

Copie a chave pública para a própria máquina.
```sh
$ ssh-copy-id localhost
```

Clone o repositório.
```sh
$ git clone git@github.com:pauloditarso/edge5g_infra.git
```

Agora exiba e copie o valor da sua chave pública, para podermos configurar o acesso as novas máquinas virtuais que vão ser criadas.
```sh
$ cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCoXpD5s8P+5knmVH7ZXoMPOX5eIomcudQA2j5SAH1ZPj6TIk2H50QJZ07OHvnOeNBFL9rTBGlDBlTW9mflfMuLT4FPWDEs22G7rBd7b9TYkcoe/tI9ve5ZGw3aOk4lSlyK6sVj463rTsIbV+U6j26v6QjSgDGbTMMNSsIyIP8o6NNoVEPCGN73F+fqVa5LTy9JRssngQezES2s5VAPtFWN9LK4l4WFa2Xjgt0/feM1B2YJcNP+wvIaWlpyCXYYM+dRrVNUMEQDXAYQi2eJ3+gqp4UkX1dJx98k7F/nshDhbvuCE7VKfpDHQRGI1Thd/LShlQej9MP8d8to/e5DSazHqjdIHDRTQlq9BwPXWHysHAV0Hq1P/CDCnX0pbdlzXczd6CD9l4c6ZAgJS6vVO3hXwWltzLfPC7XJRdipG29JHNB/nzti5Vdu+DAMeJWluXUeXaJaWnHwmjdGpDfpWKswDI+W9vDfdBQCIdgPxlohGSMMjUathPJY73b5QsmQoNM= administrador@vm-ubuntu
```

Insira a chave SSH nos seguintes arquivos.
- ~/edge5g_infra/roles/KVM/files/ifpb-c-plane.cfg
- ~/edge5g_infra/roles/KVM/files/ifpb-u-plane1.cfg
- ~/edge5g_infra/roles/KVM/files/ifpb-u-plane2.cfg
- ~/edge5g_infra/roles/KVM/files/ifpb-gnb.cfg
- ~/edge5g_infra/roles/KVM/files/ifpb-ue1.cfg
- ~/edge5g_infra/roles/KVM/files/ifpb-ue2.cfg
- ~/edge5g_infra/roles/KVM/files/ifpb-mininet.cfg

## Criando o ambiente de testbed usando o Ansible.

Agora que nós já configuramos todos os arquivos necessários, basta executarmos a playbook do Ansible.
```sh
$ ansible-playbook playbook.yaml
```

## Usuário e Senhas

Todas as máquinas virtuais tem o mesmo padrão de usuário e senha.

Usuário: **administrador**
Senha: **Mudar@123**
