# module-media

Self-hosted multimedia asset library for **Hepein** — WhatsApp bot infrastructure built on [Baileys](https://github.com/WhiskeySockets/Baileys) and compatible libraries.

This repository holds every image, GIF, and video used by roll/gacha commands, character info cards, banners, wallpapers, and reaction commands — so bots don't depend on third-party image APIs that can go down or rate-limit.

> 🇪🇸 ¿Buscas la versión en español? Mira [README.es.md](README.es.md).

## Background

`module-media` is one half of a split from the original [`module`](https://github.com/Brashkie/module) monorepo (the *Hepein Multimedia API*). That project separated into two focused, independently updated repositories:

- **[module-data](https://github.com/Brashkie/module-data)** — versioned JSON datasets (character stats, Pokédex entries, dragon lists, etc.)
- **module-media** (this repo) — the images, GIFs, and videos those datasets point to

Datasets in `module-data` reference files here by name/path, so the two repos are meant to be used together.

## Repository structure

```
module-media/
├── anime/
│   ├── img/name/        # ~2,150 character portraits (roll/gacha, info cards)
│   ├── gif/             # reserved for animated anime content
│   └── vid/role/        # reaction videos, grouped by action:
│       ├── cry/  kill/  kiss/  kisscheeks/
│       └── laugh/  pat/  punch/  sad/  sleep/
├── banner/
│   ├── animated/        # 100 numbered profile/rank banner GIFs (000001–000100)
│   ├── img/  header/  footer/  vid/   # scaffolded, pending content
├── desktop-wallpaper/
│   └── img/             # curated wallpaper photos (Pexels-sourced)
├── dragoncity/
│   ├── img/name/        # one folder per dragon (~2,100 dragons)
│   ├── anim/name/       # one folder per dragon, animated variant (~580)
│   └── vid/name/        # one folder per dragon, video variant (~580)
├── header/
│   └── img/  vid/       # scaffolded, pending content
├── line/
│   └── animated/        # animated divider/separator GIFs
├── marvel/
│   ├── img/name/        # small/pending character set
│   ├── img/code/        # numbered image set
│   ├── img/staff/       # main character set (~850 files, multiple images per character)
│   └── vid/             # scaffolded, pending content
└── pokemon/
    ├── img/cards/  img/normal/   # scaffolded, pending content
    └── vid/                       # scaffolded, pending content
```

### Naming conventions

- Character files are named after the character (`akane-kurokawa.png`), with numbered variants for extra images of the same character (`akane-kurokawa-2.jpg`, `-3`, `-4`...).
- `dragoncity/` uses one **subfolder per dragon** (rather than flat files) so each dragon can hold multiple images/animations/videos.
- Reaction videos under `anime/vid/role/` are grouped into folders by action, matching bot commands like `cry`, `kiss`, `pat`, `sleep`, etc.

### About `prueba.js` files

Empty `prueba.js` files inside otherwise-empty folders (e.g. `pokemon/img/cards/`, `header/vid/`) are placeholders. Git doesn't track empty directories, so these keep the folder structure in place for content that's planned but not yet uploaded.

## Content status

Not every category is finished. Folders fall into three states:

| State | Meaning |
|---|---|
| ✅ Populated | Real, usable media (e.g. `anime/img/name`, `dragoncity`, `banner/animated`, `marvel/img/staff`) |
| 🚧 Partial | Some content exists but the set is incomplete (e.g. `marvel/img/name`) |
| ⬜ Scaffolded | Folder exists, structure is reserved, no content yet (e.g. `pokemon/*`, `header/*`, most of `banner/*`) |

## Usage

This repo is meant to be consumed by a bot (or `module-data`) as a git submodule, or cloned alongside it, then referenced by relative path — e.g. `module-media/anime/img/name/<slug>.png`.

```bash
git clone https://github.com/Brashkie/module-media.git
```

## Content policy

All content in this repository is family-friendly (SFW). No NSFW/age-restricted material is stored here.

## Contributing

Contributions of new character images, banners, or reaction media are welcome. Please:

1. Match the existing naming convention for the category you're adding to.
2. Keep images reasonably sized/optimized before committing.
3. Don't add NSFW or age-restricted content.

## License

See the repository owner for licensing terms on third-party character/media content.
