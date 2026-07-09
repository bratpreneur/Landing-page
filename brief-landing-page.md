# 🎯 Script de génération — Landing page BERAT

> **Comment utiliser ce document :**
> - Pour générer la page : copie la **Section 0 (Prompt à coller)** comme instruction, puis colle les **Sections 2 à 6** comme référence (ou colle tout le document d'un coup).
> - Objectif unique de la page : **faire réserver un appel de qualification gratuit de 30 min.**
> - Langue : **français**. Ton : confiant, direct, honnête, façon leader. Zéro survente, zéro cliché de gourou.

---

## 0. PROMPT À COLLER (génération)

```
Tu es un expert en design UI/UX et développement front-end. Génère une landing page
"vitrine" haut de gamme, en français, dont le SEUL objectif est de faire réserver un
appel de qualification gratuit de 30 minutes.

STYLE : sombre + premium + accent OR. Fond noir profond, l'or (#D6B24A / #F0D688)
réservé UNIQUEMENT aux éléments clés (promesse, chiffres, prix, boutons CTA). Sobre,
élégant, jamais criard. Inspiration : pages "book a call" premium (Hormozi, Iman Gadzhi)
mais version raffinée et honnête.

CONTRAINTES :
- Un SEUL objectif et un SEUL type de CTA répété : "Réserver mon appel de qualification".
- Mobile-first, parfaitement responsive (360px / 768px / 1280px), aucun débordement.
- Typo : titres "Sora", corps "Manrope" (Google Fonts).
- Accessibilité AA (contrastes, focus visibles, tailles ≥ 14px sur mobile).
- Micro-animations sobres (reveals au scroll, hover), respecter prefers-reduced-motion.
- Conformité : l'investissement est présenté comme une COMPÉTENCE qui s'apprend, jamais
  comme un revenu garanti. Disclaimer AMF visible (voir Section 6).
- Tous les CTA pointent vers le lien de réservation (placeholder Calendly à remplacer).

Utilise EXACTEMENT le design system (Section 2), la structure (Section 3) et le
copywriting (Section 4) fournis ci-dessous. Respecte l'ordre des sections et le texte
au mot près. Prévois des emplacements pour les images (Section 5).
```

---

## 1. Objectif & règles d'or

| Élément | Décision |
|---|---|
| **But unique** | Réserver un appel de qualification gratuit (30 min) |
| **Avatar** | 20–35 ans, veulent comprendre le business en ligne, **peur des arnaques**, prêts à bosser (même salariés) |
| **Angle retenu (jury)** | « **Prouvé, pas promis** » — on assume la promesse ET on s'engage à la démontrer |
| **Risque n°1 à désamorcer** | La méfiance / peur de l'arnaque → on mène par la **preuve** (UGC, autorité), pas par la promesse |
| **Levier de conversion clé** | La **sélection** (« ce n'est pas pour tout le monde ») + la **transparence** |
| **CTA** | « Réserver mon appel de qualification (30 min, gratuit) » |

---

## 2. Design system

### Palette
| Rôle | Hex |
|---|---|
| Fond principal | `#0A0A0B` |
| Surface / cartes | `#101013` |
| Surface 2 | `#17171B` |
| Lignes / bordures | `#26251F` |
| Texte | `#F4EFE6` |
| Texte atténué (muted) | `#9A958A` |
| Or (accent) | `#D6B24A` |
| Or clair (highlight) | `#F0D688` |
| Or profond | `#A8842E` |

**Règle d'or absolue :** l'or est réservé aux éléments clés (promesse, chiffres/stats, prix, boutons, carte « populaire »). Jamais de surface or pleine ailleurs → c'est ce qui garde le premium.

### Typographie (Google Fonts)
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Sora:wght@500;600;700;800&family=Manrope:wght@400;500;600;700&display=swap" rel="stylesheet">
```
- **Sora** 700/800 → H1-H2 et chiffres clés (prix, stats). 600 → H3. Tracking serré `-0.02em` sur les gros titres. Poids 800 réservé au H1 + promesse centrale.
- **Manrope** 400/500 → paragraphes et labels ; 600/700 → boutons, tags prix, micro-titres. Interligne `1.6` en body.
- **Échelle** : H1 `clamp(2.6rem,6vw,4.6rem)` / H2 `clamp(2rem,4vw,3rem)` / H3 `1.5rem` / body `1.0625rem` / small `0.875rem` / eyebrow `0.75rem` uppercase `letter-spacing:0.18em`.

### Composants
- **Bouton OR (primaire)** : dégradé `#F0D688 → #D6B24A`, texte `#0A0A0B` (Manrope 700), radius `10px`, padding `16px 28px`, ombre douce dorée `0 8px 24px rgba(214,178,74,.25)`. Hover : `+6%` luminosité, `translateY(-2px)`, halo intensifié. Focus-visible : contour `#F0D688` 2px.
- **Bouton secondaire (ghost)** : bordure `#26251F`, texte clair, hover bordure or 40%.
- **Cartes de prix** : base `#101013`, bordure `#26251F`, radius `16px`. Carte populaire (6 mois) = bordure or `1.5px` pleine + fond dégradé doré 6% + pilule « LE PLUS POPULAIRE ». Prix en Sora 800, inclusions avec puce coche or.
- **Badges** : pilules radius `999px`, fond transparent, bordure or 30%, texte or clair `0.75rem` uppercase (ex. « EN DIRECT » + pastille rouge, « GARANTIE 7 JOURS »).
- **Barre de confiance** : chiffres Sora 700 or + label muted, diviseurs verticaux `1px #26251F`, fond `#101013`.
- **Accordéon FAQ** : ligne cliquable pleine largeur, question Manrope 600, chevron or qui pivote 180°, corps qui se déploie (max-height + opacity) sur léger fond `#101013`.
- **Icônes / traits** : fins `1.5px`, or réservé aux accents.

### Motion (sobre & premium)
- **Reveals au scroll** : fade + `translateY(16px→0)`, 500–600ms, `cubic-bezier(0.16,1,0.3,1)`, déclenché à ~15% de visibilité (IntersectionObserver). Stagger 60–80ms sur les grilles.
- **Hero** : halo doré en « breathing » lent (scale 1→1.05, opacité 12%→16%, 8s alternate).
- **Hover** : cartes lift `translateY(-4px)` + bordure vers l'or ; tuiles de preuve zoom image `1.03`.
- **Live TikTok** : pastille rouge pulse doux (1.5s).
- **Nav** : fond blur qui apparaît au scroll (300ms).
- **`prefers-reduced-motion`** : désactiver translate/scale, garder de légers fades. Aucun parallax agressif, aucun auto-play.

---

## 3. Structure de la page (ordre exact)

1. **Nav sticky** (logo BERAT + CTA unique)
2. **Hero** (promesse « prouvé, pas promis » + CTA + portrait)
3. **Barre de confiance** (chiffres/preuves)
4. **Problème** (douleur — « 12 paies / 100 dépenses »)
5. **Mécanisme** (« l'environnement bat la génétique » + 3 étapes)
6. **Les 3 piliers** (UGC / IA / Investissement)
7. **Preuve sociale** (résultats + live + autorité)
8. **Histoire de Berat** (parcours + citation du mentor)
9. **Ce n'est pas pour toi si…** (sélection)
10. **L'appel** (ce qui se passe pendant les 30 min)
11. **Les 3 formules** (prix + ancrage)
12. **Garantie** (7 jours)
13. **FAQ** (objections)
14. **Coût de l'inaction** (projection 12 mois)
15. **CTA final**
16. **Footer** (+ disclaimer AMF)

---

## 4. Copywriting complet (au mot près)

### 1) Nav (sticky)
- **Logo :** `BERAT` (or clair, le « R » ou le « B » souligné d'un trait or 2px)
- **Bouton :** `Réserver mon appel gratuit` · sous-texte `30 min`
- *Un seul élément cliquable. Pas de liens réseaux sociaux. Le bouton scrolle vers la réservation.*

### 2) Hero
- **Eyebrow :** Pour ceux qui veulent comprendre le business en ligne — sans se faire avoir.
- **H1 :** 2 nouvelles sources de revenus en 90 jours. **Prouvé, pas promis.**
- **Sous-titre :** UGC, IA et Investissement comme une compétence. Pas une énième formation : un accompagnement sur-mesure, entouré des bonnes personnes.
- **Corps :** Ex-ingénieur production chez Renault. Aujourd'hui, formateur de +500 personnes en 2 ans et responsable formation IA dans un réseau de 5 000. Je t'aide à bâtir 2 nouvelles sources de revenus : la création de contenu pour les marques (UGC), l'IA, et l'investissement comme une compétence qui s'apprend. Entouré de gens qui avancent vraiment, pas de vendeurs de rêve. L'environnement bat la génétique. Et honnêtement : ce n'est pas pour tout le monde. L'appel de 30 min sert justement à le vérifier. Si ce n'est pas pour toi, tu repars quand même avec un plan clair.
- **CTA :** Réserver mon appel de qualification (30 min, gratuit)
- **Sous-CTA :** Appel de qualification, pas de vente forcée. Zéro engagement.
- **Micro-badges sous le CTA :** +500 accompagnés · Garantie 7 jours · Sélection réelle
- *OR sur : « 2 », « 90 jours », « Prouvé », et le bouton. Portrait pro de Berat à droite avec halo doré.*

### 3) Barre de confiance
- **Titre :** La preuve avant la promesse
- **Sous-titre :** Des faits vérifiables, pas des adjectifs.
- **Points :**
  - +500 personnes accompagnées en 2 ans
  - Mise en relation directe avec les marques (UGC)
  - Responsable formation IA d'un réseau de 5 000 personnes
  - Ex-ingénieur production chez Renault, 4 ans
  - Live TikTok de trading en transparence totale
  - Garantie 7 jours satisfait ou remboursé
- *Chiffres en or. Emplacement pour logos de marques + 2-3 flyers de collaborations. NE PAS afficher l'Instagram.*

### 4) Problème (douleur)
- **Eyebrow :** Sois honnête avec toi une minute.
- **H2 :** 12 paies par an. Mais 100 dépenses dans le mois.
- **Sous-titre :** Une seule source de revenus, c'est une seule corde à laquelle tu es suspendu.
- **Corps :** Tu échanges 100 % de ton temps contre un seul salaire. Ton temps ne t'appartient pas. Les factures tombent, elles, sans jamais te demander ton avis. Autour de toi, un environnement qui te tire vers le bas plus qu'il ne te pousse. Tu sens que tu as plus en toi, un potentiel que personne n'exploite. Mais entre ce que tu sens et ce que tu fais : 0 passage à l'action. Pas par manque de volonté. Par manque d'infos claires et de gens crédibles à qui te fier. Le vrai risque, ce n'est pas d'essayer et de te tromper. C'est de rester dans la même case toute ta vie, en te disant chaque année que tu commenceras l'année prochaine.
- **Points :**
  - Un seul salaire, et il file avant la fin du mois
  - Un entourage qui juge au lieu de soutenir
  - Un potentiel que tu sens, mais que tu n'exploites pas
  - Déjà essayé seul (dropshipping, crypto…) et abandonné, faute d'environnement
- *Seuls les chiffres 12 / 100 / 0 en or.*

### 5) Mécanisme
- **Eyebrow :** Un leader ne montre jamais le problème sans donner la solution.
- **H2 :** L'environnement bat la génétique
- **Sous-titre :** Ce qui te manque, ce n'est pas la volonté. C'est le bon système et le bon cercle.
- **Corps :** Tu n'as pas échoué parce que tu es nul. Tu as échoué parce que tu étais seul : sans réseau, sans suivi, sans vraies opportunités. Personne ne démarre bon. On le devient dans le bon environnement. C'est exactement ce que je construis : un système éprouvé, plus les bonnes personnes autour de toi. Concrètement, ça tient en 3 étapes simples.
- **Étapes :**
  - **Étape 1 — On branche l'environnement :** tu entres dans le réseau, les sessions live et un suivi perso. Tu arrêtes d'avancer seul.
  - **Étape 2 — On active la 1re source (UGC) :** tu crées du contenu pour les marques, et je te mets en relation réelle avec elles. C'est concret, vérifiable, ça paie.
  - **Étape 3 — On empile une 2e source (IA + Investissement) :** les compétences IA qui font la différence aujourd'hui, et l'investissement appris comme une compétence. Objectif : au moins 2 nouvelles sources de revenus.
- *Mini-comparatif visuel : « Ce que ce n'est PAS » (une vidéo de plus à regarder seul) vs « Ce que c'est » (accompagnement + réseau + mise en relation réelle). Étapes en pictos or 1-2-3.*

### 6) Les 3 piliers
- **Eyebrow :** Ce que tu construis vraiment
- **H2 :** 3 piliers, 2 sources de revenus
- **Sous-titre :** On mène par le plus concret et le plus vérifiable. Le reste vient se poser dessus.
- **Corps :** L'objectif n'est pas de tout faire d'un coup. C'est de bâtir au moins 2 nouvelles sources de revenus, dans le bon ordre, en commençant par la plus prouvable.
- **Piliers :**
  - **Pilier 1 — UGC (point d'entrée) :** crée du contenu pour les marques. Je suis ta mise en relation réelle avec elles. C'est ce que +500 personnes font déjà.
  - **Pilier 2 — IA :** les compétences qui font la différence aujourd'hui, expliquées et mises en pratique dans un réseau de 5 000 personnes.
  - **Pilier 3 — Investissement :** une compétence qui s'apprend, jamais une promesse de gains. Abordé avec retenue, après l'UGC.
- *UGC dominant visuellement. Disclaimer AMF juste sous le pilier 3.*

### 7) Preuve sociale
- **Eyebrow :** Regarde, ne me crois pas sur parole.
- **H2 :** Des résultats affichés, un live que tu peux vérifier
- **Sous-titre :** Un vendeur de rêve promet et disparaît. Moi, je montre, et je reste.
- **Corps :** La différence entre une promesse et une preuve, c'est que la preuve, tu peux la vérifier toi-même. Alors voilà ce qui est sur la table, en transparence totale.
- **Points :**
  - +500 personnes accompagnées en 2 ans, dont des débutants et des salariés partis de zéro
  - Collaborations UGC affichées : 1, 10, 25, 50 marques
  - Un live TikTok de trading en direct : rien de caché, tu vérifies par toi-même
  - Responsable formation IA d'un réseau de 5 000 personnes
- *Mur de flyers clients + capture live TikTok. Chiffres de trading = illustrations d'une compétence, JAMAIS des gains attendus. Disclaimer AMF à proximité.*

### 8) Histoire de Berat
- **Eyebrow :** Qui est Berat
- **H2 :** Je ne suis pas un gourou anonyme derrière un écran
- **Sous-titre :** Ingénieur de formation. 4 ans en production chez Renault. La rigueur scientifique, je l'applique au business.
- **Corps :** J'ai toujours senti que je pouvais faire plus, sans plafond : dans les études, dans le sport, puis dans le business. J'ai quitté le confort d'un poste d'ingénieur parce que dépendre d'une seule source de revenus, ce n'était pas une vie libre. En 2 ans, j'ai accompagné +500 personnes en UGC et je suis devenu responsable formation IA d'un réseau de 5 000. Aujourd'hui, j'aide ceux qui n'arrivent pas à faire le premier pas pour eux-mêmes. Mon rôle, ce n'est pas de vendre une formation. C'est de bâtir des humains et de les entourer. Et j'ai une règle que je ne casse jamais : je ne sacrifierai jamais une relation pour une vente.
- **Citation du mentor (mise en exergue, or) :**
  > « Les petites visions ne peuvent pas comprendre les plus grandes. Mais les grandes visions peuvent comprendre les plus petites. »
- *Grande photo pro (portrait ou action, passé sports de combat). Faits en gras : Renault, +500, 5 000.*

### 9) Ce n'est pas pour toi si…
- **Eyebrow :** On va se dire les choses
- **H2 :** Ce n'est pas pour tout le monde
- **Sous-titre :** Je ne prends pas tout le monde. Et c'est exactement ce qui devrait te rassurer.
- **Corps :** Un vendeur de rêve dit oui à tout le monde. Moi, non. Environ 1 personne sur 2 qui fait l'appel démarre. Si je te dis oui, ce n'est pas pour te vendre : c'est parce que je vois concrètement que ça peut marcher pour ton profil.
- **Colonne « PAS pour toi » :**
  - Tu cherches un bouton magique et du revenu passif sans effort
  - Tu attends qu'on te motive de force tous les matins
  - Tu n'as vraiment aucune heure par semaine à investir sur toi
- **Colonne « Pour toi » :**
  - Tu as encore du temps à investir sur toi et tu es prêt à bosser, même salarié
  - Tu veux COMPRENDRE le business en ligne, pas juste consommer une énième formation
  - Tu veux entrer dans un cercle de gens qui te tirent vers le haut
- **Phrase de clôture (or) :** La vraie question n'est pas « est-ce pour moi », mais « suis-je prêt à bosser ».

### 10) L'appel
- **Eyebrow :** Avant de parler prix, parlons de l'appel
- **H2 :** Ce qui se passe pendant les 30 minutes
- **Sous-titre :** Un appel de qualification, pas un tunnel de vente.
- **Corps :** Tu repars avec de la valeur, même si on ne travaille pas ensemble. C'est ma règle de réciprocité : je ne te fais pas perdre ton temps. Voilà le déroulé, sans surprise.
- **Points :**
  - On décortique ensemble ta situation, ton problème et ton besoin réel
  - Je te donne un diagnostic clair et un plan d'action concret, adapté à ton profil
  - Je suis 100 % honnête sur le fit : si ce n'est pas pour toi, je te le dis en face et je te donne quoi faire pour te qualifier
  - Zéro pression : je cherche des gens déjà prêts à bosser, pas des gens à convaincre de force
- **CTA :** Réserver mon appel de qualification (30 min, gratuit)
- **Sous-CTA :** Gratuit. 30 min. Tu repars avec un plan clair, même sans achat.

### 11) Les 3 formules (prix)
- **Eyebrow :** Les prix, affichés noir sur blanc
- **H2 :** 3 formules. Tu choisis avec moi sur l'appel.
- **Sous-titre :** Un arnaqueur cache son prix. Moi je te le montre avant même que tu réserves.
- **Corps :** On définit ensemble la bonne formule pendant l'appel, selon ton profil et ton rythme. Aucun engagement à réserver. Et rappelle-toi : ce qui coûte vraiment cher, ce n'est pas d'investir sur toi. C'est de finir l'année avec 0 source de revenus en plus et les mêmes factures.
- **Formules :**
  - **3 mois — 629,97 €** : pour démarrer et poser les fondations
  - **6 mois — 1 319,93 € — LE PLUS POPULAIRE** : le bon équilibre pour installer 2 sources de revenus durablement
  - **12 mois — 2 339,87 €** : accompagnement complet pour aller au bout de la transformation
- **Inclus (à lister discrètement) :** réseau, sessions live, contenus/formations, suivi perso, opportunités business, développement personnel.
- **CTA :** En parler sur l'appel gratuit
- **Sous-CTA :** On choisit ensemble. Sans engagement. Garantie 7 jours.
- *Carte 6 mois surélevée + badge or « LE PLUS POPULAIRE ». Prix en or. L'action reste l'appel, jamais un paiement direct.*

### 12) Garantie
- **Eyebrow :** Le risque est de mon côté
- **H2 :** Garantie 7 jours satisfait ou remboursé
- **Sous-titre :** Tu testes. Si ce n'est pas pour toi, tu récupères ton argent.
- **Corps :** Je ne prends pas de risque avec ta confiance, donc je le prends à ta place. Comme je sélectionne à l'entrée, je ne prends pas les profils qui vont échouer : ce ne serait bon ni pour toi, ni pour ma réputation. Je ne sacrifie jamais une relation pour une vente. Un leader ne montre jamais le problème sans donner la solution, y compris le tien.
- **CTA :** Réserver mon appel gratuit · **Sous-CTA :** Garantie 7 jours · Sélection réelle · 30 min
- *Badge/sceau or « 7 jours satisfait ou remboursé ».*

### 13) FAQ (accordéon)
- **Eyebrow :** Tes questions, mes réponses directes
- **H2 :** On répond à ce qui te retient vraiment
- **Entrées :**
  - **« C'est pas pour moi. »** — Peut-être. L'appel sert justement à le vérifier. La vraie question n'est pas « est-ce pour moi », mais « suis-je prêt à bosser ». +500 personnes ont commencé en se disant la même chose.
  - **« Encore une formation. »** — Non. Une formation qu'on regarde seul, on l'abandonne à 90 %. Ici, c'est un accompagnement : réseau, sessions live, suivi perso, et surtout mise en relation réelle avec des marques qui paient.
  - **« J'ai pas le temps. »** — Tu n'as pas le temps justement parce que tu dépends d'une seule source. L'appel, c'est 30 min. Et si tu n'as vraiment aucune heure par semaine à investir sur toi, je te le dirai honnêtement.
  - **« J'ai pas d'argent. »** — L'appel est gratuit et sans engagement. Le manque d'argent, c'est précisément le problème qu'on vient régler, pas une raison de ne pas en parler.
  - **« Encore un vendeur de rêve. »** — Un vendeur de rêve promet et disparaît. Moi je montre : live en direct, flyers clients, +500 accompagnés, et une garantie 7 jours. Regarde les preuves, décide ensuite.
  - **« Et si ça ne marche pas pour moi ? »** — C'est pour ça que l'appel est une qualification, pas un closing. Si je vois que ça ne peut pas marcher pour ton profil, je te le dis, et je te donne quoi faire.
  - **« L'investissement, c'est risqué. »** — Tu as raison d'être prudent. Ici c'est une compétence qu'on apprend, jamais un revenu garanti. Le point d'entrée reste l'UGC. Transparence totale : perte en capital possible, aucun revenu garanti.
  - **« Je suis déjà salarié, je verrai plus tard. »** — « Plus tard », c'est le mot qui te garde dans la même case pendant 10 ans. Le meilleur moment pour poser la question, c'est maintenant.

### 14) Coût de l'inaction
- **Eyebrow :** Projette-toi 12 mois plus loin
- **H2 :** Même case, ou nouveau cercle ?
- **Sous-titre :** Dans un an, tu peux avoir 2 sources de revenus en plus et un entourage qui te tire vers le haut. Ou exactement la même situation qu'aujourd'hui.
- **Corps :** Rester pour ne pas déranger ceux qui te freinent, c'est le vrai coût. Raviver un rêve mis de côté par le travail et un environnement nocif, ça ne commence pas par un grand saut. Ça commence par un appel de 30 minutes.
- *Chiffres « 12 mois » et « 2 sources » en or.*

### 15) CTA final
- **Eyebrow :** Il reste une action à faire
- **H2 :** Réserve ton appel de qualification
- **Sous-titre :** Places limitées : je sélectionne sur candidature, pas au premier venu.
- **Corps :** Un seul chemin. Un seul objectif : vérifier ensemble, en 30 minutes, si tu es fait pour ça. Si oui, on bâtit. Si non, tu repars avec un plan clair. Dans les deux cas, tu ne perds rien.
- **CTA :** Réserver mon appel de qualification (30 min, gratuit)
- **Sous-CTA :** Gratuit · 30 min · Appel de qualification, pas de vente forcée · Garantie 7 jours

### 16) Footer
- **Logo :** BERAT · **Baseline :** Comprendre le business en ligne, sans se faire avoir.
- **Liens :** Mentions légales · Conditions générales · Politique de confidentialité · Contact
- **Disclaimer AMF (voir Section 6).** NE PAS afficher l'Instagram.

---

## 5. Direction visuelle & assets à fournir

| Emplacement | Asset attendu |
|---|---|
| Hero (droite) | **Portrait pro** de Berat (lifestyle / action), halo doré derrière |
| Histoire | **Grande photo** (portrait ou action, sport de combat) |
| Barre de confiance | Logos de marques + 2-3 **flyers de collaborations** |
| Preuve sociale | **Mur de flyers** succès clients (collabs 1/10/25/50), **capture du live TikTok** |
| Piliers | Icônes/pictos fins (UGC, IA, Investissement) |

> Attributs `data-img` sur chaque placeholder pour un remplacement facile. Bloc stylisé « Ta photo ici » tant que l'image n'est pas fournie.

---

## 6. Conformité (AMF) & mentions

**Règle :** l'investissement est présenté comme une **compétence qui s'apprend**, jamais comme un revenu garanti. Aucun chiffre de trading présenté comme un gain attendu.

**Disclaimer complet (footer, en toutes lettres) :**
> L'investissement comporte des risques de perte en capital. Les résultats passés ne préjugent pas des résultats futurs. Aucun revenu n'est garanti. Les éléments présentés (collaborations, résultats clients, illustrations liées à l'investissement) reflètent des situations individuelles et ne constituent ni une promesse de gains, ni un conseil en investissement. L'investissement est abordé comme une compétence qui s'apprend. BERAT propose un accompagnement à la création de contenu, à l'usage de l'IA et à la montée en compétences ; les résultats dépendent du travail et de l'implication de chacun.

**SEO :**
- **Titre :** BERAT | 2 sources de revenus en 90 jours : prouvé, pas promis
- **Description :** UGC, IA et investissement comme compétence. Ex-ingénieur Renault, +500 personnes accompagnées en 2 ans. Réserve ton appel de qualification gratuit de 30 min. Preuve avant promesse, garantie 7 jours, sélection réelle.

---

## Annexe A — Plan de trafic (bonus)

### Marketing (organique)
- **Série anti-arnaque** (TikTok/Reels) : l'ingénieur ex-Renault démonte les arnaques du business en ligne → « moi je montre les vrais chiffres, en direct » → CTA appel.
- **Live TikTok « je décortique ton business en direct »** (2-3/sem) : démo publique de l'appel de qualif. Ils arrivent déjà réchauffés.
- **Mur de preuves UGC** : carrousels de collaborations réelles (1/10/25/50), captures.
- **Études de cas « de salarié à 2 revenus »** (storytelling 60-90s).
- **Lead magnet qui qualifie** : guide gratuit « 3 modèles rentables + comment repérer une arnaque » → séquence 3-4 messages → appel.
- **Retargeting** (pixel Meta + TikTok) : ne payer que pour les gens déjà chauds.
- **Contenu « j'ai dit non à ce profil »** : renforce la sélection.
- **TikTok Search / SEO d'intention** : « l'UGC c'est une arnaque ? », « gagner de l'argent avec l'IA en 2026 ».
- **Coulisses « le système d'un ingénieur »** : la rigueur rassure.

### Co-marketing (partenariats)
- **Salles de sports de combat** (le plus naturel — son milieu) : ateliers + QR code + parrainage.
- **Marques qui cherchent des créateurs UGC** : crédibilité empruntée + nouvelles preuves.
- **Micro-influenceurs niche argent/entrepreneuriat** (10-50k) : format interview qui désarme la méfiance.
- **Live commun avec une autorité** (comptable/avocat/fiscaliste) : caution institutionnelle.
- **Activer le réseau IA de 5 000** : upsell le plus rentable à court terme.
- **Cross-promo coachs complémentaires** (sport, mindset, prise de parole).
- **Interventions écoles / BTS / alternances** (angle ex-alternant Renault).

### Community
- **Créer le mouvement « L'environnement bat la génétique »** (« Le Cercle ») : espace gratuit avec règles strictes qui filtrent.
- **Rituel hebdo « Le Cercle du dimanche »** : live récurrent = appartenance + FOMO.
- **Ambassadeurs / parrainage** (les +500) : le trafic le plus immunisé contre la méfiance.
- **Mur de preuves auto-alimenté** : les membres postent leurs résultats.
- **Défis collectifs « premier revenu en 7 jours »** : attaque l'inaction (paliers façon ceintures).
- **Sélection à l'entrée = communauté premium.**
- **Événement IRL sport + business** : incarne « bâtir des humains ».

### Plan des 7 premiers jours
1. **J1 — Tracking** : pixel Meta + TikTok, événement « réservation d'appel », agenda de réservation, un seul CTA.
2. **J2 — Lead magnet** : guide gratuit + séquence 3-4 messages.
3. **J3 — Batch de contenu** : 6-7 clips (anti-arnaque, preuves, histoire perso, « j'ai dit non », CTA).
4. **J4 — Premier live TikTok** : « je décortique 3 business en direct » + disclaimer AMF.
5. **J5 — Activer les actifs** : message aux +500 et au réseau 5k, ouvrir le canal communauté.
6. **J6 — Prospection partenaires** : 5 contacts concrets (salles de combat, influenceur, expert, marque).
7. **J7 — Retargeting + analyse** : petite campagne (10-20 €/j) + bilan des appels réservés par source.

---

*Document généré à partir de la phase de découverte + workflow multi-agents (stratégie CRO, copywriting, design system, audit). Prêt à être utilisé pour la génération.*
