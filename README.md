# Launcher — Conquête Spatiale

Launcher de l'event Minecraft **Conquête Spatiale** (1.21.1, NeoForge) : connexion Microsoft, installation et mise
à jour automatiques du modpack, puis lancement du jeu directement sur le serveur de l'event.

> Basé sur **[Selvania Launcher](https://github.com/luuxis/Selvania-Launcher) par Luuxis**, distribué sous la
> licence Luuxis v1.0 (voir [`LICENSE.md`](LICENSE.md), incluse sans modification) : code source public,
> crédit de l'auteur original, aucun usage commercial.

## Modifications par rapport à Selvania

- Identité visuelle de l'event (couleurs, fonds d'écran, icône, textes d'accueil).
- Adresses du backend avec barre finale (`config/`, `articles/`, `instances/`) : fonctionne derrière nginx sans règle de réécriture.
- `LAUNCHER_URL` (variable d'environnement) pour pointer vers un backend de développement.
- Workflow de build déclenché manuellement (onglet Actions) au lieu de chaque push.

## Développer

```bash
npm install
npm start                                      # backend de production (package.json "url")
LAUNCHER_URL=http://localhost:8767 npm start   # backend local de développement
npm run build                                  # installeurs dans dist/
```

## Publier une version

1. Augmenter `version` dans `package.json` et pousser.
2. Onglet **Actions** → **Launcher Build** → **Run workflow** : la release est créée avec les installeurs,
   et les launchers déjà installés se mettent à jour d'eux-mêmes au démarrage.
