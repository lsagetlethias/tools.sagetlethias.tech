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

Zone hébergée chez Gandi.

| Nom     | Type  | Valeur                    |
| ------- | ----- | ------------------------- |
| `tools` | CNAME | `lsagetlethias.github.io` |

Les outils gardent chacun leur propre CNAME vers `alias.deno.net`
(`caldav2ics.tools`, `fgp.tools`) et continuent de résoudre normalement, bien
qu'ils soient enfants d'un nom qui porte un CNAME. La RFC 1034 interdit
d'autres données *sur le nom lui-même*, pas sur ses enfants, et Gandi les sert
correctement (vérifié sur Cloudflare, Google et Quad9).

Si un jour un résolveur exotique bute là-dessus, le repli est de remplacer le
CNAME par des A/AAAA vers GitHub Pages, ce qui supprime la question :

```
A     185.199.108.153  185.199.109.153  185.199.110.153  185.199.111.153
AAAA  2606:50c0:8000::153  2606:50c0:8001::153  2606:50c0:8002::153  2606:50c0:8003::153
```

Le certificat est provisionné automatiquement par GitHub, « Enforce HTTPS » est
activé.

## Outils recensés

- [caldav2ics](https://github.com/lsagetlethias/caldav2ics) : CalDAV vers ICS
- [fine-grained-proxy](https://github.com/lsagetlethias/fine-grained-proxy) :
  tokens fine-grained devant n'importe quelle API
