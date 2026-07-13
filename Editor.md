# Gaia 2 - Editeur de fiches (living doc)

Editeur de fiche de personnage Gaia 2 (V2). Source de verite du STATUT projet.

## Statut

- 2026-07-13 : lot 1 CODE + REVIEW FAITS - 5 correctifs demandes + 2 bugs
  preexistants decouverts + 14 findings de review corriges (dont 1 bloquant
  dans l'autosave). Branche `v2` poussee. EN ATTENTE : test visuel Benoit
  (checklist transmise en conversation), puis merge master = deploiement.
- 2026-07-13 : V2 demarree dans `~/claude/Gaia2-Editor` (clone du repo deploye,
  branche `v2`).

## Contexte

- PROD (joueurs) : https://benam0u.github.io/Gaia2-Fiche_de_personnage/ - GitHub
  Pages sur master du repo `Benam0u/Gaia2-Fiche_de_personnage`. MERGE master =
  DEPLOIEMENT IMMEDIAT : ne merger qu'apres validation visuelle de Benoit.
- Original historique : `C:\Users\benoi\OneDrive\Bureau\Dev\WeakAuction\project_cursor\Projet_Weak_Auctions\JDR`
  (INTOUCHABLE, reference seulement ; identique au repo au 2026-07-13).
- App : un seul index.html (~7600 lignes, vanilla JS), wizard 8 etapes + mode
  libre + fiche imprimable. `creationState`/wizard = IIFE privee ;
  `collectSheetData`/`restoreSheetData`/`saveProfile` = top-level (DOM only).

## Lot 1 (branche v2)

1. Typo etape 7 : Points de Fatigue (PF).
2. Level Up : 1 avantage de classe GRATUIT par niveau impair atteint (hors 1),
   carte dediee etape 8, wizard + mode libre, garde a la finalisation.
3. +1 De Caracteristique : +2 bonus si deja D12 (libelle + wizard + libre + apercus).
4. Competences : colonnes Nom/Attribut/Niveau/Jet - Jet calcule (N x de de
   l'attribut, niveau 0 = "2Dx (pire)" = desavantage), rafraichi partout.
   + FIX bug preexistant : les +1 competence d'un level up en mode libre
   creaient des lignes sans inputs, perdues a la sauvegarde JSON.
5. Autosave localStorage + banniere de reprise + garde beforeunload.

## Regles metier notees

- Jet de competence : niveau N = lancer N des de l'attribut lie. Le desavantage
  (2 des, garder le pire) concerne les competences ABSENTES de la fiche : une
  competence ne s'y inscrit qu'avec >= 1 point, donc pas d'affichage niveau 0.
  Le "+1" historique semait la confusion.
- Level up : 10 pts de crea par niveau ; avantage de classe gratuit a chaque
  niveau IMPAIR (3, 5, 7...) hors niveau 1.
- Au-dela de D12 : un cran achete en Level Up vaut +2 au bonus (race : +1).
