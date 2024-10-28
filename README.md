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

**3. Listar todos los idiomas únicos en la tabla CountryLanguage**

**Álgebra relacional**:  

$$
\pi_{\text{Language}}(\text{CountryLanguage})
$$

**SQL equivalente**:  
```sql
SELECT Language FROM countrylanguage;
```

![image](https://github.com/user-attachments/assets/23d0024a-338e-41a6-bbbb-d797ca806cd5)

**4. Selección de países con población mayor a 100 millones**

**Álgebra relacional**:  

$$
\sigma_{\text{Population} > 100000000}(\text{Country})
$$

**SQL equivalente**:  
```sql
SELECT * FROM country where Population > 100000000;
```

![image](https://github.com/user-attachments/assets/21216c1a-9e3d-4214-950a-1cc89f977fbd)

**5. Listar nombres de países y continentes ordenados alfabéticamente por nombre de país**

**Álgebra relacional**:  

$$
\pi_{\text{Name}, \text{Continent}}(\text{Country}) \text{ ORDER BY Name}
$$

**SQL equivalente**:  
```sql

```

