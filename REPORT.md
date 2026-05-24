# Informe de Análisis y Mejoras del Repositorio - University-app

Este informe detalla el contenido actual del repositorio, identifica vulnerabilidades de seguridad y propone mejoras tanto en el ámbito de seguridad como en el de desarrollo.

## 1. Contenido del Repositorio

El proyecto es una aplicación web de gestión de citas médicas para el "Hospital Local de Puerto López", construida con el framework **Flask** de Python.

### Estructura de Archivos:
- `app.py`: El punto de entrada principal de la aplicación. Contiene la lógica del servidor, modelos de base de datos (SQLAlchemy) y rutas.
- `templates/`: Directorio que contiene las vistas HTML de la aplicación.
  - `citas_medicas.html`: Página principal/informativa de citas.
  - `dashboard.html`: Panel de control para usuarios autenticados.
  - `login.html`: Formulario de inicio de sesión.
  - `signup.html`: Formulario de registro de nuevos usuarios.
- `instance/`: (Generado automáticamente) Contiene la base de datos SQLite `users.db`.
- `README.md`: Archivo de documentación inicial.

---

## 2. Análisis de Seguridad

Se han identificado varias vulnerabilidades críticas que deben ser abordadas para un entorno de producción:

### 🚩 Vulnerabilidades Críticas:
1.  **Almacenamiento de Contraseñas en Texto Plano:** La aplicación guarda las contraseñas tal cual se reciben en la base de datos. Si la base de datos se ve comprometida, todas las cuentas quedarían expuestas de inmediato.
2.  **Clave Secreta Hardcodeada:** El `SECRET_KEY` está definido directamente en el código (`'clave_secreta'`). Esto facilita ataques de falsificación de sesiones.
3.  **Uso de `debug=True` en Producción:** El modo depuración está activo por defecto, lo que puede exponer trazas de error e información sensible del sistema a usuarios malintencionados.

### 🚩 Vulnerabilidades Moderadas:
1.  **Falta de Protección CSRF:** No se observa el uso de tokens CSRF en los formularios, lo que hace a la aplicación vulnerable a ataques de Cross-Site Request Forgery.
2.  **Validación de Entradas Limitada:** Aunque se usa HTML5 para validaciones básicas, no hay una validación robusta en el lado del servidor para el formato del email o la complejidad de la contraseña.

---

## 3. Mejoras Propuestas

### 🛡️ Mejoras en Seguridad:
- **Hashing de Contraseñas:** Utilizar bibliotecas como `Werkzeug` (integrada en Flask) o `Passlib` para aplicar algoritmos de hash (como PBKDF2 o BCrypt) con sal (salt) antes de guardar en la base de datos.
- **Variables de Entorno:** Mover la `SECRET_KEY` y la configuración de la base de datos a archivos `.env` para no exponerlas en el control de versiones.
- **Manejo de Sesiones Seguro:** Configurar cookies de sesión como `HttpOnly` y `Secure`.
- **Implementación de Flask-WTF:** Para gestionar formularios y añadir protección CSRF de forma sencilla.

### 🚀 Mejoras en Desarrollo:
- **Estructura de Proyecto (Blueprints):** Organizar el código en módulos (autenticación, citas, etc.) utilizando Blueprints de Flask para mejorar la escalabilidad y mantenimiento.
- **Gestión de Dependencias:** Crear un archivo `requirements.txt` para facilitar la instalación del entorno de desarrollo.
- **Migraciones de Base de Datos:** Usar `Flask-Migrate` para gestionar cambios en el esquema de la base de datos de forma profesional.
- **Pruebas Automatizadas:** Implementar tests unitarios y de integración para asegurar que los cambios no rompan la funcionalidad existente.

---

## 4. Conclusión

La aplicación actual funciona como un prototipo funcional, pero requiere una refactorización centrada en la seguridad antes de ser desplegada. El primer paso crucial es la implementación de **hashing de contraseñas**, que se llevará a cabo en esta intervención.
