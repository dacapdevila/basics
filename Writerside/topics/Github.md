# Github

### Generar SSH

```Bash
    ssh-keygen -t ed25519 -C "ejemplo@email.com"
```

### Copiar la clave publica

```bash
    cat ~/.ssh/id_ed25519.pub
```

### Agregar la clave publica a Github

- Ir a `GitHub` -> `Settings` -> `SSH and GPG Keys`.

- Hacer clic en `New SSH Key`.

- Pegar la clave copiada y guardar los cambios.

### Probar la conexion

```bash
    ssh -T git@github.com
```

### Luego ya se puede clonar los repos

```bash
    git clone git@github.com:usuario/repositorio.git
```