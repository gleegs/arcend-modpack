# 🌌 Arcend Modpack

Bienvenue sur le dépôt officiel du modpack **Arcend**. Ce pack est basé sur la base solide de **All The Mods (ATM)**, enrichie de mods personnalisés pour offrir une expérience unique sur notre serveur.

Ce projet utilise [Packwiz](https://packwiz.infra.link/), un outil de gestion de modpack moderne qui permet de synchroniser parfaitement les fichiers entre le serveur et les joueurs.

## 🚀 Installation rapide

### 💻 Pour les Joueurs (Client)

Si vous utilisez notre launcher personnalisé, la mise à jour est **automatique**.
Sinon, vous pouvez installer le pack manuellement via le **Packwiz Installer** :

1. Téléchargez le [Packwiz Installer Bootstrap](https://www.google.com/search?q=https://github.com/packwiz/packwiz-installer-bootstrap/releases).
2. Utilisez l'URL suivante pour la synchronisation :
   `https://gleegs.github.io/arcend-modpack/pack.toml`
3. Lancez la commande suivante dans votre dossier d'instance :

```bash
java -jar packwiz-installer-bootstrap.jar https://gleegs.github.io/arcend-modpack/pack.toml

```

### 🗄️ Pour l'Administrateur (Serveur Docker)

Ce modpack est nativement compatible avec l'image Docker de `itzg`. Ajoutez simplement ces variables d'environnement à votre `docker-compose.yml` :

```yaml
services:
  mc:
    image: itzg/minecraft-server
    environment:
      TYPE: "NEOFORGE" # Ou NEOFORGE selon la version
      VERSION: "1.21.1" # À adapter
      PACKWIZ_URL: "https://gleegs.github.io/arcend-modpack/pack.toml"
      EULA: "TRUE"
    ports:
      - "25565:25565"
```

---

## 🛠️ Maintenance du Modpack

### Ajouter un mod

Pour ajouter un nouveau mod (ex: depuis Modrinth), utilisez la console à la racine du projet :

```bash
packwiz modrinth install [NOM_DU_MOD]
# ou
packwiz curseforge install [NOM_DU_MOD]

```

N'oubliez pas de spécifier si le mod est côté client uniquement (`--client-only`) ou serveur uniquement (`--server-only`) si nécessaire.

### Mettre à jour All The Mods

Pour synchroniser les mises à jour de la base ATM :

```bash
packwiz curseforge import chemin/vers/ALL-THE-MODS-NOUVELLE-VERSION.zip

```

### Publier les changements

Après chaque modification, mettez à jour l'index et poussez sur GitHub :

```bash
packwiz refresh
git add .
git commit -m "Mise à jour des mods"
git push

```

_Le serveur et les clients détecteront automatiquement les changements au prochain redémarrage._

---

## 📂 Structure du projet

- `pack.toml` : Configuration globale du modpack.
- `index.toml` : Index de tous les fichiers (généré automatiquement).
- `mods/` : Contient les fichiers `.toml` de chaque mod (les `.jar` ne sont pas stockés ici).
- `config/` : Contient les fichiers de configuration personnalisés du serveur et du client.
