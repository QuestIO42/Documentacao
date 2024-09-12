# Documentações do projeto `QuestI0`

🚨 Para cada documento neste repositório **deve** haver um link apontando para ele nesta página. O mesmo para novos respositórios (incluir um README.md e linkar aqui). Isso facilita encontrar toda a documentação a partir de um mesmo lugar. 

## Documentos principais (⚠️fazer PR junto com a documentação e checar se existe na revisão⚠️)

- [Documento de requisitos](https://docs.google.com/document/d/1mrN9p3zhKcqRMqToB9Mj0hIYp-NVSA3TKEJNZaxD_MU/edit)
- [Diagrama de classes](https://lucid.app/lucidchart/f5e6c5eb-463a-4fad-a00e-e6fe9bb9619d/edit?invitationId=inv_e14c10db-b853-4ef4-ab46-31e7446cf394&page=HWEp-vi-RSFO#)
- [Schema SQL](SQL/Schema.md)
- [Endpoints](Back-API/README.md)
- [Telas](https://www.figma.com/design/eGVW2hBg9H8dQxIfM2iYYx/Portal-LD?node-id=0-1&t=XuDshWnr7wFOcb1I-0)

## Hosts

### [Acesso SSH](DevOps/SSH.md)

### Servidor principal (acessível externamente)

```
ssh -p 2021 user@vlab.dc.ufscar.br 

menotti@vlab:~$ uname -a 
Linux vlab.dc.ufscar.br 5.15.0-106-generic #116-Ubuntu SMP Wed Apr 17 09:17:56 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

menotti@vlab:~$ cat /etc/os-release 
VERSION="22.04.4 LTS (Jammy Jellyfish)"
```

## Práticas de desenvolvimento

### [Conventional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0-beta.4/)

### Deploy

As branchs `main/master` de cada repositório rodam no diretório `/srv/DevOps` do servidor.

Caso queira testar outra branch no servidor antes de fazer `merge`, basta clonar o repositório em sua pasta local e subir o container normalmente. Ele vai substituir o container padrão, pois possui o mesmo nome. Depois, basta voltar no camino `/srv/DevOps` e subir o container padrão. 

> Consulte mais informações em [DevOps](https://github.com/QuestIO42/DevOps)

## Web page 

* [https://questio42.github.io](https://github.com/QuestIO42/QuestIO42.github.io)

## Git

* [Tutorial para realizar seu primeiro Pull Request](https://github.com/PortalLD/Documentacao/blob/main/Versionamento/PR%20-%20Git%20e%20GitHub.md)
* [Minha Branch está desatualizada, o que eu devo fazer?](Versionamento/atualizando%20sua%20branch.md)

## DevOps

* [Docker](https://github.com/QuestIO42/DevOps)

## Backends

### Python/Django

* [Versão 5.0](https://github.com/QuestIO42/App-backend-django)
* http://localhost:9000 -> https://django.vlab.dc.ufscar.br/

### Java/Spring

* [Versão 3.3.0](https://github.com/QuestIO42/App-backend-Spring)
* http://localhost:9002 -> https://spring.vlab.dc.ufscar.br/

### Node/Fastify

* [Versão 4.27.0](https://github.com/QuestIO42/App-backend-Node.js)
* http://localhost:9001 -> https://fastify.vlab.dc.ufscar.br/

### Jupyter/Notebook

* [JupyterHub:latest](https://github.com/QuestIO42/DevOps/tree/main/jupyter/)
* http://localhost:8000 -> https://jupyter.vlab.dc.ufscar.br/

## Frontend 

* [ReactJS](https://github.com/QuestIO42/App-frontend)
* http://localhost:3000 -> https://react.vlab.dc.ufscar.br/ (dev) -> https://questio.vlab.dc.ufscar.br/ (prod)

## APIs

* [Judge](https://github.com/QuestIO42/Judge-API)

## Lab. Virtual

* [legacy](https://github.com/QuestIO42/vlab)
