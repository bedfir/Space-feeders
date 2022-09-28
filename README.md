# Stratégie de Conception et de Sécurisation d'une application

## Table des matières
 1. [Introduction](#introduction)
 2. [Définitions et recommandations](#définitions-et-recommandations)
 3. [Notre application](#notre-application)
 4. [Sources](#sources)
## Introduction
<!-- Notre introduction en anglais -->



## Définitions et recommandations

<!-- Liste des termes avec définition, recommandations, exemples, couche ntier -->

<!--  Voici un Model

<details>
  <summary>

  ### I'am the HEADER
  
  </summary>

  #### Définition
  - First line.
    - Sub-First line.
  - Second line
  
  #### Recommandations
  - R1 - title of recommandation
    - Content
  - R2
    - Content

</details>

 -->
<details>
  <summary>

  ### Transport Layer Security (TLS)

  </summary>

  #### Définition
  - Transport Layer Security anciennement appelé Secure Socket Layer (SSL) est un protocole cryptographique conçu pour fournir une communications sécurisé sur un réseau informatique.
  - TLS permet de garantir 3 propriété de sécurité, 
    - `Confidentialité` : Personne d'autre ne peut lire la communication parce que elle est chiffré.
    - `Authenticité` : L'identité des participants à la communication peut être vérifier.
    - `intégrité` : Les messages de la communication ne peuvent pas être modifiées en route par un adversaire.
  #### Recommandations
  - R1 - Recommandations de sécurité relatives à TLS: 
    - Il est nécessaire de mettre en œuvre les Recommandations de sécurité relatives à TLS
    pour tout site même si celui-ci ne traite pas d’informations sensibles.
</details>

<details>
  <summary>

  ### L'Hypertext Transfer Protocol (HTTPS) 
  
  </summary>

  #### Définition
  - C'est un protocole de communication client-serveur pout accéder à des ressources sur un serveur web.
  - La mise en place de HTTPS sur un site ou une application web est une garantie de sécurité qui
    repose sur TLS pour assurer la confidentialité, l'authenticité et l’intégrité des informations échangées, ainsi que
    l’authenticité du serveur contacté.
  - les requêtes HTTP contient : une méthode, un cible et la version du protocole, contient également un en-tête.

  
  #### Recommandations
  - R2 - Mettre en œuvre HSTS
    - Il est nécessaire de mettre en œuvre `HSTS` afin de limiter les risques d’attaque de
    type **Man-In-The-Middle** dus à des accès non sécurisés générés par les utilisateurs ou
    par un attaquant.
  - R3 - Surveiller les CT logs
    - Il est recommandé que l’hébergeur ou le responsable d’un site web mette en œuvre
    un processus de surveillance des Certificate Transparency logs afin de détecter et révo￾quer les certificats illégitimes qui correspondent à des domaines sous son contrôle.

</details>


<details>
  <summary>

  ### HTTP Strict Trransort Security (HSTS)
  
  </summary>

  #### Définition
  - indique au navigateur d’utiliser automatiquement HTTPS pour tous les accès au site web.
  - HSTS permet à un site Web d'informer le navigateur qu'il ne doit jamais charger le site à l'aide de HTTP et qu'il doit automatiquement convertir toutes les tentatives d'accès au site à l'aide de HTTP en requêtes HTTPS.
  - Demander au navigateur d’utiliser exclusivement HTTPS pour se connecter au site
    visité et à ses sous-domaines, pour une durée d’un an : 
    ``` Strict−Transport−Securit : max−age =31536000 ; includeSubDomains ; ```
  - PS: HTTPS securise seulement l'echange d'informations il agit uniquement pendant l'échange
  
  #### Recommandations
  - R2 - Mettre en œuvre HSTS
    - Il est nécessaire de mettre en œuvre `HSTS` afin de limiter les risques d’attaque de
    type **Man-In-The-Middle** dus à des accès non sécurisés générés par les utilisateurs ou
    par un attaquant.
  - *Attention*
    - Attention, la pérennité de l’accès en HTTPS est un prérequis indispensable à HSTS, qui rendra l’accès en clair impossible

</details>
 
 
<details>
  <summary>

  ### Certificate Transparency (CT)
  
  </summary>

  #### Définition
  - L'autorité de certification c'est un eco-systeme qui vise à faciliter la détection de certificats frauduleux ou invalides.
  
  #### Recommandations
  - R3 - Surveiller les CT logs
    - Il est recommandé que l’hébergeur ou le responsable d’un site web mette en œuvre
    un processus de surveillance des *Certificate Transparency* logs afin de détecter et révoquer les certificats illégitimes qui correspondent à des domaines sous son contrôle.


</details>


  
<details>
  <summary>

  ### Same-Origin Policy (SOP)
  
  </summary>

  #### Définition
  - c'est un protocole qui restrient dans la communications lorsque ils ont des origine differents.
  - *SOP* est l'une des protections les plus importantes du navigateur.
  - Elle sert à vérifier que les contenus chargés sur la page proviennent du même domaine que celle-ci.
  - Toutes les données doivent provenir de la même source, c'est-à-dire du même serveur. 
  
</details>


</details>

- Content Security Policy (CSP)
  - permet de définir une stratégie de contrôle des accès aux ressources atteignables d’un site web donné par l’application de restrictions sous forme de liste d’au￾torisations (aussi appelée liste blanche).
  - Le principal avantage de définir une Content Security Policy (CSP) est de détecter et d’atténuer les attaques XSS.
  - Elle utilise des méta-éléments ou des en-têtes pour donner le feu vert ou bloquer le contenu chargé sur votre site web.
  - Pour activer CSP, vous devez configurer vos serveurs web afin d'ajouter un en-tête (header) HTTP Content-Security-Policy aux réponses. 
```js
  // Une autre possibilité consiste à utiliser l'élément HTML <meta> pour configurer la règle,
  <meta
    http-equiv="Content-Security-Policy"
    content="default-src 'self'; img-src https://*; child-src 'none';" />
``` 

- http Cookies
  - Un cookie HTTP (cookie web, cookie de navigateur) est un petit ensemble de données qu'un serveur envoie au navigateur web de l'utilisateur. Le navigateur peut alors le stocker localement, puis le renvoyer à la prochaine requête vers le même serveur. Typiquement, cette méthode est utilisée par le serveur pour déterminer si deux requêtes proviennent du même navigateur.
  - Les cookies sont utilisés pour 3 raisons principales :
    - Gestion des sessions : Logins, panier d'achat, score d'un jeu, ou tout autre chose dont le serveur doit se souvenir.
    - Personnalisation : Préférences utilisateur, thèmes, et autres paramètres.
    - Suivi : Enregistrement et analyse du comportement utilisateur.
  - Les entêtes Set-Cookie et Cookie
```js
  // L'entête de réponse HTTP Set-Cookie envoie un cookie depuis le serveur vers le navigateur.
  // cookie simple est défini comme ceci:
  Set-Cookie: <nom-du-cookie>=<valeur-du-cookie>
```

- injection SQL (SQLi)
  - L'injection SQL tire parti des applications web qui ne parviennent pas à valider les entrées utilisateur. Les pirates peuvent transmettre des commandes SQL via l'application web de manière malveillante pour exécution par une base de données principale.
  - L'injection SQL peut obtenir un accès non autorisé à une base de données ou récupérer des informations directement à partir de la base de données. De nombreuses violations de données sont dues à l'injection SQL.
```sql
-- Les pirates utilisent une simple chaîne appelée chaîne magique, par exemple : 
-- Nom d'utilisateur : administrateur
-- Password: anything 'or'1'='1
-- Après avoir cliqué sur le bouton de connexion, la requête SQL fonctionnera comme suit :
"SELECT Count(*) FROM Users WHERE Username=' admin ' AND Password=' anything 'or'1'='1 ' ";
```

- Cross-Site Request Forgery (CSRF) 
  - est une classe d’attaques qui force un utilisateur à exécuter, à son insu, des actions privilégiées sur une application tierce sur laquelle il est au￾thentifié. Ce type d’attaques a lieu lors de la navigation sur un site piégé qui émet des requêtes
  vers un site de confiance, mais vulnérable au CSRF (un mécanisme d’authentification faible qui repose uniquement sur les cookies pour gérer les sessions des utilisateurs).
  - pour se protéger des attaques cross-site request forgery : La méthode recommandée et la plus largement adoptée pour lutter contre les attaques cross-site request forgery consiste à utiliser un token anti-CSRF, ou token de synchronisation qui sera géneré aléatoirement en session par le serveur.


- Cross-Site Scripting (XSS)
  - Il s'agit d'une attaque de site Web courante qui est capable d'affecter le site Web ainsi que les utilisateurs du site Web. Les attaquants utilisent couramment JavaScript pour écrire du code malveillant dans XSS. Le code peut voler les détails des cookies de l'utilisateur , modifier les paramètres de l'utilisateur, afficher divers téléchargements de logiciels malveillants et bien d'autres.
  - Comment puis-je empêcher XSS en PHP ? Filtrez vos entrées avec une liste blanche de caractères autorisés et utilisez des indications de type ou un casting de type. Échappez vos sorties avec des *** htmlentities *** et  ***ENT_QUOTES******  pour les contextes HTML, ou des échappements JavaScript Unicode pour les contextes JavaScript.



  
<details>
  <summary>

  ### Cross-Origin ressources Sharing (CORS)
  
  </summary>

  #### Définition
  - le Cross-Origin Resource Sharing il est en réalité strictement interdit : quiconque appelle un site Web ne doit pas charger d’autres données venant de serveurs externes ! Mais il peut y avoir des exceptions. Si les deux exploitants du site s’entendent sur une coopération, rien ne s’oppose à un accord. Le Cross-Origin Resource Sharing (CORS) régit cette coopération, il est donc important de n'utiliser CORS que dans certains cas particuliers, et de le configurer de manière aussi restrictive que possible.
  - Accepter de partager les ressources entre un ou plusieur origine.
```js
    // hôte A
    /OPTIONS
    Origin: 'http://example.com'
    Access-Control-Request-Method: DELETE
```
```js
    // hôte B
    Access-Control-Allow-Origin: 'http://example.com'
    Access-Control-Allow-Methods: PUT, POST, DELETE
```
[This operation performs a simple exchange between the client and the server, using CORS headers to handle the privileges:](images/simple-req.png)

</details>



## Notre application

<!-- Ce que l'ont va mettre en place et pour quel raison -->

### Client (applicative)

### Serveur (Métier)
### BDD (Données)
## Sources

- Guide ANSSI: RECOMMANDATIONS POUR LA MISE EN ŒUVRE D'UN SITE WEB : MAÎTRISER LES STANDARDS DE SÉCURITÉ CÔTÉ NAVIGATEUR:
  https://simplonline-v3-prod.s3.eu-west-3.amazonaws.com/media/file/pdf/436f5816-a1f0-4795-a722-2046d1181db6.pdf
- GUIDE ANSSI: RECOMMANDATIONS RELATIVES À L'AUTHENTIFICATION MULTIFACTEUR ET AUX MOTS DE PASSE
  https://simplonline-v3-prod.s3.eu-west-3.amazonaws.com/media/file/pdf/6e056f88-eef5-489c-85fe-57c1c58fb165.pdf
- Guide RGPD CNIL de l'équipe de développement
  https://lincnil.github.io/Guide-RGPD-du-developpeur/

