# P.A.M - Panel de Administración Municipal (Backend API)

[![Django](https://img.shields.io/badge/Django-4.2+-092E20?style=flat&logo=django&logoColor=white)](https://www.djangoproject.com/)
[![Django REST Framework](https://img.shields.io/badge/DRF-3.14+-red?style=flat)](https://www.django-rest-framework.org/)
[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-Proprietary-red.svg)](LICENSE)

> **Nota**: Este proyecto fue desarrollado en **2023** como parte de las **prácticas profesionalizantes** en la escuela técnica. Actualmente se encuentra en fase de **mantenimiento y refactorización** para aplicar mejores prácticas de arquitectura, patrones de diseño y principios SOLID.

## 📋 Descripción

**P.A.M Backend** es una API REST desarrollada con Django y Django REST Framework que proporciona servicios backend para el sistema de gestión de arbolado urbano municipal. Este proyecto forma parte de un sistema completo que permite a las autoridades municipales registrar, monitorear y gestionar el arbolado público de la ciudad.

## 🎯 Propósito del Proyecto

Este proyecto fue creado como una solución práctica para:
- Digitalizar el registro de árboles urbanos
- Facilitar el seguimiento del estado del arbolado público
- Proporcionar datos georreferenciados para análisis municipal
- Gestionar el mantenimiento preventivo y correctivo de árboles
- Documentar el estado de veredas y elementos urbanos relacionados

## ✨ Características Principales

### Funcionalidades Core
- ✅ **Autenticación basada en tokens** (Django REST Framework Token Authentication)
- ✅ **CRUD completo de árboles** con información detallada
- ✅ **Geolocalización** mediante coordenadas (latitud/longitud)
- ✅ **Gestión de relaciones** (especies, estados, detalles de área)
- ✅ **Sistema de usuarios** con registro y login
- ✅ **API RESTful** con endpoints documentados

### Modelos de Datos
- **Arbolado**: Registro principal con información completa del árbol
- **Arbol_especie**: Catálogo de especies arbóreas
- **Arbol_estado**: Estados del árbol (bueno, regular, malo, etc.)
- **Vereda_estado**: Condición de la vereda circundante
- **Arbol_area_detalles**: Detalles específicos del área donde se encuentra

## 🛠️ Stack Tecnológico

| Tecnología | Versión | Propósito |
|------------|---------|-----------|
| **Python** | 3.8+ | Lenguaje base |
| **Django** | 4.2+ | Framework web |
| **Django REST Framework** | 3.14+ | API REST |
| **SQLite** | 3.x | Base de datos (desarrollo) |
| **django-cors-headers** | - | Manejo de CORS |
| **python-decouple** | - | Gestión de configuración |

## 📦 Instalación

### Prerrequisitos
- Python 3.8 o superior
- pip (gestor de paquetes de Python)
- Git

### Pasos de Instalación

1. **Clonar el repositorio**
```bash
git clone https://github.com/neocizee/P.A.M.git
cd P.A.M
```

2. **Crear entorno virtual**
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Linux/Mac
python3 -m venv venv
source venv/bin/activate
```

3. **Instalar dependencias**
```bash
pip install -r requirements.txt
```

4. **Configurar variables de entorno** (opcional)
```bash
# Crear archivo .env en la raíz del proyecto
# Agregar configuraciones sensibles
SECRET_KEY=tu-secret-key-aqui
DEBUG=True
```

5. **Ejecutar migraciones**
```bash
python manage.py migrate
```

6. **Crear superusuario** (opcional)
```bash
python manage.py createsuperuser
```

7. **Ejecutar servidor de desarrollo**
```bash
python manage.py runserver
```

La API estará disponible en: `http://127.0.0.1:8000/`

## 🚀 Uso

### Endpoints Principales

| Método | Endpoint | Descripción | Autenticación |
|--------|----------|-------------|---------------|
| POST | `/api/login` | Iniciar sesión | No |
| POST | `/api/signup` | Registrar usuario | No |
| GET | `/api/testToken` | Verificar token | Sí |
| GET | `/api/arboles` | Listar todos los árboles | Sí |
| POST | `/api/agregarArbol` | Agregar nuevo árbol | Sí |
| POST | `/api/editarArbol` | Editar árbol existente | Sí |
| POST | `/api/borrarArbol` | Eliminar árbol | Sí |
| GET | `/api/listaAForeign` | Obtener datos relacionados | Sí |

### Ejemplos de Uso

Ver el archivo `test.rest` para ejemplos completos de peticiones HTTP.

#### Login
```http
POST http://127.0.0.1:8000/api/login
Content-Type: application/json

{
  "username": "usuario",
  "password": "contraseña"
}
```

#### Agregar Árbol
```http
POST http://127.0.0.1:8000/api/agregarArbol
Content-Type: application/json
Authorization: Token YOUR_TOKEN_HERE

{
  "maps_long": 35.123132,
  "maps_lat": 45.12312321,
  "observacion": "Árbol en buen estado",
  "altura_calle": 150,
  "nombre_calle": "Salta",
  "ancho_vereda": 4.45,
  "altura_aprox": 6,
  "circurns": 0.18,
  "diametro": 0.06,
  "tiene_clavel": true,
  "vereda_damaged": false,
  "vereda_levantada": false,
  "element_rare": false,
  "element_rare_type": "",
  "element_rare_desc": "",
  "activo": true,
  "arbol_area_detalles": 1,
  "arbol_especie": 1,
  "arbol_estado": 1,
  "vereda_estado": 1
}
```

## 📊 Estructura del Proyecto

```
P.A.M/
├── arbolado/              # Configuración principal del proyecto Django
│   ├── settings.py        # Configuración de Django
│   ├── urls.py            # URLs principales
│   └── wsgi.py            # Configuración WSGI
├── arb_datos/             # Aplicación principal
│   ├── models.py          # Modelos de datos
│   ├── views.py           # Vistas/Controladores
│   ├── serializers.py     # Serializadores DRF
│   ├── urls.py            # URLs de la app
│   └── migrations/        # Migraciones de base de datos
├── db.sqlite3             # Base de datos SQLite
├── manage.py              # Script de gestión Django
├── requirements.txt       # Dependencias del proyecto
└── test.rest              # Ejemplos de peticiones HTTP
```

## ⚠️ Consideraciones Importantes

### Estado del Proyecto

Este proyecto fue desarrollado en **2023 con fines educativos** durante las prácticas profesionalizantes. Como tal, **no implementa todas las mejores prácticas de ingeniería de software** que se esperarían en un proyecto de producción.

**Aspectos no implementados:**
- ❌ Tests automatizados
- ❌ Configuración de seguridad para producción
- ❌ Arquitectura en capas / Clean Architecture
- ❌ Principios SOLID aplicados consistentemente
- ❌ Validaciones robustas en todos los endpoints
- ❌ Manejo avanzado de errores

## 🤝 Contribuciones

Este es un proyecto personal en proceso de refactorización. Sin embargo, sugerencias y feedback son bienvenidos.

## 📝 Licencia

Este proyecto está bajo una **Licencia Propietaria**. 
- Se puede ver el código con fines educativos y de portfolio
- Se puede estudiar el código para aprendizaje
- No se permite uso comercial
- No se permite distribución o venta
- No se permite crear trabajos derivados sin permiso

### Uso Comercial
Para licencias comerciales, uso empresarial o SaaS, por favor contacta al autor.
Ver el archivo [LICENSE](LICENSE) para más detalles.

## 👨‍💻 Autor

**neocizee**
- GitHub: [@neocizee](https://github.com/neocizee)

## 🎓 Contexto Académico

Este proyecto fue desarrollado como parte de las **prácticas profesionalizantes** en una escuela técnica durante el año 2023. Representa un hito importante en mi aprendizaje de desarrollo web y arquitectura de software.

## 🏠 Home Lab

Este proyecto está disponible en mi home lab como parte de mi portafolio de desarrollo. Puede ser utilizado como referencia de evolución técnica y aprendizaje continuo.

---

**Nota**: Este README será actualizado conforme se implementen las mejoras y refactorizaciones planificadas.
