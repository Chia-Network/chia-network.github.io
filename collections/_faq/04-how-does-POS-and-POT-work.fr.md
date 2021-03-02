---
lang: fr
order: 4
title: "Comment fonctionnent les preuves d'espace et les preuves de temps?"
---

La preuve d'espace peut être considérée comme un moyen de prouver que vous conservez une partie de l'espace de stockage inutilisé sur votre disque dur. Les utilisateurs de la blockchain Chia «amorceront» l'espace inutilisé sur leur disque dur en installant un logiciel qui stocke une collection de numéros cryptographiques sur le disque dans des «tracés». Ces utilisateurs sont appelés «agriculteurs». Lorsque la blockchain diffuse un défi pour le bloc suivant, les agriculteurs peuvent scanner leurs parcelles pour voir s'ils ont le hachage le plus proche du défi. La probabilité qu'un agriculteur gagne un bloc est le pourcentage de l'espace total qu'un agriculteur a comparé à l'ensemble du réseau.

La preuve de temps nécessite une petite période de temps pour passer entre les blocs. La preuve de temps est implémentée par une fonction de délai vérifiable qui prend un certain temps à calculer, mais est très rapide à vérifier. L'idée clé d'un VDF est qu'il nécessite un calcul séquentiel, et comme le fait d'avoir de nombreuses machines parallèles ne donne aucun avantage, le gaspillage d'électricité est minimisé. Il y aura probablement relativement peu de serveurs VDF («Timelords»), car le plus rapide terminera toujours en premier et il ne faudra qu'un seul Timelord rapide et juste sur le réseau pour terminer un bloc et faire avancer la chaîne.
