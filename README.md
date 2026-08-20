# tools.sagetlethias.tech

Page de recensement des outils auto-hébergés sur `*.tools.sagetlethias.tech`.

Site statique d'un seul fichier, servi par GitHub Pages depuis la branche
`main`. Pas de build, pas de dépendances, pas de framework : on édite
`index.html` et on pousse.

## Ajouter un outil

Dupliquer un bloc `<li><article class="tool">…</article></li>` dans
`index.html` et remplacer le nom, la description, les deux liens et le
sous-domaine. Rien d'autre à toucher.

## Structure

| Fichier      | Rôle                                                       |
| ------------ | ---------------------------------------------------------- |
| `index.html` | La page, styles inclus dans un `<style>`                    |
| `CNAME`      | Domaine custom lu par GitHub Pages                          |
| `.nojekyll`  | Désactive Jekyll, on sert les fichiers tels quels           |

## DNS

Zone hébergée chez Gandi. Le nom `tools.sagetlethias.tech` porte déjà des
enregistrements enfants (`caldav2ics.`, `fgp.`), il faut donc l'adresser en
**A / AAAA et non en CNAME** : la RFC 1034 interdit toute autre donnée sur un
nom qui porte un CNAME, et plusieurs résolveurs gèrent mal les enfants d'un
alias.

| Nom     | Type | Valeurs                                                                                  |
| ------- | ---- | ---------------------------------------------------------------------------------------- |
| `tools` | A    | `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`                |
| `tools` | AAAA | `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153` |

Les outils gardent chacun leur CNAME vers `alias.deno.net`, ils ne sont pas
affectés.

Une fois la propagation faite, GitHub provisionne le certificat tout seul, puis
il reste à cocher « Enforce HTTPS » dans les réglages Pages.

## Outils recensés

- [caldav2ics](https://github.com/lsagetlethias/caldav2ics) : CalDAV vers ICS
- [fine-grained-proxy](https://github.com/lsagetlethias/fine-grained-proxy) :
  tokens fine-grained devant n'importe quelle API
