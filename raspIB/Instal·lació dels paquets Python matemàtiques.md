# Instal·lació dels paquets Python matemàtiques

Els paquets [SciPy](https://www.scipy.org) permeten treballar diferents aspectes de ciències i matemàtiques amb Python.

- Numpy: càlcul amb matrius i vectors multidimensionals
- Matplotlib: representació de gràfics
- IPython: widgets interactius (ja inclòs en Jupyter notebooks)
- Pandas: anàlisis de dades
- SymPy: càlcul simbòlic

## Instal·lar els diferents paquets

La instal·lació es fa en l'entorn virtual on hem instal·lat JupyterHub

```bash
sudo apt-get install libatlas-base-dev
sudo /opt/jupyterhub/bin/python3 -m pip install numpy
sudo apt-get install libopenjp2-7
sudo /opt/jupyterhub/bin/python3 -m pip install matplotlib
sudo /opt/jupyterhub/bin/python3 -m pip install pandas
sudo /opt/jupyterhub/bin/python3 -m pip install sympy
sudo /opt/jupyterhub/bin/python3 -m pip install scipy
```

## Comprovar el funcionament

```python
# Importem la llibreria numpy amb el nom np
import numpy as np
# Creació d'un vector
lista=[2,-2,1]
vector=np.array(lista)
print(vector)
#Suma
print(vector+vector)
# Producte escalar
np.dot(vector,vector)
# Matriu
M = np.array([[1, 0, -3], [2, -1, 0],[1,1,1]])
print(M)
print("Matriu inversa:")
print(np.linalg.inv(M))

import matplotlib.pyplot as plt
import numpy as np
X = np.linspace(-np.pi, np.pi, 256, endpoint=True)
C = np.cos(X)
S = np.sin(X)
plt.plot(X, C)
plt.plot(X, S)
plt.show()

import pandas as pd
dades = pd.DataFrame()
dades['alumne']=['Joan','Joaneta', 'Pep','Pepeta']
dades['nota']=[3, 5, 5, 6]
media = dades['nota'].mean()
mediana = dades['nota'].median()
moda = dades['nota'].mode()

print("""
    Media: %.2f
    Mediana: %.2f
    Moda: %.2f
""" %(media,mediana,moda))
import sympy as sp
x = sp.Symbol('x')
polinomi=sp.expand((x-4)**4)
sp.pprint(polinomi)
derivada=sp.diff(polinomi,x)
sp.pprint(derivada)
```

La comprovació s'ha fet amb un altre usuari diferent a pi. I funciona!

## Més informació

- <https://pybonacci.org/2012/06/07/algebra-lineal-en-python-con-numpy-i-operaciones-basicas/>
- <https://claudiovz.github.io/scipy-lecture-notes-ES/intro/matplotlib/matplotlib.html>
- <https://blog.adrianistan.eu/estadistica-python-media-mediana-varianza-percentiles-parte-iii>
- <http://research.iac.es/sieinvens/python-course/source/sympy.html>
