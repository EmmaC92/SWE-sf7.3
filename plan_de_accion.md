# Plan de Acción para Proyecto Symfony 7.3

## 1. Instalación de Symfony 7.3
- [ ] Verificar requisitos del sistema (PHP 8.2+)
- [ ] Instalar Symfony CLI si no está instalado
- [ ] Crear nuevo proyecto con: `symfony new proyecto_symfony --version=7.3 --webapp`
- [ ] Navegar al directorio del proyecto
- [ ] Verificar la instalación ejecutando el servidor de desarrollo

## 2. Configuración Inicial
- [ ] Configurar el archivo `.env` con los parámetros de la aplicación
- [ ] Actualizar dependencias con Composer
- [ ] Verificar que la estructura del proyecto sea correcta

## 3. Creación del Servicio de Contraseñas
- [ ] Crear interfaz `PasswordGeneratorInterface` en `src/Service/`
- [ ] Implementar la interfaz en `PasswordGeneratorService`
- [ ] Implementar la lógica para generar contraseñas seguras
- [ ] Registrar el servicio en `services.yaml`

## 4. Desarrollo del Controlador
- [ ] Crear `PasswordController` en `src/Controller/`
- [ ] Inyectar el servicio `PasswordGeneratorService` en el constructor
- [ ] Implementar método `getRandomPassword` (GET)
  - Devolver una contraseña aleatoria en formato JSON
- [ ] Implementar método `generateRandomPasswordFile` (POST)
  - Crear directorio con la fecha actual si no existe
  - Generar 6 contraseñas usando el servicio
  - Guardarlas en `var/generated_passwords/[fecha]/pass.txt`
  - Retornar confirmación de la operación

## 5. Configuración de Rutas
- [ ] Configurar rutas en `config/routes.yaml`
  - `GET /api/password/random` para `getRandomPassword`
  - `POST /api/password/generate-file` para `generateRandomPasswordFile`

## 6. Pruebas Manuales
- [ ] Probar el endpoint GET para obtener una contraseña
- [ ] Probar el endpoint POST para generar el archivo
- [ ] Verificar que el archivo se genera correctamente con 6 contraseñas
- [ ] Verificar el manejo de errores

## 7. Pruebas Automatizadas

### 7.1 Pruebas Unitarias
- [ ] Crear `PasswordGeneratorServiceTest` para probar el servicio de generación de contraseñas
  - [ ] Verificar que genera una contraseña con la longitud correcta
  - [ ] Verificar que la contraseña contiene al menos un número
  - [ ] Verificar que la contraseña contiene al menos una letra mayúscula
  - [ ] Verificar que la contraseña contiene al menos una letra minúscula
  - [ ] Verificar que la contraseña contiene al menos un carácter especial
  - [ ] Verificar que las contraseñas generadas son diferentes en múltiples ejecuciones

### 7.2 Pruebas Funcionales
- [ ] Crear `PasswordControllerTest` para probar los endpoints
  - [ ] Probar el endpoint GET `/api/password/random`
    - [ ] Verificar el código de respuesta 200
    - [ ] Verificar que la respuesta es un JSON válido
    - [ ] Verificar que contiene el campo 'password'
  - [ ] Probar el endpoint POST `/api/password/generate-file`
    - [ ] Verificar el código de respuesta 200
    - [ ] Verificar que se crea el archivo en la ruta correcta
    - [ ] Verificar que el archivo contiene exactamente 6 contraseñas
    - [ ] Verificar que cada contraseña cumple con los requisitos de formato
  - [ ] Probar casos de error
    - [ ] Verificar manejo de errores en la creación de directorios
    - [ ] Verificar manejo de errores en la escritura de archivos

### 7.3 Configuración de PHPUnit
- [ ] Configurar `phpunit.xml.dist` con los parámetros necesarios
- [ ] Asegurar la cobertura de código mínima requerida
- [ ] Configurar GitHub Actions o similar para ejecución automática de pruebas

## 8. Documentación
- [ ] Documentar los endpoints con OpenAPI/Swagger
- [ ] Actualizar README.md con instrucciones de uso

## 8. Despliegue (Opcional)
- [ ] Configurar entorno de producción
- [ ] Optimizar la aplicación para producción
- [ ] Desplegar en el servidor de producción

## Comandos Importantes
```bash
# Instalar dependencias
composer install

# Iniciar servidor de desarrollo
symfony server:start

# Verificar rutas disponibles
php bin/console debug:router

# Limpiar caché
php bin/console cache:clear
```

## Estructura de Archivos
```
proyecto_symfony/
├── config/
│   └── routes.yaml
├── src/
│   ├── Controller/
│   │   └── PasswordController.php
│   └── Service/
│       ├── PasswordGeneratorInterface.php
│       └── PasswordGeneratorService.php
└── var/
    └── generated_passwords/
        └── 2025-06-10/
            └── pass.txt
```

## Notas Adicionales
- Asegurarse de que el usuario del servidor web tenga permisos de escritura en `var/`
- Considerar implementar autenticación para los endpoints en producción
- Implementar validación de entrada para mayor seguridad
- Considerar agregar tests unitarios y de integración
