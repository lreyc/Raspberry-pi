# Muntatge d'una raspberry pi per al batxillerat internacional

## Objectiu
Instal·lar un sistema que permeti als alumnes i professors utilitzar quaderns per a programar en Python i utilitzar el programa Mathematica.

- [Instal·lació març 2021]()
- [Instal·lació JuypyterHub i Labs](https://github.com/lreyc/Raspberry-pi/blob/982fd45f730f9b71b9126f31841917e40cd124f1/Instal%C2%B7laci%C3%B3_JuypyterHub_i_Labs.md)
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
- Instal·lar paquets matemàtics a Python

## Pendent
- Notebooks d'exemple
    - Python
    - Mathematica
    - Com canviar la contrasenya
- Creació usuris professors
- Creació usuaris alumnes finals
- Eliminar usuaris
- Crear pàgina 404


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
Un exemple de feina molt semblant
- https://professorkazarinoff.github.io/jupyterhub-engr101/
- https://professorkazarinoff.github.io/jupyterhub-engr114/
