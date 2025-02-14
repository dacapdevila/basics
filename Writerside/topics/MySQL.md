# MySQL

### Iniciar y detener MySQL

Para inicializar el servicio:

``` bash
    brew services start mysql
```


Para detener el servicio:
``` bash
    brew services stop mysql
```

Para reiniciar el servicio:
``` bash
    brew services restart mysql
```

### Conectarse a MySQL

``` bash
    mysql -u root -p
```

Ejemplo:

``` bash
    mysql -u velocity_admin -p
    mysql -u content_creator_toolkit_admin -p
    
    // then:
    xDZdY93Yvppx3aZ6Qak3
```

Si se usa desde Laravel Sail:

``` bash
    ./vendor/bin/sail mysql
```

### Listar base de datos

``` SQL
    SHOW DATABASES;
```

### Crear una base de datos

``` SQL
    CREATE DATABASE nombre_base_de_datos;
```

Si la creacion debe hacerse con el charset utf8mb4 (recomendado para Laravel)

``` SQL
    CREATE DATABASE nombre_base_de_datos CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

### Usar una base de datos

```SQL
    USE nombre_base_de_datos;
```

### Eliminar base de datos

```SQL
    DROP DATABASE nombre_base_de_datos;
```

### Ver tablas dentro de una base de datos

```SQL
    SHOW TABLES;
```

### Ver la estructura de una tabla

```SQL
    DESCRIBE nombre_tabla;
    // o
    SHOW COLUMNS FROM nombre_tabla;
```

### Insertar datos en una tabla

```SQL
    INSERT INTO users (name, email, password) VALUES ('Dario', 'dario@example.com', '123456');
```

### Consultar datos en una tabla

```SQL
    SELECT * FROM users;
    // o
    SELECT * FROM users WHERE email = 'dario@example.com';
```

### Actualizar datos

```SQL
    UPDATE users SET name = 'Dario Capdevila' WHERE email = 'dario@example.com';
```


### Eliminar datos

```SQL
    DELETE FROM users WHERE email = 'dario@example.com';
```

para vaciar la tabla sin eliminar la estructura

```SQL
    TRUNCATE TABLE users;
```

### Salir de MySQL

```SQL
    exit;
```

### Crear un usuario MySQL para Laravel

Por cuestiones de seguridad, es recomendable crear un usuario especifico en lugar de usar `root`.

```SQL
    CREATE USER 'laravel'@'localhost' IDENTIFIED BY 'contraseña_segura';
```

Ejemplo:

```SQL
    CREATE USER 'content_creator_toolkit_admin'@'localhost' IDENTIFIED BY 'oz6bLN9BPLpAXH63kzJF';
```

Luego es importante dar permisos al usuario:

```SQL
    GRANT ALL PRIVILEGES ON nombre_base_de_datos.* TO 'laravel'@'localhost';
```

Ejemplo:

```SQL
    GRANT ALL PRIVILEGES ON content_creator_toolkit_db.* TO 'content_creator_toolkit_admin'@'localhost';
```

Por ultimo, actualizar los priviligios:

```SQL
    FLUSH PRIVILEGES;
```

### Respaldar y restaurar bases de datos

Exportar una base de datos:

```SQL
    mysqldump -u root -p nombre_base_de_datos > backup.sql
```

Importar una base de datos:

```SQL
    mysql -u root -p nombre_base_de_datos < backup.sql
```

### Resetear la base de datos en Laravel

Si se necesita borrar y recrear todas las tablas en Laravel

```bash
    php artisan migrate:fresh
```

Si ademas queres insertar datos de pruebas

```bash
    php artisan migrate:fresh --seed
```