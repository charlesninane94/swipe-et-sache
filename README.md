# Swipe & Sache

Un outil d'apprentissage par cartes à swiper. Tu donnes un thème (« apprends-moi des mots en espagnol », « histoire de France »…), Claude génère des cartes courtes, et pour chacune tu réponds « je savais » (droite) ou « je ne savais pas » (gauche). Ce que tu savais ne revient jamais. Ce que tu ne savais pas revient plus tard, à intervalles croissants, jusqu'à être acquis. Ton profil montre tes forces et tes lacunes par sous-thème.

Page : https://charlesninane94.github.io/swipe-et-sache/

## Fonctionnement

- Modèle de connaissance : chaque carte porte 2 ou 3 sous-thèmes (tags). Un « je savais » / « je ne savais pas » alimente un taux de connaissance par sous-thème, par thème et global. Le profil affiche les points forts et ce qui reste à travailler.
- File d'apprentissage : une carte non sue revient dans la pile après 20 minutes, puis 1 jour, puis 4 jours. Trois « je savais » d'affilée la rendent acquise ; elle ne revient plus. Un échec la remet au début.
- Claude reçoit forces et lacunes : il consolide les sous-thèmes faibles par des notions voisines, monte en finesse sur les sous-thèmes maîtrisés, et explore le reste.
- Marque-page indépendant pour sauvegarder une carte, « Approfondir », prononciation audio pour les mots de langue, suggestions de thèmes, niveau par thème, série de jours et objectif quotidien, export / import.

- Une seule page HTML, sans build ni dépendance.
- Les cartes sont générées en flux par l'API Anthropic (une ligne JSON par carte) : la première carte s'affiche dès qu'elle est écrite.
- Chaque carte porte 2 ou 3 sous-thèmes. Un « j'aime » leur ajoute 2 points, un « passe » en retire 1. Le profil est renvoyé à Claude à chaque lot : 70 % de cartes dans tes goûts, 30 % d'exploration.
- Sur GitHub Pages, le profil et la clé API restent dans le navigateur (localStorage). Dans la version claude.ai, le profil est aussi enregistré dans la base de l'artefact, privée par utilisateur.

## Actualité en direct

Sur GitHub Pages, un thème d'actualité (sport, politique, économie…) active la recherche web côté Anthropic : Claude cherche des faits des 7 derniers jours avant d'écrire les cartes, avec date et média dans chaque carte. Le commutateur « Actualité en direct » dans le panneau du thème permet de couper. Chaque recherche est facturée par Anthropic en plus des tokens. La version claude.ai n'a pas d'accès à internet.

## Clé API

La page appelle `https://api.anthropic.com/v1/messages` directement depuis le navigateur. Il faut une clé Anthropic personnelle, à coller dans « Clé API ». Elle n'est envoyée qu'à l'API Anthropic. Modèles proposés : Opus 5, Sonnet 5, Haiku 4.5.
