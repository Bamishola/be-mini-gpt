# Mini-projet GPT — Génération de texte sur Molière

**École Centrale de Lyon — MSO 3.7**  
**Auteurs :** Bamishola LOKE, Mamoudou WONE  
**Enseignant :** Julien Velcin  

---

## Description

Implémentation from scratch d'un modèle de langage génératif de type GPT (décodeur Transformer),
entraîné sur le corpus des *Œuvres complètes de Molière*.  
Inspiré de [nanoGPT](https://github.com/karpathy/nanoGPT) (A. Karpathy).

---

## Contenu du dépôt
```
├── BE_miniGPT_LOKE_WONE.ipynb   # Notebook principal (entraînement + évaluation)
├── myGPTV2.py                   # Architecture myGPT (code du cours)
├── bigrammeV2.py                # Modèle Bigramme baseline (code du cours)
├── custom.py                    # Utilitaire d'affichage du modèle
├── corpus/
│   └── moliere.txt              # Corpus d'entraînement
└── rapport_miniGPT_LOKE_WONE.pdf  # Rapport final
```

---

## Modèles implémentés

- **Bigramme** — baseline sans attention (code du prof)
- **myGPT** — Transformer complet (6 couches, 8 têtes, 4.8M paramètres)
- **myGPT BPE** — myGPT avec tokenisation GPT-2 via `tiktoken` (13.7M paramètres)

---

## Stratégies de génération

| Stratégie | Description |
|---|---|
| Température | Contrôle la créativité (T < 1 = déterministe, T > 1 = créatif) |
| Top-k | Filtre les k tokens les plus probables |
| Nucleus (Top-p) | Filtre adaptatif basé sur la masse de probabilité cumulée |
| Beam Search | Explore k séquences en parallèle |

---

## Résultats

| Modèle | PPL | TTR | Hallucination |
|---|---|---|---|
| Bigramme | 11.04 | 0.90 | 81.1% |
| myGPT standard | 3.34 | 0.77 | 13.9% |
| myGPT Nucleus (p=0.95, T=0.8) | 3.34 | 0.77 | **3.6%** |
| myGPT BPE* | 21.25 | 0.90 | 10.3% |

*PPL BPE non comparable aux autres (vocabulaire différent)*

---

## Installation
```bash
pip install torch tiktoken
```

---

## Utilisation

Ouvrir `BE_miniGPT_LOKE_WONE.ipynb` sur Google Colab et exécuter les cellules dans l'ordre.  
Les checkpoints sont sauvegardés automatiquement sur Google Drive.

---

## Références

- Karpathy, A. — [Let's build GPT from scratch](https://www.youtube.com/watch?v=kCc8FmEb1nY)
- Karpathy, A. — [nanoGPT](https://github.com/karpathy/nanoGPT)
- Velcin, J. — Cours MSO 3.7, École Centrale de Lyon (2025-2026)