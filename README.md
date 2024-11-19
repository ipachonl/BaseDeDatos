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
SELECT Name from country where Name like '%Republic%';
```

![image](https://github.com/user-attachments/assets/ee99b280-e944-4ef1-8111-160309529f0e)

**8. Listar los 5 países más poblados**

**Álgebra relacional**:  

$$
\pi_{\text{Name, Population}}(\text{Country}) \text{ ORDER BY Population DESC LIMIT 5}
$$

**SQL equivalente**:  
```sql
SELECT Name, Population FROM city order by Population desc limit 5;
```

![image](https://github.com/user-attachments/assets/7e617628-6c41-45c8-9ebf-23965b54d2b4)


**9. Calcular la población promedio de los países en el continente 'Europe'**

**Álgebra relacional**:  

$$
\text{AVG}(\pi_{\text{Population}}(\sigma_{\text{Continent} = 'Europe'}(\text{Country})))
$$

**SQL equivalente**:  
```sql
SELECT AVG(Population) 
FROM country
WHERE Continent = 'Europe'; 

```

![image](https://github.com/user-attachments/assets/b6f75f3c-84c3-4f2e-aef3-3bc6bcffd383)

**10. Selección de idiomas con más del 10% de la población mundial que los habla**

**Álgebra relacional**:  

$$
\sigma_{\text{Percentage} > 10}(\text{CountryLanguage})
$$

**SQL equivalente**:  
```sql
SELECT *  
FROM CountryLanguage  
WHERE Percentage > 10 ; 
```

![image](https://github.com/user-attachments/assets/1b6d20c9-e31a-4bf2-90ae-67c59a65ab0e)

## Consultas de Nivel Medio

**1. Encontrar los 5 países más poblados por continente**

**Álgebra relacional**:  

$$
\pi_{\text{Name, Population}}(\text{Country}) \text{ GROUP BY Continent ORDER BY Population DESC LIMIT 5}
$$

**SQL equivalente**:  
```sql
SELECT Continent, Name, Population FROM country AS c
WHERE Population = (SELECT MAX(Population)
    FROM country
    WHERE Continent = c.Continent)
ORDER BY Population DESC LIMIT 5;
```

![image](https://github.com/user-attachments/assets/5a76f296-a4b2-47c7-99ec-215b9f071d98)

**2. Listar países que usan más de un idioma**

**Álgebra relacional**:  

$$
\sigma_{\text{count(Language)} > 1}(\text{CountryLanguage GROUP BY CountryCode})
$$

**SQL equivalente**:  
```sql
SELECT c.Name AS CountryName, cl.Language
FROM country c
JOIN countrylanguage cl ON c.Code = cl.CountryCode
WHERE c.Code IN (
    SELECT CountryCode
    FROM countrylanguage
    GROUP BY CountryCode
    HAVING COUNT(Language) > 1
);
```

![image](https://github.com/user-attachments/assets/f100e74a-8899-4631-a480-1d4e79a5e25b)


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
# Taller: Consultas Nivel Medio

## Consultas

Aquí tienes un conjunto de preguntas de nivel medio que utilizan operaciones relacionales en MySQL aplicadas a la base de datos `world`. Cada una incluye una breve descripción del objetivo de la consulta y su formulación en álgebra relacional y en MySQL:



### 1. Encuentra los países que tienen un idioma oficial.
**Objetivo:** Identificar los países con al menos un idioma oficial registrado en la tabla `countrylanguage`.
- **Álgebra Relacional:** 
  $$\pi_{\text{CountryCode}}(\sigma_{\text{IsOfficial} = 'T'} (\text{CountryLanguage}))$$
- **Consulta en SQL:**
  ```sql
SELECT * FROM CountryLanguage;
SELECT DISTINCT CountryCode
FROM CountryLanguage
WHERE IsOfficial = 'T';
  ```
  ![image](https://github.com/user-attachments/assets/fd4bb267-fd9f-41bb-8aec-6a473fbcd999)


### 2. Lista los países que tienen más de un idioma oficial.
**Objetivo:** Identificar los países con varios idiomas oficiales.
- **Álgebra Relacional:**
  $$\pi_{\text{CountryCode}} (\sigma_{\text{IsOfficial} = 'T'} (\text{CountryLanguage}))\ \ \text{GROUP BY CountryCode HAVING COUNT(*) > 1}$$
- **Consulta en SQL:**
  ```sql
  
  ```

### 3. Encuentra los países que tienen el mismo continente que Japón.
**Objetivo:** Listar los países que comparten el mismo continente que Japón.
- **Álgebra Relacional:**
  $$\pi_{\text{Name}} (\text{Country} \bowtie_{\text{Continent} = 'Asia'} \text{Country})$$
- **Consulta en SQL:**
  ```sql
  
  ```

### 4. Encuentra las ciudades que tienen población mayor a 5 millones y están en América del Sur.
**Objetivo:** Filtrar ciudades por población y continente.
- **Álgebra Relacional:**
  $$\pi_{\text{City.Name}} (\sigma_{\text{City.Population} > 5000000 \land \text{Country.Continent} = 'South America'}(\text{City} \bowtie \text{Country}))$$
- **Consulta en SQL:**
  ```sql
  
  ```

### 5. Encuentra los países que no tienen ningún idioma oficial.
**Objetivo:** Listar los países sin idioma oficial.
- **Álgebra Relacional:**
  $$\pi_{\text{Country.Code}}(\text{Country}) - \pi_{\text{CountryCode}}(\sigma_{\text{IsOfficial} = 'T'}(\text{CountryLanguage}))$$
- **Consulta en SQL:**
  ```sql
  
  ```

### 6. Encuentra los idiomas que son oficiales en al menos dos países.
**Objetivo:** Identificar idiomas que sean oficiales en varios países.
- **Álgebra Relacional:**
  $$\pi_{\text{Language}} (\sigma_{\text{IsOfficial} = 'T'} (\text{CountryLanguage}) \ \text{GROUP BY Language HAVING COUNT(DISTINCT CountryCode) >= 2})$$
- **Consulta en SQL:**
  ```sql
  
  ```

### 7. Lista los países y su capital.
**Objetivo:** Obtener la relación entre los países y sus capitales.
- **Álgebra Relacional:**
  $$\pi_{\text{Country.Name}, \text{City.Name}} (\text{Country} \bowtie_{\text{Country.Capital} = \text{City.ID}} \text{City})$$
- **Consulta en SQL:**
  ```sql
  
  ```

### 8. Encuentra los países que tienen una población mayor que Alemania.
**Objetivo:** Comparar población con un país específico.
- **Álgebra Relacional:**
  $$\pi_{\text{Name}}(\sigma_{\text{Population} > ( \text{SELECT Population FROM Country WHERE Name = 'Germany'} ) }(\text{Country}))$$
- **Consulta en SQL:**
  ```sql
  
  ```

### 9. Encuentra los idiomas oficiales de Europa.
**Objetivo:** Listar los idiomas oficiales de países europeos.
- **Álgebra Relacional:**
  $$\pi_{\text{Language}} (\sigma_{\text{Country.Continent} = 'Europe'} (\text{Country} \bowtie \text{CountryLanguage}))$$
- **Consulta en SQL:**
  ```sql
  
  ```

### 10. Encuentra los países sin ciudades registradas en la tabla `City`.
**Objetivo:** Detectar países sin representación en la tabla de ciudades.
- **Álgebra Relacional:**
  $$\pi_{\text{Country.Code}}(\text{Country}) - \pi_{\text{CountryCode}}(\text{City})$$
- **Consulta en SQL:**
  ```sql
  
  ```

### 11. Muestra la población total de cada continente.
**Objetivo:** Calcular la población por continente.
- **Álgebra Relacional:**
  $$\pi_{\text{Continent}, \text{SUM(Population)}} (\text{Country} \ \text{GROUP BY Continent})$$
- **Consulta en SQL:**
  ```sql
  
  ```

### 12. Encuentra los países en los que la esperanza de vida es menor al promedio global.
**Objetivo:** Filtrar países con esperanza de vida baja en comparación con el promedio.
- **Álgebra Relacional:** $$\pi_{\text{Name}}(\sigma_{\text{LifeExpectancy} < \text{AVG(LifeExpectancy)}}(\text{Country}))$$
- **Consulta en SQL:**
  ```sql
  
  ```

### 13. Encuentra los países en Asia sin idioma oficial registrado.
**Objetivo:** Listar países asiáticos sin idiomas oficiales.
- **Álgebra Relacional:**
  $$\pi_{\text{Country.Code}}(\sigma_{\text{Continent} = 'Asia'} (\text{Country})) - \pi_{\text{CountryCode}}(\sigma_{\text{IsOfficial} = 'T'}(\text{CountryLanguage}))$$
- **Consulta en SQL:**
  ```sql
  
  ```

### 14. Lista los idiomas que son oficiales en países con esperanza de vida mayor a 80.
**Objetivo:** Identificar idiomas en países con alta esperanza de vida.
- **Álgebra Relacional:**
  $$\pi_{\text{Language}} (\sigma_{\text{Country.LifeExpectancy} > 80} (\text{Country} \bowtie \text{CountryLanguage}))$$
- **Consulta en SQL:**
  ```sql
  
  ```

### 15. Encuentra los países con más de 10 ciudades en la tabla `City`.
**Objetivo:** Identificar países con una gran cantidad de ciudades registradas.
- **Álgebra Relacional:**

$$ \pi_{\text{CountryCode}} (\text{City} \ \text{GROUP BY CountryCode HAVING COUNT(*) > 10}) $$

- **Consulta en SQL:**
  ```sql
  
  ```


