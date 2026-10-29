# Combat Assessment

Static quiz site for **combatassessment.com** — four game-themed personality assessments
(PUBG: BATTLEGROUNDS, Ready or Not, Call of Duty, GTA VI) that end in a character match and
two recommended replicas.

## Structure

```
index.html            entry / game picker
pubg.html             PUBG: BATTLEGROUNDS quiz
ready-or-not.html     Ready or Not quiz
cod.html              Call of Duty quiz
gta6.html             GTA VI quiz
assets/img/           49 images used by the pages (heroes, characters, products)
CNAME                 custom domain for GitHub Pages
.nojekyll             serve files as-is (no Jekyll processing)
```

## Hosting

GitHub Pages, branch `main`, folder `/ (root)`.
Custom domain `combatassessment.com` — `CNAME` is already committed, so Pages picks it up
automatically once DNS resolves:

| Type | Name | Value |
|------|------|-------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | `<your-github-username>.github.io` |

Enable **Enforce HTTPS** after the certificate is issued (usually within an hour of DNS propagating).

## Email capture

The quiz posts to Klaviyo on submit (public API key + list `TaizN7`, list name *Combat Assessment*).
Profile properties (`game`, `character`, `trait1..4_name/pct`, `gun1/2_*`, `theme_accent`, `game_bg`, …)
are written in the same request as the list join, so the welcome flow can merge them immediately.
The email template itself lives outside this repo (`email-combat-assessment.html`) and is pasted
into the Klaviyo flow's HTML block.
