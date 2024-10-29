---
id: Publicacao
aliases: []
tags: []
---

# Passo a Passo:

1- Conectar na vpn martinelli
    vpn.martinelli.adv.br:443
    usuário: youtan
    senha: 9xzz24ytm@!4555yt8tH@

2 - Acessar Servidor    
    ssh youtan@ipservidor
    cd /var/www

3 - Criar pasta do projeto
    sudo mkdir nomeappgit
    sudo chown youtan:youtan nomeappgit
    git clone
    para back criar o .env

merge quando subir pra producao, pegar da homolog (desabilitar caixinha de apagar branch apos o merge (gitlab))

settings do repo, criar deploy token (se atenta as portas)
    
4 - Configurando NGINX
    cd /etc/nginx
    cd sites-available
    cp "algumprojeto" nomeappgit
    cd sites-enabled
    sudo ln -s /etc/ngnix/sites-available/nomeappgit nomeappgit
    sudo systemctl restart nginx
