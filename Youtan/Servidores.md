---
id: Servidores
aliases: []
tags: []
---

# Comandos

1 - Restart de serviços

    sudo systemctl restart nginx && sudo systemctl restart inovatax && sudo systemctl restart celery && sudo systemctl restart rabbitmq-server

1.1 - Restart separado de serviços

    sudo systemctl restart nginx
    sudo systemctl restart inovatax
    sudo systemctl restart celery
    sudo systemctl restart rabbitmq-server

------------------------------------------------------------

2 - Interromper serviços

    sudo systemctl stop inovatax && sudo systemctl stop nginx && sudo systemctl stop celery && sudo systemctl stop rabbitmq-server

2.1 - Interromper serviços separadamente

    sudo systemctl stop inovatax &&
    sudo systemctl stop nginx &&
    sudo systemctl stop celery &&
    sudo systemctl stop rabbitmq-server 

------------------------------------------------------------

3 - Inicializar serviços

    sudo systemctl start inovatax && sudo systemctl start nginx && sudo systemctl start celery && sudo systemctl start rabbitmq-server

3.1 - Inicializar serviços separadamente

    sudo systemctl start inovatax
    sudo systemctl start nginx
    sudo systemctl start celery
    sudo systemctl start rabbitmq-server

------------------------------------------------------------

4 - Status serviços

    sudo systemctl status inovatax && sudo systemctl status nginx && sudo systemctl status celery && sudo systemctl status rabbitmq-server

4.1 - Status serviços separadamente

    sudo systemctl status inovatax
    sudo systemctl status nginx
    sudo systemctl status celery
    sudo systemctl status rabbitmq-server

------------------------------------------------------------

5 - Confirmação de branch e atualização sua atualização

    git branch -a
    git pull

------------------------------------------------------------

6 - Caminho atualização

    /var/www/inovatax

------------------------------------------------------------

7 - Inserindo tabelas externas no banco de dados

    python manage.py loaddata tools/initialdata/areas.json &&
    python manage.py loaddata tools/initialdata/contas_referencias.json &&
    python manage.py loaddata tools/initialdata/RFBParteB.json &&
    python manage.py loaddata tools/initialdata/codigo_receita_dirf.json &&
    python manage.py loaddata tools/initialdata/codigo_tipo_credito.json &&
    python manage.py loaddata tools/initialdata/tabela_5.json &&
    python manage.py loaddata tools/initialdata/lei_complementar_116.json &&
    python manage.py loaddata tools/initialdata/base_calculo_credito_4_3_7.json &&
    python manage.py loaddata tools/initialdata/tabela_paises.json &&
    python manage.py loaddata tools/initialdata/tabela_5_2.json &&
    python manage.py loaddata tools/initialdata/tabela_5_4.json &&
    python manage.py loaddata tools/initialdata/table_4_2_1.json &&
    python manage.py loaddata tools/initialdata/tabela511.json

    python manage.py loaddata tools/initialdata/*.json

------------------------------------------------------------

8 - Caminho para aumentar capacidade de tamanho de arquivos

    /etc/nginx/sites-available/inovatax
    inserir: "client_max_body_size       20000m;"
    sudo systemctl restart nginx

------------------------------------------------------------

9 - Provocar erro no F12

    /var/www/inovatax/inovatax/templates/files
    adicionar "// " antes de "location.reload();"

------------------------------------------------------------

10 - Reconstruir uwsgi/inovatax.sock quando servidor cair dentro de "run" (se for esse o problema)

    /var/run/;
    mkdir uwsgi
    touch inovatax.sock
    resultado: /var/run/uwsgi/inovatax.sock

------------------------------------------------------------

# Servidor Youtan

11 - Servidor Youtan

    ssh root@192.53.164.85
    inovatax@135
    http://inovatax.dessimoni.com/

    ssh youtan@45.56.120.186
    RWq*W0X2QHEBX8TlNt
    http://martinelli-inovatax.youtan.com.br/
    
    caminho dos projetos: /home/youtan/martinelli

11.1 - Servidor de Banco de Dados (DEV):

    Host: 173.255.193.85
    DB: inovatax_db
    User: SA
    Password: inovatax@135

    Host: 45.56.120.186
    DB: martinelli_inovatax
    User: SA
    Password: hqv5g8B4ZboJ

------------------------------------------------------------

# Servidores Martinelli

12 - Inovatax (credenciais FortClient)

    Nome da Conexão: Martinelli
    Descrição: Inovatax
    Gatway Remoto:
        200.193.36.205:443
        177.67.89.186:443
        177.0.200.3:443
        177.0.200.6:443
        vpn.martinelli.adv.br:443
    Username: youtan
    Password: 9xzz24ytm@!4555yt8tH@

12.1 - Homologação

    https://taxqs.portalmartinelli.adv.br/
    ssh inovatax@192.168.0.148
    Password: 1aW&=%yt7D0f%g<9D
    Nome da máquina: MTLADVL048

12.1.1 - Servidor de Banco de Dados (HML):

    Host: 192.168.0.168
    DB: dwqs
    User: dwqsusr
    Password: hozsGag2n5

12.2 - Produção

    https://tax.portalmartinelli.adv.br/
    ssh inovatax@192.168.0.107
    Password: 555yt8tH<f-i%<jjw
    Nome da máquina: MTLADVL051

12.2.1 - Servidor de Banco de Dados (PROD):

    Host: 192.168.0.168
    DB: inovatax_db
    User: SA
    Password: D&hzklfuzcJQ
