Cette issue répartit le travail entre les trois membres de l'équipe. Chaque partie comporte de la mise en œuvre de modèles, des expériences et de la rédaction, pour que la charge et l'intérêt soient équilibrés. Chacune coche ses tâches au fur et à mesure.

## Partie 1 : Données, modèles et quantification (Wafae)

Préparer les images et faire tourner les deux VLMs en 16, 8 et 4 bits.

- [ ] Préparer le sous-ensemble Flickr8k (300 à 500 images, redimensionnées à 512 px) dans le Drive partagé `projet7_vlm`
- [ ] Charger Qwen2-VL-2B et SmolVLM en 16 bits et vérifier qu'ils légendent correctement
- [ ] Ajouter la quantification 8 bits (LLM.int8) et 4 bits (NF4) avec `bitsandbytes`
- [ ] Premier test : SmolVLM en 16, 8 et 4 bits sur quelques images
- [ ] Générer les légendes des six configurations (2 modèles × 3 précisions) et les enregistrer dans `results/`
- [ ] Mesurer la mémoire des poids, le pic de mémoire GPU, le temps de chargement et le temps par image
- [ ] Tracer les graphiques de coût et analyser le gain de mémoire et l'effet sur la vitesse
- [ ] Extension si le temps le permet : passer à 1 000 images, ou ajouter un troisième modèle
- [ ] Notebook `01_donnees_generation` : préparation, chargement, génération, mesures
- [ ] `docs/` : fiche des modèles et de la quantification

## Partie 2 : Évaluation des légendes et jeu de données LoRA (Meriem)

Mesurer la qualité des légendes et préparer les données d'entraînement (option A).

- [ ] Implémenter BLEU-1, BLEU-4, ROUGE-L et CIDEr par rapport aux cinq légendes humaines
- [ ] Implémenter le CLIPScore (accord image ↔ légende, sans référence)
- [ ] Vérifier les métriques sur les légendes humaines : une légende contre les quatre autres, et une légende d'une autre image
- [ ] Calculer les scores des six configurations
- [ ] Mesurer la fidélité des versions 8 et 4 bits par rapport à la version 16 bits
- [ ] Graphiques de qualité et du compromis mémoire / qualité
- [ ] Choisir et commenter des exemples de légendes
- [ ] Exporter le jeu image + légende pour la LoRA (`metadata.jsonl` et un `.txt` par image)
- [ ] Extension si le temps le permet : petit entraînement LoRA sur Stable Diffusion 1.5
- [ ] Notebook `02_evaluation_lora`
- [ ] `docs/` : fiche des métriques et de leurs limites

## Partie 3 : VLM juge et démo (Fatima)

Utiliser le modèle comme juge (option B), le comparer à nos propres notes, puis montrer le tout.

- [ ] Écrire le prompt de notation de 1 à 5 et la lecture de la note dans la réponse
- [ ] Construire les paires à noter : légende humaine, légende générée, légende d'une autre image
- [ ] Mettre en place l'outil d'annotation et noter les paires (idéalement les trois membres)
- [ ] Faire noter les paires par les six configurations
- [ ] Calculer les corrélations de Spearman, Pearson et Kendall avec nos notes, et l'accord entre annotatrices
- [ ] Comparer le VLM juge au CLIPScore
- [ ] Démo Gradio : charger une image, obtenir une légende ou un score, choisir le modèle et la quantification
- [ ] Enregistrer une courte vidéo de la démo dans `demo/`
- [ ] Notebook `03_juge_demo`
- [ ] `docs/` : limites d'un VLM juge, licences des données et réflexion éthique

## Ensemble : rapport final

- [ ] Se mettre d'accord sur le plan du rapport
- [ ] Chacune rédige la section de sa partie
- [ ] Rédiger ensemble l'introduction, la discussion et la conclusion
- [ ] Compléter le README : installation, lancement des notebooks, résultats principaux
- [ ] Relecture croisée finale

## Points de coordination

- La Partie 1 fixe dès le début les réglages communs (`SEED = 42`, `N_IMAGES`, `MAX_SIDE`) et partage le dossier Drive `projet7_vlm` ; personne ne les change sans prévenir.
- Les Parties 2 et 3 n'attendent pas les légendes générées : elles commencent avec les légendes humaines de Flickr8k.
- La Partie 3 réutilise les fonctions de chargement de la Partie 1 et le CLIPScore de la Partie 2.
- Les images, les modèles et les gros fichiers restent sur le Drive ; seuls les notebooks, les tableaux et les graphiques vont sur GitHub.
- Chacune travaille sur sa propre branche et ouvre une pull request vers `main`.
