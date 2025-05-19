# Evaluacion - Mariano Casal
**Fecha:**  19/05 

---

## 📌 Actividad 1 
### Obtener el nombre de todos los usuarios mayores a 20 años de los siguientes paices; Spain, France y Turkey. ¿Cuantos son masculinos y cuantos son femeninos? -Hacer un grafico con mathplolib
```python
import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv('users.csv')

# 1. Filtrar usuarios mayores de 20 años de Spain, France y Turkey
usuarios_filtrados = df[(df['edad'] > 20) & ((df['pais'] == 'Spain') | (df['pais'] == 'France') | (df['pais'] == 'Turkey'))]

nombres = usuarios_filtrados['nombre']

conteo_genero = usuarios_filtrados['genero'].value_counts()

# 4. Crear el gráfico
plt.figure(figsize=(8, 5))
conteo_genero.plot(kind='bar', color=['green', 'blue'])  # Colores comunes para female/male
plt.title('Distribución de Género (Usuarios >20 años) de España, Francia y Turquía')
plt.xlabel('Género')
plt.ylabel('Cantidad')
plt.xticks(rotation=0)  # Etiquetas horizontales

plt.show()


```
## 📌 Actividad 2
### Obtener todos los usuarios enmtre las edades de 45 y 60, ¿Cuantos son masculinos y cuantos son femeninos? -Hacer un grafico con mathplolib
```python
import pandas as pd
import matplotlib.pyplot as plt

# Cargar los datos
df = pd.read_csv("users.csv")

# 1. Filtrar usuarios entre 45 y 60 años (inclusive)
usuarios_filtrados = df[(df["edad"] >= 45) & (df["edad"] <= 60)]
conteo_genero = usuarios_filtrados["genero"].value_counts()
conteo_genero = conteo_genero.reindex(["female", "male"]).fillna(0)  # Forzar orden

# 3. Crear el gráfico
plt.figure(figsize=(8, 5))
conteo_genero.plot(
    kind="bar", 
    color=["pink", "lightblue"], 
    edgecolor="black"
)

plt.title("Distribución de género (Usuarios 45-60 años)", fontweight="bold")
plt.xlabel("Género", fontstyle="italic")
plt.ylabel("Cantidad de usuarios", fontstyle="italic")
plt.xticks(rotation=0)

# Mostrar valores en las barras
for i, valor in enumerate(conteo_genero):
    plt.text(i, valor + 0.1, str(valor), ha="center")

plt.show()

```
