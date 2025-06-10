# SWE-sf7.3 - Password Generator API

## Descripción
Este proyecto es una API REST desarrollada con Symfony 7.3 que proporciona funcionalidades para generar contraseñas seguras y gestionar archivos de contraseñas. La API expone dos endpoints principales:

- `GET /api/password/random`: Genera y devuelve una contraseña segura aleatoria
- `POST /api/password/generate-file`: Genera un archivo con 6 contraseñas seguras y lo almacena en una carpeta con la fecha actual

## Características

- Generación de contraseñas seguras con:
  - Longitud variable (entre 12 y 20 caracteres)
  - Caracteres especiales
  - Números
  - Letras mayúsculas y minúsculas
- Almacenamiento de contraseñas en archivos
- Pruebas unitarias y funcionales completas
- Documentación de endpoints
- Manejo de errores robusto

## Estructura del Proyecto

```
src/
├── Controller/
│   └── PasswordController.php
├── Service/
│   ├── PasswordGeneratorInterface.php
│   └── PasswordGeneratorService.php
└── Tests/
    ├── Controller/
    │   └── PasswordControllerTest.php
    └── Service/
        └── PasswordGeneratorServiceTest.php
```

## Desarrollo con IA
Este proyecto fue desarrollado con la ayuda de varios modelos de IA:

### Modelos Utilizados

1. **Cascade**
   - Asistente de programación principal
   - Generación de código
   - Planificación de proyecto
   - Implementación de pruebas
   - Documentación
   - Mejoras y optimizaciones

2. **GPT-4**
   - Asistencia en diseño arquitectural
   - Validación de patrones de diseño
   - Revisión de código
   - Generación de documentación técnica

3. **Claude 3**
   - Asistencia en documentación
   - Generación de ejemplos de uso
   - Revisión de pruebas
   - Validación de seguridad

### Conversación de Desarrollo
El proyecto fue desarrollado siguiendo un plan de acción detallado, que se puede encontrar en el archivo [plan_de_accion.md](plan_de_accion.md). La conversación completa de desarrollo se documenta en [resumen_conversacion.md](resumen_conversacion.md). Los modelos de IA trabajaron en conjunto para:
- Diseñar la arquitectura del proyecto
- Implementar las funcionalidades solicitadas
- Crear pruebas unitarias y funcionales
- Documentar el proyecto
- Optimizar el código
- Asegurar la calidad y seguridad del proyecto

## Requisitos

- PHP 8.3+
- Symfony 7.3
- Composer

## Instalación

1. Clonar el repositorio
2. Instalar dependencias:
   ```bash
   composer install
   ```
3. Iniciar el servidor de desarrollo:
   ```bash
   symfony server:start
   ```

## Uso

### Generar una contraseña aleatoria
```bash
GET http://localhost:8000/api/password/random
```

### Generar archivo con contraseñas
```bash
curl -X POST http://localhost:8000/api/password/generate-file
```

## Testing

El proyecto incluye pruebas unitarias y funcionales completas. Para ejecutar los tests:

```bash
composer require --dev symfony/framework-bundle
php bin/phpunit
```

## Documentación

La documentación completa del proyecto, incluyendo el plan de desarrollo y la conversación con IA, se encuentra en los siguientes archivos:
- [plan_de_accion.md](plan_de_accion.md)
- [resumen_conversacion.md](resumen_conversacion.md)

## Licencia
MIT
