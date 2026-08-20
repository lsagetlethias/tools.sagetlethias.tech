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

Le domaine apex de ce sous-domaine pointe sur GitHub Pages, les outils
pointent chacun sur leur hébergeur :

| Nom                                | Type  | Valeur                    |
| ---------------------------------- | ----- | ------------------------- |
| `tools.sagetlethias.tech`          | CNAME | `lsagetlethias.github.io` |
| `caldav2ics.tools.sagetlethias.tech` | CNAME | (Deno Deploy)             |
| `fgp.tools.sagetlethias.tech`      | CNAME | (Deno Deploy)             |

Un enregistrement joker `*.tools.sagetlethias.tech` ne couvre pas
`tools.sagetlethias.tech` lui-même : les deux cohabitent sans conflit.

## Outils recensés

- [caldav2ics](https://github.com/lsagetlethias/caldav2ics) : CalDAV vers ICS
- [fine-grained-proxy](https://github.com/lsagetlethias/fine-grained-proxy) :
  tokens fine-grained devant n'importe quelle API
