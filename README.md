# Inventaire PHP — serveurs vulnérables

Outil local qui repère les serveurs d'un établissement de santé exécutant PHP et ceux dont la version est
concernée par les vulnérabilités **CVE-2026-109618 / CVE-2026-109619** (alerte CERT-FR du 21/10/2026), suit leur
correction et consolide les bilans de plusieurs hôpitaux. Il aide à décider ; il ne corrige rien et ne décide rien.

Conçu et développé par **Stéphane Monéger, RSSI des Hôpitaux de Corrèze** (stephane.moneger@ch-correze.fr), avec
l'assistance de Claude (Anthropic). Partagé avec les établissements du club national des RSSI santé, sous
**licence MIT** (`LICENSE`). Ce dépôt ne diffuse que les **versions signées** ; il ne contient ni code source à
exécuter tel quel, ni aucune donnée.

## Ce que fait l'outil

- **Périmètre déclaré par vous** : cartographie des VLAN, inventaire des serveurs, noms d'hôtes. Rien en dehors
  n'est interrogé ; les exclusions l'emportent toujours.
- **Scan réseau** (sans compte) : services web et indices PHP, versions annoncées.
- **Scan hôtes** (compte SSH ou WinRM saisi à l'exécution, jamais enregistré) : versions de PHP réellement
  installées, en lecture seule.
- **Résultats** : machines concernées, suivi des corrections, plan d'action, vue multi-hôpitaux, exports.
- Fonctionne sur un poste Windows, sans installation ni droits d'administration (Python embarqué par le lanceur) ;
  interface dans le navigateur, sur 127.0.0.1 uniquement. Les données restent sur le poste.

## Récupérer la dernière version

Le dossier [`livraisons/`](livraisons/) contient un sous-dossier par version ; `DERNIERE-VERSION.txt` indique la
plus récente. Chaque version comprend :

| Fichier | Rôle |
| --- | --- |
| `InventairePHP-vX.Y.Z.zip` | le programme |
| `InventairePHP-vX.Y.Z.zip.sig` | la signature de l'auteur (toujours la télécharger avec l'archive) |
| `A LIRE - installation.txt` | la notice pas à pas |
| `Verifier InventairePHP-vX.Y.Z.html` | page de vérification de l'archive (première installation) |

**Première installation** : suivez la notice. Par prudence, comparez l'empreinte SHA-256 de l'archive à celle
annoncée par l'auteur sur un autre canal que ce dépôt (message du club, courriel) — la page « Verifier » le fait
pour vous. **Mises à jour** : déposez l'archive et sa signature dans Téléchargements et utilisez l'option 5 du
lanceur : l'outil installé vérifie lui-même la signature de l'auteur et refuse toute archive modifiée.

## Ce que l'outil exige de vous

- **Une autorisation écrite de balayage**, consignée dans votre établissement (qui autorise, quel périmètre,
  quelles actions) : l'outil n'interroge que ce que vous lui donnez, sous votre responsabilité.
- Un poste réservé aux fonctions DSI / RSSI / RSI, avec un dossier de données aux droits restreints : les
  résultats révèlent des faiblesses de votre système d'information.

Au premier lancement, déclarez votre organisation et vos établissements (« Mon établissement n'est pas dans la
liste ») : l'écran se met à vos couleurs, sans aucune référence aux Hôpitaux de Corrèze hormis le crédit d'auteur.

## Signatures

Chaque archive est signée par la clé de l'auteur (format SSHSIG, Ed25519). Clé publique :

```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIKnS1RnyTPZC1zN6N9EHz2YHY8HnJdSfsPeFhHmeLHCK Signature Inventaire PHP - RSSI Hopitaux de Correze
```

Empreinte : `SHA256:ua+kcOxT3hsOeFxdyJADPogVig7D7jd4foQrMm/b0rg`. L'outil installé porte cette clé et vérifie
chaque mise à jour tout seul.

Questions, anomalies, demandes : écrire à l'auteur. Les contributions passent par lui : ce dépôt n'accepte pas de
modifications directes.
