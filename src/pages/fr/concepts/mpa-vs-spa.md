---
layout: ~/layouts/MainLayout.astro
title: MPAs vs. SPAs
description: "Il est essentiel de comprendre les compromis entre les architectures d'applications multi-pages (MPA) et d'applications monopages (SPA) pour comprendre ce qui différencie Astro des autres frameworks web."
i18nReady: true
---

Il est essentiel de comprendre les compromis entre l'architecture d'une application multi-page (MPA) et d'une application monopage (SPA) pour comprendre ce qui différencie Astro des autres frameworks web comme Next.js et Remix.

## Terminologie

**Une application multi-pages (AMP)** est un site web composé de plusieurs pages HTML, dont la plupart sont rendues sur un serveur. Lorsque vous naviguez vers une nouvelle page, votre navigateur demande une nouvelle page de HTML au serveur. **Les cadres traditionnels d'AMP comprennent également Ruby on Rails, Python Django, PHP Laravel, Wordpress, Joomla, Drupal et les constructeurs de sites statiques comme Eleventy ou Hugo.

**Une application monopage (SPA)** est un site Web composé d'une seule application JavaScript qui se charge dans le navigateur de l'utilisateur et rend ensuite le HTML localement. Les SPA peuvent *également* générer du HTML sur le serveur, mais les SPA sont uniques dans leur capacité à exécuter votre site Web en tant qu'application JavaScript dans le navigateur pour rendre une nouvelle page de HTML lorsque vous naviguez. Next.js, Nuxt, SvelteKit, Remix, Gatsby et Create React App sont tous des exemples de frameworks SPA.

## Astro vs. les autres MPAs

Astro est un framework MPA. Cependant, Astro est également unique par rapport aux autres frameworks MPA. Sa principale différence est qu'il utilise JavaScript comme langage serveur et comme moteur d'exécution. Les frameworks MPA traditionnels vous obligent à écrire un langage différent sur le serveur (Ruby, PHP, etc.) et le JavaScript sur le navigateur. Dans Astro, vous vous contentez toujours d'écrire JavaScript, HTML et CSS. Ainsi, vous pouvez rendre vos composants d'interface utilisateur (comme React et Svelte) à la fois sur le serveur et sur le client.

Le résultat est une expérience de développement qui ressemble beaucoup à Next.js et à d'autres frameworks Web modernes, mais avec les caractéristiques de performance d'une architecture de site MPA plus traditionnelle.

## MPAs vs. SPAs

Il y a trois différences principales à prendre en compte lorsque l'on compare les MPA et les SPA :

#### Rendu du serveur (MPA) vs. rendu du client (SPA)

Dans les MPA, la plupart du HTML de votre page est rendu sur le serveur. Dans les SPA, la plupart du HTML est rendu localement en exécutant JavaScript dans le navigateur. Cela a un impact considérable sur le comportement, les performances et le référencement du site.

Le rendu de votre HTML dans le navigateur peut sembler être l'option la plus rapide par rapport à la demande d'un serveur distant. Cependant, c'est le contraire qui est vrai. Un SPA sera toujours plus lent au premier chargement de la page qu'un MPA, à moins que le rendu du serveur ne soit utilisé. Cela s'explique par le fait qu'un SPA doit télécharger, analyser et exécuter une application JavaScript entière dans le navigateur, juste pour rendre le moindre HTML sur la page. Ensuite, votre SPA devra probablement récupérer des données distantes, ce qui augmentera encore le temps d'attente avant le chargement de la page.

La plupart des frameworks SPA tentent d'atténuer ce problème de performance en ajoutant un rendu de base sur le serveur lors du premier chargement de la page. C'est une amélioration, mais cela introduit une nouvelle complexité due au fait que votre site web peut désormais être rendu de plusieurs façons et dans plusieurs environnements (serveur, navigateur). Cela introduit également un nouveau problème de "vallée étrange" où votre site semble chargé (HTML) mais ne répond pas car la logique JavaScript de l'application est toujours en train de se charger en arrière-plan.

Les MPA rendent tout le HTML sur un serveur distant et ne nécessitent souvent pas beaucoup (voire pas du tout) de JavaScript pour fonctionner. Les MPA offrent donc une expérience de premier chargement beaucoup plus rapide que les SPA, ce qui est essentiel pour les sites Web axés sur le contenu. Mais cela s'accompagne d'un inconvénient : la navigation future dans les pages ne peut pas bénéficier du rendu local, de sorte que les expériences des utilisateurs à long terme ne profiteront pas autant du premier chargement de la page.

#### Routage du serveur (MPA) vs. routage du client (SPA)

Où se trouve le routeur de votre site Web ? Dans un MPA, chaque demande adressée au serveur décide du HTML à utiliser pour répondre, de sorte que la logique de routage réside dans le serveur. Dans un SPA, votre routeur s'exécute localement dans le navigateur et détourne toute navigation pour rendre la nouvelle page sans jamais toucher au serveur.

Il s'agit d'un compromis similaire à celui décrit ci-dessus : Les MPA offrent une expérience de premier chargement plus rapide, tandis que les SPA peuvent offrir un deuxième ou troisième chargement de page plus rapide une fois que l'application JavaScript est entièrement chargée dans le navigateur. 

Les SPA peuvent également offrir des transitions plus puissantes dans la navigation des pages, car ils contrôlent une grande partie du rendu des pages. Pour égaler cette prise en charge, les MPA exploitent des outils tels que Hotwire [Turbo](https://turbo.hotwired.dev/) qui imitent le routage du client en contrôlant également la navigation dans le navigateur. Le HTML est toujours rendu sur le serveur, mais Turbo peut désormais afficher une transition transparente entre les pages, similaire au routage client dans un SPA.

#### Gestion de l'état du serveur (MPA) vs. gestion de l'état du client (SPA)

Les SPA constituent l'architecture supérieure pour les sites Web qui gèrent des états complexes sur plusieurs pages (pensez à Gmail). En effet, un SPA exécute l'ensemble du site Web sous la forme d'une seule application JavaScript, ce qui permet à l'application de conserver l'état et la mémoire sur plusieurs pages. Les expériences interactives axées sur les données, comme les boîtes de réception et les tableaux de bord d'administration, se prêtent bien aux SPA, car le site Web lui-même est intrinsèquement "semblable à une application".

## Les MPA sont-elles meilleures que les SPA ?

Lorsqu'on compare les MPA et les SPA, il n'y a pas de choix "meilleur" ou "pire". Tout se résume à des compromis.

**Astro privilégie les performances et la simplicité des MPA parce que c'est ce qui convient le mieux à notre cas d'utilisation, à savoir les sites Web axés sur le contenu** Les sites Web plus riches en états et en interactions peuvent bénéficier davantage de l'architecture de type application qu'offrent les SPA, au détriment des performances au premier chargement.

:::note[Accessibilité]
Les MPA utilisent l'élément standard `<a>` pour la navigation. Cela permet d'offrir d'importantes fonctionnalités d'accessibilité, comme la gestion des états de focus et l'annonce par défaut des changements d'itinéraire.
:::

## Études de cas

Vous trouverez ci-dessous toutes les comparaisons publiques d'Astro dont nous avons connaissance :

- [Astro vs. SPA (Next.js)](https://twitter.com/t3dotgg/status/1437195415439360003) - 94 % de JavaScript en moins
- [Astro vs SPA (Next.js)](https://twitter.com/jlengstorf/status/1442707241627385860?lang=en) - Chargement 34 % plus rapide
- [Astro vs. SPA (Next.js)](https://vanntile.com/blog/next-to-astro) – Réduction de 65% de l'utilisation du réseau
- [Astro vs SPA (Remix, SvelteKit)](https://www.youtube.com/watch?v=2ZEMb_H-LYE&t=8163s) - "Ce [score Lighthouse] est incroyable."
- [Astro vs Qwik](https://www.youtube.com/watch?v=2ZEMb_H-LYE&t=8504s) - 43% de gain de temps sur le TTI

If you know a public migration or benchmark and don't see it listed here, please create a PR to add it.

## Ressources supplémentaires

Si vous souhaitez en savoir plus, Surma (Google) et Jake Archibald (Google) ont enregistré un excellent échange de vues [sur ce sujet précis](https://www.youtube.com/watch?v=ivLhf3hq7eM).

