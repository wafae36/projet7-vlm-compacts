# Petits modèles vision-langage : légender et juger des images

*Projet 7 du cours, VLMs légers.*

Projet réalisé par Wafae, Meriem et Fatima.

## Le projet

On compare deux petits modèles vision-langage, Qwen2-VL-2B et SmolVLM, sur les mêmes images tirées de Flickr8k. Chaque modèle est testé en précision normale (16 bits), puis quantifié en 8 bits et en 4 bits, pour voir ce qu'on gagne en mémoire et ce qu'on perd en qualité.

On s'en sert de deux façons :

- **Légender les images.** On compare les légendes produites à celles écrites par des humains, puis on garde les meilleures pour constituer un jeu de données qui pourra servir à entraîner une LoRA.
- **Juger des légendes.** Le modèle donne une note de 1 à 5, et on regarde si ses notes rejoignent les nôtres.

Le projet se termine par une petite démo : on charge une image et on obtient une légende ou un score, en choisissant le niveau de quantification.

## Organisation du dépôt

```
notebooks/
  01_donnees_generation.ipynb   Partie 1 : images, modèles en 16, 8 et 4 bits, légendes, mémoire et vitesse
  02_evaluation_lora.ipynb      Partie 2 : métriques, graphiques, jeu de données pour la LoRA
  03_juge_demo.ipynb            Partie 3 : le modèle comme juge, corrélations, démo Gradio
  04_projet_complet.ipynb       Les trois parties réunies
results/                        Tableaux et graphiques
docs/                           Fiches (modèles, métriques, limites)
demo/                           Vidéo de la démo
```

La répartition détaillée des tâches est suivie dans l'issue « Répartition des tâches ».

## Lancer les notebooks

Les notebooks tournent sur Google Colab avec un GPU T4 (*Exécution → Modifier le type d'exécution*). Il faut les lancer dans l'ordre 01, 02, 03, car chaque partie utilise les résultats de la précédente.

Les images et les résultats intermédiaires sont stockés dans un dossier Google Drive partagé, `projet7_vlm`. Pour que nos résultats restent comparables, on garde toutes les mêmes réglages : `SEED = 42`, `N_IMAGES = 300` et `MAX_SIDE = 512`.
