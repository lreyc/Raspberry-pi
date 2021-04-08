# Muntatge d'una raspberry pi per al batxillerat internacional

## Objectiu
Instal·lar un sistema que permeti als alumnes i professors utilitzar quaderns per a programar en Python i utilitzar el programa Mathematica.

- [Instal·lació març 2021](.\Hola)
- Instal·lació JuypyterHub i Labs
- Reverse Proxy para Jupyter
- Instal·lar Mathematica i afegir a Jupyter Hub
- Usuaris a Jupyter Hub/Lab
- Firewall
- Redirecció de la pàgina d'inici
- Servei de correu
- Protecció del sistema
- Apagar els servidors no utilitzats
- Extensions de Jupyter Lab
- Assignar IP fixa
- Servei HTTPS

## Pendent
- Notebooks d'exemple
    - Python
    - Mathematica
    - Com canviar la contrasenya
- Creació usuris professors
- Creació usuaris alumnes finals
- Eliminar usuaris
- Crear pàgina 404
- Instal·lar paquets Python
    - Numpy
    - Pandas
    - Matplotlib
    - Scipy (càlcul simbòlic en Python)

Servei DNS dinàmic per a proves (Només proves, no entra en producció)

## Descartat

Posar jupyter lab en català.
## Accés
local
    $ ssh -l pi raspib.local
o
    $ ssh -l pi 192.168.0.2

Remot
    $ ssh -l pi -p 2202 iesalzina.xtec.cat

## Més informació
- https://professorkazarinoff.github.io/jupyterhub-engr101/
- https://professorkazarinoff.github.io/jupyterhub-engr114/
