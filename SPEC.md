# SPEC: Dish Customization

**Feature Name:** Personalisation des plats avant commande  
**Status:** MVP (Hackathon)  
**Last Updated:** 2026-07-01  
**Audience:** Users Deliveroo, Internal Testing Team  

---

## ⭐️ Context & User Persona

### Context

Deliveroo veut permettre aux utilisateurs de personnaliser les plats avant de les ajouter au panier — ajouter des options (taille, extras, exclusions) et voir le prix mis à jour en temps réel. Actuellement, les plats sont commandés en l'état, ce qui limite les cas d'usage (plats complexes, régimes, préférences).

### User Personas

- **Regular User** : Utilisateur qui commande régulièrement, veut adapter les plats à ses goûts ou contraintes alimentaires (sans oignon, taille L, ajouter du fromage). **Persona principale.**
- **New User** : Utilisateur qui découvre l'app, doit comprendre que les options sont disponibles et comment les utiliser.
- **Occasional User** : Commande rarement, cherche une option simple pour faire des choix spécifiques.

### KPIs visés

- Taux de conversion (ajout au panier après personnalisation)
- Valeur moyenne par commande (augmentation via options payantes)
- Satisfaction utilisateur (réduction des cas "j'aurais aimé personnaliser ce plat")

---

## 👫 User Stories

**Epic : Dish Customization — Personaliser les plats avant commande**

**US 1 — Browse menu et découvrir les options disponibles**  
En tant que **Regular User**, lorsque j'accède au menu d'un restaurant, je veux voir quels plats ont des options disponibles (size, extras, exclusions), afin de savoir d'emblée quels plats je peux personnaliser.

**US 2 — Ouvrir le modal de customisation**  
En tant que **Regular User**, lorsque je clique sur un plat avec des options, je veux voir un modal/panel de customisation, afin de sélectionner mes options avant d'ajouter au panier.

**US 3 — Sélectionner les options (Size)**  
En tant que **Regular User**, dans le modal de customisation, je veux sélectionner une taille (S/M/L/XL), afin d'adapter la portion à mes besoins.

**US 4 — Ajouter des extras**  
En tant que **Regular User**, dans le modal de customisation, je veux ajouter des extras (fromage, bacon, sauce supplémentaire), afin de personnaliser le plat selon mes goûts.

**US 5 — Exclure des ingrédients**  
En tant que **Regular User**, dans le modal de customisation, je veux exclure des ingrédients (oignon, tomate, noix), afin de respecter mes préférences ou contraintes alimentaires.

**US 6 — Voir le prix mis à jour en temps réel**  
En tant que **Regular User**, lorsque je modifie mes options (ajouter/retirer), je veux voir le prix total se recalculer en temps réel, afin de connaître le coût avant de valider.

**US 7 — Ajouter le plat customisé au panier**  
En tant que **Regular User**, une fois mes options sélectionnées, je veux valider et ajouter le plat au panier avec toutes mes customisations, afin de passer à la commande.

**US 8 — Ajouter le même plat avec customisations différentes (multi-add)**  
⚠️ **V2** — En tant que **Regular User**, lorsque j'ai ajouté un plat customisé au panier, je veux pouvoir revenir au modal et ajouter le même plat avec d'autres options, afin de commander plusieurs versions du même plat.

**US 9 — Voir les customisations dans le panier**  
En tant que **Regular User**, lorsque je consulte mon panier, je veux voir clairement quelles options j'ai sélectionnées pour chaque plat, afin de vérifier que ma commande est correcte avant checkout.

**US 10 — Modifier ou retirer les customisations depuis le panier**  
En tant que **Regular User**, lorsque je suis dans le panier et que je veux ajuster ma commande, je veux pouvoir supprimer et ré-ajouter un plat avec d'autres customisations, afin de corriger sans recommencer.

**US 11 — Découvrir les options (New User)**  
En tant que **New User**, lorsque j'utilise Deliveroo pour la première fois, je veux une indication claire que je peux personnaliser les plats (tooltip, icône, ou texte), afin de ne pas passer à côté de cette fonctionnalité.

---

## 🚀 Releases

### Quick Win
**Objectif :** Valider que les utilisateurs veulent personnaliser les plats et comprendre les attentes sur les types d'options

- Customisation basique (size + extras) sur 2-3 plats tests
- Modal simple avec prix qui se met à jour
- Ajout au panier (sans les exclusions pour l'instant)

⚠️ **Ne livre PAS encore :**
- Exclusions
- Multi-add
- Modification depuis panier
- Indication "customizable" dans le menu

### MVP
**Objectif :** Permettre la customisation complète de TOUS les plats avec tous les types d'options

- Size + Extras + Exclusions fonctionnels pour tous les plats
- Prix en temps réel
- Affichage des customisations dans le panier
- Suppression/ré-ajout depuis panier (flow simplifié)
- Indication visuelle que les plats sont customisables (icône ou badge)

### V2
**Objectif :** Améliorer UX et autoriser multi-add

- Multi-add (même plat, customisations différentes, dans une seule US)
- Modification in-place des customisations depuis le panier
- Favoris/recommandations basés sur customisations fréquentes
- Presets (ex: "Sans ail", "Végétarien")

---

## ✅ Acceptance Criteria

### US 1 — Browse menu et découvrir les options disponibles

**AC 1.1 — Plats customisables sont identifiables**  
GIVEN je suis sur la page menu d'un restaurant  
WHEN je charge le menu  
THEN chaque plat customisable affiche un badge/icône "Personalizable" ou similaire

**AC 1.2 — Plats sans options n'ont pas l'indicateur**  
GIVEN je suis sur la page menu  
WHEN je consulte les plats  
THEN seuls les plats avec au moins une option disponible affichent l'indicateur

### US 2 — Ouvrir le modal de customisation

**AC 2.1 — Modal s'ouvre au clic sur plat customisable**  
GIVEN je suis sur le menu et un plat affiche l'icône "Personalizable"  
WHEN je clique sur ce plat  
THEN un modal/panel de customisation s'ouvre affichant toutes les options disponibles

**AC 2.2 — Modal affiche le nom et photo du plat**  
GIVEN le modal de customisation est ouvert  
WHEN je regarde le contenu  
THEN le nom du plat, sa description et sa photo sont visibles en haut

**AC 2.3 — Fermeture du modal sans customiser**  
GIVEN je suis dans le modal de customisation  
WHEN je clique sur "Annuler" ou la croix de fermeture  
THEN le modal se ferme et aucune donnée n'est sauvegardée

### US 3 — Sélectionner les options (Size)

**AC 3.1 — Les tailles disponibles s'affichent**  
GIVEN je suis dans le modal de customisation  
WHEN le plat a des tailles disponibles (S/M/L/XL)  
THEN je vois une section "Taille" avec des boutons radio ou des cartes pour chaque taille

**AC 3.2 — Une taille est sélectionnée par défaut**  
GIVEN je suis dans le modal pour la première fois  
WHEN aucune taille n'a été choisie  
THEN la taille par défaut (ex: M) est pré-sélectionnée

**AC 3.3 — Sélectionner une autre taille change le prix**  
GIVEN j'ai sélectionné la taille S  
WHEN je clique sur la taille L  
THEN la taille change et le prix total se met à jour (voir US 6)

**AC 3.4 — Plats sans tailles n'affichent pas la section**  
GIVEN un plat n'a pas d'options de taille  
WHEN j'ouvre le modal  
THEN la section "Taille" n'est pas affichée

### US 4 — Ajouter des extras

**AC 4.1 — Extras s'affichent avec prix**  
GIVEN je suis dans le modal de customisation  
WHEN le plat a des extras disponibles  
THEN je vois une section "Extras" avec des cases à cocher et le prix de chaque extra (+€1.50, etc.)

**AC 4.2 — Plusieurs extras peuvent être sélectionnés**  
GIVEN je suis dans la section Extras  
WHEN je coche plusieurs extras  
THEN tous les extras cochés restent sélectionnés

**AC 4.3 — Extras non disponibles sont désactivés**  
GIVEN je suis dans la section Extras  
WHEN certains extras ne peuvent pas être ajoutés (stock, incompatibilité)  
THEN ces extras apparaissent grisés/désactivés

### US 5 — Exclure des ingrédients

**AC 5.1 — Exclusions s'affichent avec cases à cocher**  
GIVEN je suis dans le modal de customisation  
WHEN le plat a des ingrédients exluables  
THEN je vois une section "Exclusions" avec des cases à cocher (pas d'oignon, pas de sauce, etc.)

**AC 5.2 — Plusieurs exclusions peuvent être cochées**  
GIVEN je suis dans la section Exclusions  
WHEN je coche plusieurs ingrédients à exclure  
THEN toutes les exclusions restent cochées

**AC 5.3 — Exclusions n'affectent pas le prix**  
GIVEN j'ai coché une ou plusieurs exclusions  
WHEN je regarde le prix total  
THEN le prix ne change pas (exclusions sont gratuites)

### US 6 — Voir le prix mis à jour en temps réel

**AC 6.1 — Prix initial affichage correct**  
GIVEN j'ouvre le modal pour un plat à €10  
WHEN aucune option n'est sélectionnée  
THEN le prix affiche €10 (prix de base)

**AC 6.2 — Prix se met à jour au changement de taille**  
GIVEN un plat à €10 (M) avec L à +€2  
WHEN je passe de M à L  
THEN le prix passe de €10 à €12 en temps réel

**AC 6.3 — Prix se met à jour avec extras**  
GIVEN un plat à €10 avec extras à +€1.50 chacun  
WHEN je sélectionne 2 extras  
THEN le prix passe de €10 à €13 en temps réel

**AC 6.4 — Prix avec taille + extras**  
GIVEN un plat à €10 (M), L à +€2, extras à +€1.50  
WHEN je sélectionne L et 1 extra  
THEN le prix affiche €13.50 (10 + 2 + 1.50)

**AC 6.5 — Prix persiste si exclusions ajoutées**  
GIVEN j'ai L + 1 extra pour €13.50  
WHEN j'ajoute une exclusion  
THEN le prix reste €13.50

### US 7 — Ajouter le plat customisé au panier

**AC 7.1 — Bouton "Ajouter au panier" valide**  
GIVEN je suis dans le modal avec options sélectionnées  
WHEN je clique sur "Ajouter au panier"  
THEN le plat s'ajoute au panier avec toutes les options sélectionnées

**AC 7.2 — Confirmation visuelle d'ajout**  
GIVEN j'ai cliqué sur "Ajouter au panier"  
WHEN l'action réussit  
THEN un toast/notification confirme "Plat ajouté au panier" et le modal se ferme

**AC 7.3 — Panier se met à jour**  
GIVEN le plat s'ajoute au panier  
WHEN je navigue vers mon panier  
THEN le nombre d'articles et le total reflètent le nouvel ajout

**AC 7.4 — Erreur réseau**  
GIVEN j'essaie d'ajouter un plat au panier  
WHEN la connexion réseau échoue  
THEN un message d'erreur s'affiche et le modal reste ouvert avec mes sélections préservées

### US 9 — Voir les customisations dans le panier

**AC 9.1 — Customisations affichées dans le panier**  
GIVEN j'ai ajouté un plat customisé au panier  
WHEN je consulte mon panier  
THEN le plat affiche clairement : nom + taille + extras + exclusions

**AC 9.2 — Exemple affichage**  
GIVEN un plat "Burger" avec L + Bacon + Fromage extra + Pas d'oignon  
WHEN je regarde le panier  
THEN j'affiche : "Burger (L, +Bacon, +Fromage extra, sans oignon)"

**AC 9.3 — Prix corrects dans le panier**  
GIVEN j'ai customisé un plat à €13.50  
WHEN je regarde le panier  
THEN le prix affiché correspond au prix customisé (pas le prix de base)

### US 10 — Modifier ou retirer les customisations depuis le panier

**AC 10.1 — Supprimer un plat du panier**  
GIVEN un plat customisé est dans mon panier  
WHEN je clique sur "Supprimer"  
THEN le plat disparaît et le total du panier se met à jour

**AC 10.2 — Ré-ajouter avec d'autres options**  
GIVEN j'ai supprimé un plat du panier  
WHEN je retourne au menu et clique sur le même plat  
THEN le modal s'ouvre avec les options par défaut (pas mes anciennes sélections)

### US 11 — Découvrir les options (New User)

**AC 11.1 — Tooltip au premier usage**  
GIVEN je suis un nouvel utilisateur sur mon premier menu  
WHEN j'interagis avec un plat customisable pour la première fois  
THEN un tooltip/hint indique "Vous pouvez personnaliser ce plat"

**AC 11.2 — Tooltip disparaît après première interaction**  
GIVEN le tooltip a été affiché  
WHEN je clique sur le plat ou ferme le tooltip  
THEN le tooltip ne s'affiche plus pour les plats suivants (enregistré localement)

---

## ⚙️ Management Rules

### Trigger & Éligibilité

- Une option est customisable si elle est associée au plat en base de données
- Les options sont définies au niveau restaurant (chaque resto peut avoir un ensemble différent)
- Les options sont affichées seulement si elles sont **actives** (status = "active" en base)
- Un plat sans options ne déclenche pas le modal de customisation — clique direct → panier

### Données des Options

**Taille :**
- Chaque plat peut avoir 0 à N options de taille (S/M/L/XL, etc.)
- Une taille par défaut est définie en base
- Chaque taille a un surcoût fixe (ex: M = +€0, L = +€2, XL = +€3)

**Extras :**
- Chaque plat peut avoir 0 à N extras disponibles
- Chaque extra a un prix fixe (ex: +€1.50)
- Un extra peut être marqué "indisponible" (stock) → désactivé dans le modal
- **Maximum 5 extras** peuvent être sélectionnés par plat
- Si l'utilisateur essaie de cocher un 6e extra → message d'alerte "Maximum 5 extras atteint"
- Aucune autre limite de sélection

**Exclusions :**
- Chaque plat peut avoir 0 à N ingrédients exluables
- Les exclusions n'affectent pas le prix
- Aucune limite de sélection

### Calcul du Prix

- Prix final = Prix plat de base + Surcoût taille + (Somme des extras sélectionnés)
- Exclusions n'impactent pas le prix
- Le prix s'affiche et se recalcule **en temps réel** à chaque changement d'option
- Les prix affichent **toujours les décimales** (€13.50, pas €14)
- Calcul : arrondi à 2 décimales après chaque opération

### Affichage dans le Panier

- Format : `[Nom plat] ([Taille], [+Extra1], [+Extra2], [sans Ingrédient1], [sans Ingrédient2])`
- Exemple : `Burger (L, +Bacon, +Fromage extra, sans oignon)`
- Ordre d'affichage : Taille → Extras (avec +) → Exclusions (avec "sans")

### Suppression & Ré-ajout

- Quand un plat est supprimé du panier, ses customisations sont **perdues**
- Ré-ajouter le même plat depuis le menu ne restaure **pas** les anciennes customisations
- À chaque nouveau clic, les options reviennent à leur état par défaut

### Extras devenant indisponibles

- Si un extra devient out-of-stock pendant que le modal est ouvert :
  - L'extra est immédiatement **désactivé** (grisé, non cliquable)
  - Message d'info : "Cet extra n'est plus disponible" apparaît sous l'extra
  - Si cet extra était déjà sélectionné → il est **auto-décroché** et un toast confirme "Bacon n'est plus disponible, retiré de vos options"

### Tooltip Découverte (New User)

- Le tooltip "Vous pouvez personnaliser ce plat" s'affiche **une seule fois** pour chaque utilisateur
- Stockage : flag local (localStorage) `customization_tooltip_shown = true` après première fermeture
- Le tooltip disparaît aussi si l'utilisateur clique sur le plat (ouverture modal)

### Permissions & Accès

- Tous les utilisateurs authentifiés peuvent customiser les plats
- Les utilisateurs non-authentifiés voient les plats sans options (ou redirection login)

### Erreurs & Validation

- Si un extra devient indisponible (stock vide) **après** sélection → message d'alerte avant ajout au panier
- Si une option est supprimée en base pendant le modal ouvert → recharger le modal automatiquement
- Si l'ajout au panier échoue → garder le modal ouvert avec les options préservées

### Plats identiques avec customisations différentes

- Les plats identiques avec des customisations différentes restent **séparés** dans le panier (pas de fusion)
- Chaque ligne du panier est une instance unique

---

## 🧀 Edge Cases

**EC 1 — Plat sans aucune option**  
Si un plat n'a aucune option (pas de taille, pas d'extras, pas d'exclusions), alors le clic sur le plat ajoute directement au panier sans ouvrir le modal.

**EC 2 — Options deviennent indisponibles pendant la customisation**  
Si un extra est coché, puis devient out-of-stock avant que l'user clique "Ajouter au panier", alors l'extra est auto-désactivé, un message prévient l'utilisateur, et le prix se recalcule automatiquement.

**EC 3 — Fermeture du modal et ré-ouverture**  
Si j'ouvre le modal, sélectionne L + 2 extras, puis ferme sans ajouter, alors à la ré-ouverture du modal (même plat), les options reviennent à leur état par défaut (pas de mémoire).

**EC 4 — Utilisateur atteint le max d'extras (5)**  
Si j'ai 5 extras sélectionnés et que j'essaie de cocher un 6e, alors un message d'alerte bloque la sélection : "Maximum 5 extras atteint".

**EC 5 — Prix avec surcoût taille + extras multiples**  
Si j'ajoute une taille à +€2, puis 3 extras à +€1.50 chacun, alors le prix se met à jour en temps réel : €10 → €12 → €13.50 → €15 → €16.50.

**EC 6 — Ajout au panier échoue (réseau)**  
Si je clique "Ajouter au panier" mais la connexion échoue, alors un message d'erreur s'affiche ("Erreur réseau, veuillez réessayer"), le modal reste ouvert, et toutes mes options sont préservées.

**EC 7 — Même plat avec différentes customisations dans le panier**  
Si j'ajoute un Burger (L, +Bacon) puis un Burger (M, sans oignon), alors le panier affiche 2 lignes distinctes (pas de fusion).

**EC 8 — Utilisateur modifie les options d'un plat depuis le panier**  
Si je veux changer les options d'un plat déjà dans le panier, je dois : supprimer la ligne → ré-ajouter le plat avec nouvelles options.

**EC 9 — Stock réel vs affichage modal**  
Si le restaurant met à jour le stock pendant que le user est dans le modal, la vérification stock se fait à l'ajout seulement (pas de reload auto du modal).

---

## 📱 Workflow Diagrams

**User Flow : Menu Browse → Customization Modal → Cart**

```
Phase 1: Menu Browse
  ↓
Start → Browse dishes (see "Personalizable" badge) → Click dish
  ↓
Phase 2: Customization Modal
  ↓
Modal opens → Select Size/Extras/Exclusions → Price recalculates in real-time
  ↓
Options valid? → No → Adjust options (loop back)
  ↓
Yes → Continue
  ↓
Phase 3: Add to Cart
  ↓
Click "Ajouter au panier" → Customized dish + price saved in cart → Modal closes
  ↓
Cart ✓
```

**Actors covered :** Regular User, New User, System (price calculation, validation)  
**Phases :** Browse menu → Open modal → Customize → Add to cart → View in cart

---

## 📊 Tracking

**3 events pour valider la feature en hackathon :**

| Event Name | Trigger | Properties | KPI |
|---|---|---|---|
| `customization_modal_opened` | User clicks on customizable dish | `dish_id`, `restaurant_id` | Engagement (% of users who discover feature) |
| `customization_options_selected` | User modifies at least 1 option (size, extra, exclusion) | `options_count`, `option_types` (size\|extra\|exclusion), `price_delta` | Feature validation (which option types are used most) |
| `customized_dish_added_to_cart` | User clicks "Ajouter au panier" in modal | `dish_id`, `final_price`, `num_extras`, `has_exclusions` | Conversion (% of modal opens → add to cart), AOV lift (avg price increase vs base) |

**Implementation notes :**
- `option_types` : encode as delimited string ("size,extra,exclusion")
- `price_delta` : difference between final price and base dish price
- `num_extras` : count of selected extras (0-5)
- All events include `user_id`, `session_id`, `timestamp` implicitly

---

## 🚦 Rollout Plan

### Alpha
- **Audience :** Équipe interne (PM, devs, designers) + testeurs internes Deliveroo
- **État :** Feature complète mais non polie (logs bruts, pas d'animations, edge cases non gérés)
- **Timeline :** Fin semaine 1
- **Objectif :** Détécter bugs critiques (crash modal, calcul prix buggé, panier dysfonctionnel)

### Beta
- **Audience :** 10-15 utilisateurs réels recrutés (mixed: nouveaux + réguliers)
- **État :** Stable, animations fluides, messages d'erreur clairs
- **Timeline :** Semaine 2 (pendant hackathon)
- **Objectif :** **Feature validation** — valider que users veulent customiser, comprennent le flow, acceptent la pricing
- **Note :** C'est le test utilisateur principal pour la présentation finale

### Stable
- **Audience :** Rollout graduel post-hackathon (10% → 50% → 100%)
- **État :** Complètement testé, documenté, all edge cases handled
- **Objective :** Adoption maximale, stabilité en production

---

## 🧪 Testing Plan

### Flows business-critiques à tester en priorité

**1. Happy path complet** — User browse → click plat → customize (size + 2 extras) → add to cart → voir dans panier
- **Pourquoi c'est critique :** C'est le parcours 80% des users
- **QA checklist :** Modal ouvre, prix se recalcule en temps réel, plat apparaît dans panier avec toutes les customisations

**2. Pricing validation** — Add 1 taille (M→L +€2) + 2 extras (+€1.50 chacun) = €10 → €15
- **Pourquoi c'est critique :** Acceptation du pricing = clé de conversion
- **QA checklist :** Prix affichage correct, pas de bug arrondi, pas de duplication de surcoût

**3. Edge case : Max extras (5)** — User sélectionne 5 extras, tente d'en ajouter un 6e → message d'alerte bloque
- **Pourquoi c'est critique :** Validez la limite métier
- **QA checklist :** Message clair, no UX friction, extras non ajouté

**4. Error handling : Réseau échoue à l'ajout** — Click "Ajouter au panier" → connexion timeout → modal reste ouvert, données préservées
- **Pourquoi c'est critique :** Users ne perdent pas leur travail
- **QA checklist :** Toast d'erreur clair, retry possible, pas de data loss

### Flows non-critiques (à tester mais pas bloquants)

- Multi-add (même plat 2x avec persos différentes) — non crucial pour hackathon (V2)
- Modification depuis panier (suppression + ré-ajout fonctionne) — important mais pas bloquant si le delete marche
- Tooltip "New User" s'affiche une seule fois — UX nice-to-have, pas business-critical

### Axes de test

**1. Fonctionnalité core** — Pas de bug bloquant
- **Scenario :** Happy path + max extras + réseau error
- **Validation :** Tous les AC passent

**2. Tracking** — Events fire avec les bonnes properties
- **Scenario :** Open modal → select options → add to cart
- **Validation :** 3 events capturés avec properties correctes

**3. UX** — Pas d'étape confuse, pas de loading issue
- **Scenario :** Test avec 5 users (hackathon panel) — observe fluidité modal, clarté du pricing, compréhension du flow
- **Validation :** 80%+ des users complètent le flow sans aide

---

## 📋 Decisions & Constraints

| Decision | Rationale |
|----------|-----------|
| Tous les plats customisables | Flexibilité maximale, pas de cas spéciaux |
| Size > Extras > Exclusions (MVP) | Priority: taille la plus demandée, puis extras payants, exclusions gratuites en bonus |
| Prix fixe, pas de combos | Simplify for hackathon; dynamic pricing en V2 |
| Max 5 extras | Limite métier pragmatique, évite les commandes impossibles |
| Panier: pas de modification in-place | Supprimer + ré-ajouter = flow simpler pour MVP |
| 3 events de tracking | Balance: capture le funnel complet sans surcharge data |
| Alpha/Beta/Stable rollout | Standard post-hackathon; hackathon = Quick Win + MVP validation |

---

**Spec Version:** 1.0  
**Next Steps:** Créer prototype fonctionnel → Tests utilisateurs en Beta → Itération  
