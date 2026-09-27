# Swipe & Sache

Le tinder de l'info. Tu donnes un thème (« apprends-moi des mots en espagnol », « les nouvelles du sport »…), Claude génère des cartes courtes, tu swipes à droite ce qui t'intéresse, et chaque « j'aime » renforce ce genre d'info dans les cartes suivantes.

Page : https://charlesninane94.github.io/swipe-et-sache/

## Fonctionnement

- Profil utilisateur global : série de jours, objectif quotidien, centres d'intérêt et types de cartes préférés agrégés sur tous les thèmes, niveau (débutant / intermédiaire / expert). Il est renvoyé à Claude pour personnaliser chaque nouveau thème dès la première carte.
- Bibliothèque de thèmes : chaque thème garde sa pile, ses cartes aimées et ses poids ; on reprend où on s'était arrêté.
- Révision par répétition espacée des cartes aimées (boîtes de Leitner : 1, 3, 7 puis 21 jours).
- « Approfondir » sur une carte, prononciation audio pour les mots de langue, suggestions de thèmes par Claude, export / import du profil.

- Une seule page HTML, sans build ni dépendance.
- Les cartes sont générées en flux par l'API Anthropic (une ligne JSON par carte) : la première carte s'affiche dès qu'elle est écrite.
- Chaque carte porte 2 ou 3 sous-thèmes. Un « j'aime » leur ajoute 2 points, un « passe » en retire 1. Le profil est renvoyé à Claude à chaque lot : 70 % de cartes dans tes goûts, 30 % d'exploration.
- Sur GitHub Pages, le profil et la clé API restent dans le navigateur (localStorage). Dans la version claude.ai, le profil est aussi enregistré dans la base de l'artefact, privée par utilisateur.

## Clé API

La page appelle `https://api.anthropic.com/v1/messages` directement depuis le navigateur. Il faut une clé Anthropic personnelle, à coller dans « Clé API ». Elle n'est envoyée qu'à l'API Anthropic. Modèles proposés : Opus 5, Sonnet 5, Haiku 4.5.
