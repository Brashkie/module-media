# module-media

Biblioteca de contenido multimedia autoalojado para **Hepein** — infraestructura de bots de WhatsApp construida sobre [Baileys](https://github.com/WhiskeySockets/Baileys) y librerías compatibles.

Este repositorio contiene todas las imágenes, GIFs y videos usados por comandos de roll/gacha, tarjetas de información de personajes, banners, wallpapers y comandos de reacción — para que los bots no dependan de APIs de imágenes de terceros que pueden caerse o limitar peticiones.

> 🇬🇧 Looking for the English version? See [README.md](README.md).

## Contexto

`module-media` es una de las dos mitades en las que se dividió el monorepo original [`module`](https://github.com/Brashkie/module) (la *Hepein Multimedia API*). Ese proyecto se separó en dos repositorios independientes con actualizaciones propias:

- **[module-data](https://github.com/Brashkie/module-data)** — datasets JSON versionados (estadísticas de personajes, entradas de Pokédex, listas de dragones, etc.)
- **module-media** (este repo) — las imágenes, GIFs y videos a los que apuntan esos datasets

Los datasets en `module-data` referencian archivos de este repositorio por nombre/ruta, por lo que ambos repositorios están pensados para usarse juntos.

## Estructura del repositorio

```
module-media/
├── anime/
│   ├── img/name/        # ~2,150 retratos de personajes (roll/gacha, tarjetas de info)
│   ├── gif/             # reservado para contenido animado de anime
│   └── vid/role/        # videos de reacción, agrupados por acción:
│       ├── cry/  kill/  kiss/  kisscheeks/
│       └── laugh/  pat/  punch/  sad/  sleep/
├── banner/
│   ├── animated/        # 100 GIFs de banner numerados (000001–000100)
│   ├── img/  header/  footer/  vid/   # estructura reservada, contenido pendiente
├── desktop-wallpaper/
│   └── img/             # fotos de wallpaper seleccionadas (origen Pexels)
├── dragoncity/
│   ├── img/name/        # una carpeta por dragón (~2,100 dragones)
│   ├── anim/name/       # una carpeta por dragón, variante animada (~580)
│   └── vid/name/        # una carpeta por dragón, variante en video (~580)
├── header/
│   └── img/  vid/       # estructura reservada, contenido pendiente
├── line/
│   └── animated/        # GIFs animados de línea/separador
├── marvel/
│   ├── img/name/        # set de personajes pequeño/pendiente
│   ├── img/code/        # set de imágenes numeradas
│   ├── img/staff/       # set principal de personajes (~850 archivos, varias imágenes por personaje)
│   └── vid/             # estructura reservada, contenido pendiente
└── pokemon/
    ├── img/cards/  img/normal/   # estructura reservada, contenido pendiente
    └── vid/                       # estructura reservada, contenido pendiente
```

### Convenciones de nombres

- Los archivos de personajes se nombran según el personaje (`akane-kurokawa.png`), con variantes numeradas para imágenes extra del mismo personaje (`akane-kurokawa-2.jpg`, `-3`, `-4`...).
- `dragoncity/` usa **una subcarpeta por dragón** (en lugar de archivos planos) para que cada dragón pueda tener varias imágenes/animaciones/videos.
- Los videos de reacción en `anime/vid/role/` están agrupados en carpetas por acción, coincidiendo con comandos del bot como `cry`, `kiss`, `pat`, `sleep`, etc.

### Sobre los archivos `prueba.js`

Los archivos `prueba.js` vacíos dentro de carpetas por lo demás vacías (p. ej. `pokemon/img/cards/`, `header/vid/`) son marcadores de posición (placeholders). Git no rastrea directorios vacíos, así que estos archivos mantienen la estructura de carpetas para contenido planeado que aún no se ha subido.

## Estado del contenido

No todas las categorías están terminadas. Las carpetas se agrupan en tres estados:

| Estado | Significado |
|---|---|
| ✅ Completo | Contenido multimedia real y utilizable (p. ej. `anime/img/name`, `dragoncity`, `banner/animated`, `marvel/img/staff`) |
| 🚧 Parcial | Existe algo de contenido pero el set está incompleto (p. ej. `marvel/img/name`) |
| ⬜ Reservado | La carpeta existe, la estructura está reservada, aún sin contenido (p. ej. `pokemon/*`, `header/*`, la mayoría de `banner/*`) |

## Uso

Este repositorio está pensado para ser consumido por un bot (o por `module-data`) como submódulo de git, o clonado junto a él y referenciado por ruta relativa — p. ej. `module-media/anime/img/name/<slug>.png`.

```bash
git clone https://github.com/Brashkie/module-media.git
```

## Política de contenido

Todo el contenido de este repositorio es apto para todo público (SFW). No se almacena material NSFW ni restringido por edad.

## Contribuir

Las contribuciones de nuevas imágenes de personajes, banners o media de reacción son bienvenidas. Por favor:

1. Respeta la convención de nombres existente para la categoría a la que agregas contenido.
2. Optimiza/reduce el tamaño de las imágenes antes de subirlas.
3. No agregues contenido NSFW ni restringido por edad.

## Licencia

Consulta al propietario del repositorio los términos de licencia para contenido de personajes/media de terceros.
