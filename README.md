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
SELECT Name, Continent FROM country order by Name;
```

![image](https://github.com/user-attachments/assets/197100f8-4bf4-447d-bc98-24b8446849f5)

**6. Obtener la ciudad con mayor población**

**Álgebra relacional**:  

$$
\text{MAX}(\pi_{\text{Population}}(\text{City}))
$$

**SQL equivalente**:  
```sql
SELECT Name, Population FROM city order by Population desc limit 1;
```

![image](https://github.com/user-attachments/assets/9c68f918-b464-4383-a4b1-e70663f870ea)


**7. Selección de países que tienen 'Republic' en su nombre**

**Álgebra relacional**:  

$$
\sigma_{\text{Name LIKE '%Republic%'}}(\text{Country})
$$

**SQL equivalente**:  
```sql

```



**8. Listar los 5 países más poblados**

**Álgebra relacional**:  

$$
\pi_{\text{Name, Population}}(\text{Country}) \text{ ORDER BY Population DESC LIMIT 5}
$$

**SQL equivalente**:  
```sql

```

![image](https://github.com/user-attachments/assets/7e617628-6c41-45c8-9ebf-23965b54d2b4)


**9. Calcular la población promedio de los países en el continente 'Europe'**

**Álgebra relacional**:  

$$
\text{AVG}(\pi_{\text{Population}}(\sigma_{\text{Continent} = 'Europe'}(\text{Country})))
$$

**SQL equivalente**:  
```sql

```



**10. Selección de idiomas con más del 10% de la población mundial que los habla**

**Álgebra relacional**:  

$$
\sigma_{\text{Percentage} > 10}(\text{CountryLanguage})
$$

**SQL equivalente**:  
```sql

```



## Consultas de Nivel Medio

**1. Encontrar los 5 países más poblados por continente**

**Álgebra relacional**:  

$$
\pi_{\text{Name, Population}}(\text{Country}) \text{ GROUP BY Continent ORDER BY Population DESC LIMIT 5}
$$

**SQL equivalente**:  
```sql

```

**2. Listar países que usan más de un idioma**

**Álgebra relacional**:  

$$
\sigma_{\text{count(Language)} > 1}(\text{CountryLanguage GROUP BY CountryCode})
$$

**SQL equivalente**:  
```sql

```

**3. Calcular el total de población de cada continente**

**Álgebra relacional**:  

$$
\pi_{\text{Continent}, \text{SUM(Population)}}(\text{Country}) \text{ GROUP BY Continent}
$$

**SQL equivalente**:  
```sql

```

**4. Contar el número de ciudades en cada país**

**Álgebra relacional**:  

$$
\pi_{\text{CountryCode}, \text{COUNT(*)}}(\text{City}) \text{ GROUP BY CountryCode}
$$

**SQL equivalente**:  
```sql

```

**5. Listar los países y su promedio de vida ordenados por el promedio de vida en orden descendente**

**Álgebra relacional**:  

$$
\pi_{\text{Name}, \text{LifeExpectancy}}(\text{Country}) \text{ ORDER BY LifeExpectancy DESC}
$$

**SQL equivalente**:  
```sql

```

**6. Selección de ciudades cuya población está entre 500,000 y 1,000,000**

**Álgebra relacional**:  

$$
\sigma_{500000 \leq \text{Population} \leq 1000000}(\text{City})
$$

**SQL equivalente**:  
```sql

```

**7. Listar los idiomas hablados en países donde la población es mayor a 50 millones**

**Álgebra relacional**:  

$$
\pi_{\text{Language}}(\sigma_{\text{Population} > 50000000}(\text{Country}) \bowtie \text{CountryLanguage})
$$

**SQL equivalente**:  
```sql

```

**8. Calcular el promedio de población por ciudad en cada país**

**Álgebra relacional**:  

$$
\pi_{\text{CountryCode}, \text{AVG(Population)}}(\text{City}) \text{ GROUP BY CountryCode}
$$

**SQL equivalente**:  
```sql

```

**9. Seleccionar los países cuya calificación de vida está por encima del promedio mundial**

**Álgebra relacional**:  

$$
\sigma_{\text{LifeExpectancy} > \text{AVG(LifeExpectancy)}}(\text{Country})
$$

**SQL equivalente**:  
```sql

```

**10. Encontrar los continentes con una calificación de vida superior al promedio de su continente**

**Álgebra relacional**:  

$$
\pi_{\text{Continent, AVG(LifeExpectancy)}}(\text{Country}) \text{ GROUP BY Continent}
$$

**SQL equivalente**:  
```sql

```



