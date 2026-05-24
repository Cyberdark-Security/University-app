# 🏥 Hospital Local de Puerto López - Gestión de Citas Médicas

![Flask](https://img.shields.io/badge/flask-%23000.svg?style=for-the-badge&logo=flask&logoColor=white)
![SQLite](https://img.shields.io/badge/sqlite-%2307405e.svg?style=for-the-badge&logo=sqlite&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

Bienvenido a la plataforma oficial de **Gestión de Citas Médicas** del Hospital Local de Puerto López. Una aplicación diseñada para facilitar el acceso a la salud de manera digital, segura y eficiente.

---

## 🌟 Características Principales

- **🔐 Seguridad Avanzada:** Implementación de hashing de contraseñas para proteger la privacidad de los usuarios.
- **📅 Gestión de Citas:** Interfaz intuitiva para que los pacientes puedan encontrar a su médico ideal.
- **🖥️ Panel de Control:** Dashboard personalizado para usuarios registrados.
- **📱 Diseño Responsivo:** Accesible desde cualquier dispositivo móvil o de escritorio.

---

## 🛠️ Tecnologías Utilizadas

El proyecto está construido con un stack moderno y eficiente:

- **Backend:** [Flask](https://flask.palletsprojects.com/) (Python)
- **Base de Datos:** SQLite con [SQLAlchemy](https://www.sqlalchemy.org/)
- **Seguridad:** Werkzeug Security para hashing (PBKDF2)
- **Frontend:** HTML5, CSS3 y Jinja2 Templates

---

## 🚀 Instalación y Uso

Sigue estos pasos para ejecutar el proyecto localmente:

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/tu-usuario/university-app.git
   cd university-app
   ```

2. **Crear un entorno virtual:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # En Windows: venv\Scripts\activate
   ```

3. **Instalar dependencias:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Ejecutar la aplicación:**
   ```bash
   python app.py
   ```

5. **Acceder al sitio:**
   Abre tu navegador en `http://127.0.0.1:5000`

---

## 🛡️ Mejoras de Seguridad Recientes

Hemos realizado una auditoría y refactorización del código para garantizar la seguridad de los datos:
- **Hashing de Contraseñas:** Ya no almacenamos contraseñas en texto plano. Utilizamos `generate_password_hash`.
- **Validación de Sesiones:** Sistema robusto de gestión de sesiones de usuario.
- **Consultas Seguras:** Uso de SQLAlchemy ORM para prevenir inyecciones SQL.

> 📝 **Nota:** Para más detalles, consulta el [Informe de Seguridad](REPORT.md) detallado.

---

## 🤝 Contribuciones

¿Quieres mejorar este proyecto? ¡Las contribuciones son bienvenidas!
1. Haz un Fork del proyecto.
2. Crea una rama para tu mejora (`git checkout -b feature/MejoraIncreible`).
3. Haz un commit de tus cambios (`git commit -m 'Añadir nueva funcionalidad'`).
4. Sube tu rama (`git push origin feature/MejoraIncreible`).
5. Abre un Pull Request.

---

Desarrollado con ❤️ para la comunidad de Puerto López.
