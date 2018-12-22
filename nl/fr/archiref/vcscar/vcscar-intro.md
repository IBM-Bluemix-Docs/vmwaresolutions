---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-13"

---

# Introduction à l'architecture Concept Cat pour VMware et Skate Advisor

L'architecture de référence ci-après est un “concept car”, autrement dit, un mécanisme qui met en évidence et affiche les technologies permettant de résoudre les problèmes du monde réel. L'architecture “concept car” ne représente en aucun cas un service immédiatement disponible.


L'architecture de référence fournit également les informations suivantes :

-   Fournit une langue commune pour les différentes parties prenantes. 
-   Fournit une implémentation technologique cohérente pour résoudre les problèmes. 
-   Prend en charge la validation de solutions par rapport à une architecture de référence qui fait ses preuves.

-   Encourage le respect de normes, spécifications et modèles communs.


## A propos d'ACME Skate Advisor

Nous avons voulu démontrer qu'il existe véritablement une interaction entre l'intelligence artificielle de Watson et l'apprentissage automatique et à travers elle explorer de manière plus approfondie la culture du skateboard. Nous présentons de façon unique les services et l'infrastructure de cloud disponibles en démontrant les capacités et les évolutions techniques dans ce domaine.
L'implémentation du “concept car” est une extension de l'application Acme Skateboard de démonstration nommée Skate Advisor. Skate Advisor est un outil qui permet aux utilisateurs d'avoir des conversations sur les astuces en matière de skateboard avec un moteur entraîné par Watson. Les citations suivantes représentent un exemple de conversation :

-   "Watson, montre-moi les combinaisons du trick Casper"
-   "Watson, montre-moi les sites communs pour effectuer un trick"
-   "Watson, montre-moi une vidéo du trick Casper"

Acme Skate Advisor exploite Watson Discovery Service pour ingérer des articles, des vidéos, des blogues et d'autres contenus Internet afin de créer une base de données d'enseignements tirés sur les tricks, qui peut être interrogée par l'application.


L'application Skate Advisor est également implémentée sur la plateforme de modernisation des applications, qui fournit des services basés sur le conteneur via {{site.data.keyword.cloud}} Private (ICP) hébergé sur la plateforme {{site.data.keyword.cloud_notm}} for VMware Services. 

L'application Acme Skate Advisor exploite à la fois la plateforme Watson et la plateforme de modernisation des applications.


## Cas d'utilisation

### Démonstration de la modernisation des applications

Faites la démonstration d'une application qui a été déployée sur la plateforme de modernisation des applications.
La plateforme inclut les composants ICP, CAM et NSX déployés sur l'offre VMware vCenter Server on {{site.data.keyword.cloud_notm}}.


### Reconnaissance vocale Watson avec Watson Assistant

L'application Acme Skate Advisor communique avec les utilisateurs via un service speech-to-text et text-to-speech qui est fourni avec la plateforme Watson. 

### Watson Discovery Service - Utilisation et entraînement

L'application Acme Skate Advisor utilise Watson Discovery Service pour garder une trace d'une base de données de tricks pour laquelle une langue de classification est appliquée et les tricks sont reconnus à partir de services en ligne. 

### Utilisation des services Watson

Les services Watson suivants ont été utilisés pour créer l'application Acme Skate Advisor :
-   Watson Text to Speech.
-   Watson Speech to Text.
-   Watson Advisor.
-   Watson Discovery Service.
-   Watson Knowledge Studio.

## Modernisation des applications sur IBM Cloud

La modernisation des applications fait référence au processus de transition d'applications existantes pour utiliser de nouvelles approches de développement et de distribution sur le cloud. Aujourd'hui, les clients recherchent des approches innovantes et efficaces qui les aident à effectuer cette transition en tenant compte de la complexité de leur activité et de leurs applications.

Les pressions économiques imposent des commercialisations plus rapides. Votre patrimoine existant inclut non seulement des applications, mais également des données, des processus, une logique métier et des interfaces utilisateur, qui doivent tous être adaptés aux nouveaux besoins commerciaux.

Les avantages de la modernisation des applications sont les suivants :

- Amélioration de la productivité des développeurs
- Augmentation de l'efficacité opérationnelle
- Réduction du coût lié à la création de nouvelles fonctionnalités
- Extension de la capacité fournie en peu de temps

IBM comprend que dans 70 % des cas, l'adoption d'un cloud privé est motivée par la nécessité de moderniser les environnements d'application. Toutefois, la plupart des organisations envisagent la modernisation des applications de façon progressive, ce qui nécessite un paysage hybride et multi-cloud, dans lequel :

- des applications existantes complexes et monolithiques qui s'exécutent généralement sur des grands systèmes ou des systèmes UNIX demeurent sur site ;
- les environnements x86 utilisés pour des systèmes d'enregistrement (SoR), ou les applications qui sont des charges de travail sensibles à la sécurité ou régulées, sont placés sur une infrastructure virtuelle ou un cloud privé ;
- les applications, telles que SAP ou des applications de calcul hautes performances, consomment des ressources bare metal ;
- les charges de travail sensibles à la sécurité ou certaines charges de travail régulées, qui peuvent être déplacées sur le cloud public, sont déplacées vers des environnements dédiés ;
- les systèmes d'engagement (SoE), tels que Web, mobile, IoT, AI ou Video, sont déplacés vers des clouds publics.

Par exemple, un modèle commun consiste à avoir des applications SoE frontales qui sont déployées en tant que conteneurs avec des bases de données et des logiciels intermédiaires existants déployés sur des machines virtuelles sur un cloud privé.

Etant donné que les besoins métier et en infrastructure informatique sont uniques, une approche de modernisation doit fournir les priorités suivantes :

* Accélérer l'apport de valeur métier
* Réduire les délais de livraison
* Réduire les risques
* Préserver les investissements existants

IBM fournit ce type d'approche pour la modernisation des applications et vous pouvez la personnaliser en fonction de vos besoins métier et technologiques spécifiques. 

Les documents suivants fournissent différentes vues des technologies utilisées dans le parcours de modernisation des applications vers {{site.data.keyword.cloud_notm}} :

* [vCenter Server et {{site.data.keyword.cloud_notm}} Private](../vcsicp/vcsicp-intro.html) - Architecture de référence pour le déploiement des plateformes suivantes :
   - **VMware vCenter Server on IBM Cloud** - vCenter Server est une offre d'{{site.data.keyword.vmwaresolutions_short}} qui est une plateforme basée sur VMware automatiquement mise à disposition sur {{site.data.keyword.cloud_notm}}.
   - **IBM Cloud Private** – ICP est une plateforme applicative pour le développement et la gestion d'applications conteneurisées. ICP est un environnement intégré qui inclut l'orchestrateur de conteneurs Kubernetes, un registre d'images privé, une console de gestion, ainsi que des infrastructures préfabriquées de surveillance et une interface graphique. L'interface graphique vous permet de déployer, gérer, surveiller et mettre à l'échelle vos applications de façon centralisée. 
   - **IBM Cloud Automation Manager** – CAM est une plateforme IaC (infrastructure as code) prête pour l'entreprise qui permet à partir d'un point unique de mettre à disposition des charges de travail basées sur des machines virtuelles, ainsi que des charges de travail Kubernetes en utilisant des modèles qui sont stockés et dont la version est gérée dans un référentiel. 
* [vCenter Server et IBM Kubernetes Service](../vcsiks/vcsiks-intro.html) -  Architecture de référence pour le déploiement des plateformes suivantes :
   - **VMware vCenter Server on IBM Cloud** - vCenter Server est une offre d'{{site.data.keyword.vmwaresolutions_short}} qui est une plateforme basée sur VMware automatiquement mise à disposition sur {{site.data.keyword.cloud_notm}}.
   - **IBM Cloud Kubernetes Service** – IKS est un service géré sur {{site.data.keyword.cloud_notm}} qui utilise Kubernetes comme moteur d'orchestration pour l'automatisation du déploiement, la mise à l'échelle et les opérations de conteneurs d'applications sur un cluster à service exclusif. 
* [Mise en réseau de vCenter Server](../vcsnsxt/vcsnsxt-intro.html) - Met l'accent sur les technologies de réseau utilisées pour l'intégration entre vCenter Server, ICP et IKS, par exemple, NSX-V et Calico, ainsi que sur l'aperçu technologique NSX-T.
* _Guide Concept Car pour VMware et Skate Advisor_ - Cette architecture de référence est un “concept car”, autrement dit, un mécanisme qui met en évidence et affiche les technologies permettant de résoudre les problèmes du monde réel. Nous avons voulu démontrer qu'il existe véritablement une interaction entre l'intelligence artificielle de Watson et l'apprentissage automatique. Au travers de la culture du skateboard, nous illustrons des services de cloud de manière unique. L'implémentation du “concept car” est une extension de l'application Acme Skateboard nommée Skate Advisor. Skate Advisor est un outil qui permet aux utilisateurs d'avoir des conversations sur les astuces en matière de skateboard avec un moteur entraîné par Watson.
* [VMware : Le parcours de modernisation de Stock Trader](../vcscontent/vcscontent-modjourney.html) - Cas d'utilisation de référence qui décrit une application WebSphere Application Server classique qui fait l'objet d'une modernisation à l'aide d'{{site.data.keyword.cloud_notm}} Private, de contenu IBM Middleware, d'{{site.data.keyword.cloud_notm}} Kubernetes Service et de vCenter Server on {{site.data.keyword.cloud_notm}}. Nous sommes tous engagés sur un parcours de cloud et nous sommes tous à différents stades de ce parcours. Au travers d'étapes incrémentielles planifiées par Jane et Todd, respectivement architecte d'application et architecte d'infrastructure de cloud, nous modernisons une application existante nommée Stock Trader. Passez en revue des exemples qui vous permettent de franchir chaque étape de votre parcours, et d'apporter de la valeur à votre entreprise, quelle que soit la taille de chaque étape. Nous nous concentrons sur quatre thèmes : applications, DevOps, intégration et gestion. Ces thèmes sont indissociables pour vous permettre d'atteindre vos objectifs, et de fait, en moderniser un sans vous soucier des autres engendrera des problèmes. 

### Liens connexes

* [Présentation de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)