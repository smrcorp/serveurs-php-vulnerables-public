# Politique de sécurité — Inventaire PHP

## Signaler une vulnérabilité

Si vous pensez avoir trouvé une vulnérabilité dans l'outil, ne la décrivez pas publiquement (ni ticket,
ni liste de diffusion) : écrivez directement à l'auteur, **Stéphane Monéger, RSSI des Hôpitaux de
Corrèze** — stephane.moneger@ch-correze.fr — en décrivant le scénario, la version concernée et, si
possible, un moyen de reproduire. N'envoyez jamais de données réelles (adresses internes, noms de
serveurs, résultats de scans).

Vous recevrez un accusé de réception sous cinq jours ouvrés. Les vulnérabilités confirmées sont
corrigées en priorité et donnent lieu à une version signée ; le signaleur est crédité s'il le souhaite.

## Versions prises en charge

Seule la **dernière version publiée** est maintenue (voir `DERNIERE-VERSION.txt` du dépôt de
diffusion). Les mises à jour sont vérifiées par signature par l'outil lui-même (option 5).

## Comment les modifications sont revues

Chaque modification passe par une branche et une demande de fusion, des contrôles automatiques
(essais de bout en bout, recherche de secrets, refus d'imports piégés, vecteurs de signature) et la
validation écrite du propriétaire. Les changements qui touchent à la sécurité (signature des
livraisons, serveur local, périmètre des scans) reçoivent en plus une revue contradictoire par une IA
tierce avant livraison ; chaque constat est consigné dans `docs/audit/SUIVI-CONSTATS.md` avec son
état, et n'est clos qu'avec un test de non-régression.
