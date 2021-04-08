# Instal·lació JuypyterHub i Labs

L'intenció es poder accedir al notebooks de jupyter en un entorn multiusuari.

## Fer Python 3 l'opció per defecte i instal·lar els paquets necessaris

    $ sudo rm /usr/bin/python
    $ sudo ln -s /usr/bin/python3 /usr/bin/python
    $ sudo apt install python3 python3-dev git curl python3-venv

## Instal·lar el gestor de paquets de Python

    $ sudo apt-get install python3-pip
    $ sudo pip3 install --upgrade pip


## Instal·lar Jupyter Notebook, Hub i Lab

JupyterHub consists of three components:
A single-user notebook server that is started for every user on the system when they log in. This is basically what you have installed on your laptop and start with jupyter notebook.
The hub that manages the user accounts, authentication and coordinates the single-user notebook servers.
A proxy that routes the user requests to the hub and the notebook servers.

###  Instal·lar sistema npm i proxy

npm és el sistema de node.js un entorn de programació en javascript.
    $ sudo apt install nodejs npm
    $ sudo npm install -g configurable-http-proxy

### Crear l'entorn virtual on funcionarà Jupyter

    $ sudo python3 -m venv /opt/jupyterhub/
Atenció que tot, tot, el que s'instal·li per a jupyter s'haurà d'instal·lar en aquest entorn.  Es pot distingir per l'ordre "/opt/jupyterhub/bin/python3 -m" que ha de precedir a tot.

### Instal·lar JupyterHub (amb els notebooks)
    $ sudo /opt/jupyterhub/bin/python3 -m pip install wheel
    $ sudo /opt/jupyterhub/bin/python3 -m pip install jupyterhub jupyterlab
    $ sudo /opt/jupyterhub/bin/python3 -m pip install ipywidgets

Crear la configuració

    $ sudo mkdir -p /opt/jupyterhub/etc/jupyterhub/
    $ cd /opt/jupyterhub/etc/jupyterhub/
    $ sudo /opt/jupyterhub/bin/jupyterhub --generate-config
És a dir, crea el directori per a la configuració i s'accedix. Crida a jupyterhub per a crear la configuració en el directori actual.

Podem afegir l'opció que arrenqui directament amb Jupyter Lab:
    $ nano jupyterhub_config.py

    c.Spawner.default_url = '/lab'

## Establir com a servei del sistema

Crear el directori on es guarda el fitxer de servei
    $ sudo mkdir -p /opt/jupyterhub/etc/systemd

Crear el fitxer del servei:
    $ sudo nano /opt/jupyterhub/etc/systemd/jupyterhub.service

    [Unit]
    Description=JupyterHub
    After=syslog.target network.target

    [Service]
    User=root
    Environment="PATH=/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/opt/jupyterhub/bin"
    ExecStart=/opt/jupyterhub/bin/jupyterhub -f /opt/jupyterhub/etc/jupyterhub/jupyterhub_config.py

    [Install]
    WantedBy=multi-user.target
Fer notar que en cas de caiguda no rearranca. Només en l'arrencada del sistema.

Establer un enlace para activar el servicio
    $ sudo ln -s /opt/jupyterhub/etc/systemd/jupyterhub.service /etc/systemd/system/jupyterhub.service

Activar el sistema i comprovar el funcionament.
    $ sudo systemctl daemon-reload
    $ sudo systemctl start jupyterhub
    $ sudo systemctl enable jupyterhub
    $ sudo systemctl status jupyterhub.service

Comprovar el funcionament a
http://raspib.local:8000
Entrar amb l'usuari pi i la seva contrasenya (pi:L12R18g7). De moment per a tots els usuaris creats a la raspberry es pot accedir.

## Instal·lar Jupyter Lab

    sudo -H pip3 install jupyterlab
    sudo jupyter serverextension enable --py jupyterlab --system

I modificar la configuració per a a que funcioni:
    $ sudo nano /root/jupyterhub_config.py

    c.Spawner.default_url = '/lab'

## Altres

Una opció que en principi és molt interessant és instal·lar The Littlest JupyterHub. Simplifica molt tot el provés però l'instal·lador només funciona en Ubuntu. A més sembla tenir problemes amb l'arquitectura ARM. Llàstima semblava molt interessant. S'ha descartat
També s'ha descartat l'opció de funcionar amb Docker, no hi ha versions de imatges Docker per a ARM de la raspberry pi.

## Més informació
- https://jupyterhub.readthedocs.io/en/stable/installation-guide-hard.html
- https://towardsdatascience.com/setup-your-home-jupyterhub-on-a-raspberry-pi-7ad32e20eed
- https://stackoverflow.com/questions/55132540/jupyterlab-on-jupyterhub
