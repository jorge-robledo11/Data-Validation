# Validación de Datos con Python

## Descripción General
Este proyecto implementa un sistema de validación de datos robusto y escalable utilizando Python. Está diseñado para procesar y validar grandes conjuntos de datos de manera eficiente, empleando técnicas de paralelización para optimizar el rendimiento.

## Configuración

### Requisitos
- Python 3.12.9
- Dependencias principales:
  - pandas >= 2.2.3
  - pandera >= 0.23.1
  - joblib >= 1.4.2
- Dependencias de desarrollo:
  - jupyter >= 1.1.1

### Instalación
1. Clonar el repositorio
2. Instalar poetry si no está instalado:
```bash
pip install poetry
```
3. Instalar las dependencias:
```bash
poetry install
```

### Configuración
El proyecto utiliza poetry para la gestión de dependencias y entornos virtuales. La configuración principal se encuentra en `pyproject.toml`.

## Uso
El proyecto incluye un notebook Jupyter (`src/data_validation.ipynb`) que demuestra las principales funcionalidades:

```python
# Importar las dependencias necesarias
from pandera import Column, DataFrameSchema, Check
from joblib import Parallel, delayed

# Crear un esquema de validación
schema = DataFrameSchema({
    "column_name": Column(int, checks=[
        Check.ge(1),
        Check.is_unique()
    ])
})

# Validar datos con diferentes métodos
schema.validate(df)  # Validación completa
schema.validate(df_chunk)  # Validación por chunks
```

## Documentación de la API

### Funciones Principales

#### `validate_full()`
Realiza la validación del DataFrame completo en una sola operación.

#### `validate_sequential()`
Divide el DataFrame en chunks y realiza la validación de forma secuencial.

#### `validate_concurrent()`
Implementa validación paralela utilizando joblib para mejorar el rendimiento.

### Esquemas de Validación
El proyecto soporta validación de múltiples tipos de datos:
- Enteros con rangos específicos
- Valores flotantes con validación de rango
- Datos categóricos
- Fechas y horas
- Valores booleanos

## Desarrollo

### Estructura del Proyecto
```
.
├── data/           # Directorio para datos de prueba
├── docs/           # Documentación adicional
├── src/            # Código fuente
│   └── data_validation.ipynb
├── tests/          # Tests unitarios
├── pyproject.toml  # Configuración del proyecto
└── README.md       # Documentación principal
```

### Flujos de Trabajo Comunes
1. Generación de datos de prueba
2. Definición de esquemas de validación
3. Ejecución de validaciones
4. Análisis de resultados

## Contribución
1. Fork del repositorio
2. Crear una rama para la nueva funcionalidad (`git checkout -b feature/nueva-funcionalidad`)
3. Commit de los cambios (`git commit -am 'Añade nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Crear un Pull Request

## Licencia
Este proyecto está bajo la licencia incluida en el archivo LICENSE.

## Contacto
- **Desarrollador**: Jorge Andrés Robledo Ariza
- **Repositorio**: [GitHub](https://github.com/usuario/repo)