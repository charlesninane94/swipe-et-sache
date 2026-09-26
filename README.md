# Swipe & Sache

Le tinder de l'info. Tu donnes un thème (« apprends-moi des mots en espagnol », « les nouvelles du sport »…), Claude génère des cartes courtes, tu swipes à droite ce qui t'intéresse, et chaque « j'aime » renforce ce genre d'info dans les cartes suivantes.

Page : https://charlesninane94.github.io/swipe-et-sache/

## Fonctionnement

- Une seule page HTML, sans build ni dépendance.
- Les cartes sont générées en flux par l'API Anthropic (une ligne JSON par carte) : la première carte s'affiche dès qu'elle est écrite.
- Chaque carte porte 2 ou 3 sous-thèmes. Un « j'aime » leur ajoute 2 points, un « passe » en retire 1. Le profil est renvoyé à Claude à chaque lot : 70 % de cartes dans tes goûts, 30 % d'exploration.
- Le profil, la pile de cartes et la clé API restent dans le navigateur (localStorage).

## Clé API

La page appelle `https://api.anthropic.com/v1/messages` directement depuis le navigateur. Il faut une clé Anthropic personnelle, à coller dans « Clé API ». Elle n'est envoyée qu'à l'API Anthropic. Modèles proposés : Opus 5, Sonnet 5, Haiku 4.5.
