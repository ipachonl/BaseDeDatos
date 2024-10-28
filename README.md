# BasesDeDatos
## Consultas Básicas

**1. Selección de países en el continente 'Asia'**

**Álgebra relacional**:

$$
\sigma_{\text{Continent} = 'Asia'}(\text{Country})
$$

**SQL equivalente**:

```sql
SELECT * FROM country WHERE Continent = 'Asia';
```


![Captura de pantalla 2024-10-28 183238](https://github.com/user-attachments/assets/a16af567-31b6-44a2-98ec-1944cc759ed9)

**2. Contar el número total de ciudades**

**Álgebra relacional**:  

$$
\text{COUNT}(\text{City})
$$

**SQL equivalente**:  
```sql
SELECT distinct count(Name)
FROM city;
```

![image](https://github.com/user-attachments/assets/3dcc8021-7434-4420-8597-a3849e397776)
