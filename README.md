# Git class

Este archivo está pensado para acompañar tu clase de Git con diagramas sencillos y explicaciones visuales. Puedes usarlo como un segundo `.md` independiente para no alterar el README original.

---

## 1. Modelo remoto / local

Local:

```
[Tu PC]
   | Working Directory
   | Staging Area
   | Local repository (HEAD)
```

Remoto:

```
[GitHub / GitLab / remoto]
   | Remote repository
   | Origin/main
```

Flujo básico:

```
[Tu PC] -- push --> [Remoto]
[Tu PC] <-- pull -- [Remoto]
```

---

## 2. `git fetch`, `git pull`, `git push`

### `git fetch`

- Trae los cambios desde el remoto.
- No modifica tu código local.

Diagrama:

```
[Remoto] -- fetch --> [Tu PC]
   (actualiza referencias remotas como origin/main)
```

### `git pull`

- Hace `fetch` + `merge` o `rebase`.
- Actualiza tu rama activa con los cambios remotos.

Diagrama:

```
[Remoto] -- pull --> [Tu PC]
   (trae cambios y los integra en tu rama local)
```

### `git push`

- Sube tus commits locales al remoto.
- Actualiza la rama remota.

Diagrama:

```
[Tu PC] -- push --> [Remoto]
   (envía commits locales a origin/main o a tu rama)
```

---

## 3. Ramas (`branches`)

Las ramas permiten trabajar en paralelo sin afectar `main`.

```
          main
            |
            o---o---o
                   \
                    feature
                     o---o---o
```

Explicación:
- `main`: línea principal.
- `feature`: rama para un cambio.
- Se puede volver a integrar con `git merge` o `git rebase`.

---

## 4. Conflictos

Ocurren cuando dos cambios modifican lo mismo en distintos lugares.

Ejemplo visual:

```
Archivo: app.js

En remoto:
  console.log("Hola desde remoto");

En local:
  console.log("Hola desde local");
```

Flujo:

1. `git pull`
2. Git detecta conflicto.
3. Editas el archivo.
4. `git add archivo`
5. `git commit`

Diagrama de decisión:

```
[git pull]
    |
    +-- sin conflicto -> listo
    |
    +-- conflicto -> resolver -> git add -> git commit
```

---

## 5. GitHub Actions / Actions

Actions permite automatizar tareas cuando sucede un evento.

Ejemplo de flujo básico:

```
[Push a main] -> [Action se ejecuta] -> [Tests / Build / Deploy]
```

Visual:

```
[Commit/push] --> [Workflow] --> [Result]
```

Acciones típicas:
- ejecutar pruebas
- revisar estilo
- desplegar código

---

## 6. Seguridad de ramas

Protege ramas importantes como `main`.

Concepto visual:

```
[main protegido]
  - no se puede pushear directo
  - requiere PR
  - requiere revisión
```

Puntos clave:
- `branch protection` en GitHub/GitLab.
- `pull request` obligatorio.
- revisión y aprobaciones.

---

## 7. Changelog

Un changelog es un registro de cambios importantes.

Estructura simple:

- `2026-06-11`: Añadido `git pull` y explicación de ramas.
- `2026-06-12`: Agregada seguridad de ramas.

Visual:

```
[Changelog]
  1. Feature
  2. Bug fix
  3. Documentación
```

---
