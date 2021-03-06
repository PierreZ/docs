---
title: Configurer les groupes d’objets NSX
slug: configurer-les-groupes-d-objets-nsx
legacy_guide_number: '7766837'
section: NSX
---




Les groupes d'objets permettent d'inclure plusieurs paramètres permettant ensuite de gérer des règles sur ces groupes qui s'appliqueront ensuite à tous les services pour lesquelles ces règles correspondent.

Pour réaliser ce guide, il vous faut [accéder à l'interface de gestion NSX]({legacy}7766338).

Les groupes peuvent être gérées de manière ponctuelle au niveau de la source ou destination des règles de Firewall par exemple, mais il peut être plus simple de la gérer de manière globale via la partie "NSX Manager".

![](images/NSXHome.PNG){.thumbnail}

Vous pouvez cliquer sur l'IP de votre NSX Manager et vous rendre dans la partie "Manage" pour avoir accès à l'onglet "Grouping Objects".

![](images/GroupingObjects.PNG){.thumbnail}

Les groupes suivants peuvent être configurés :

Security Group
--------------

Les groupes de sécurité permettent de créer des groupes d'objet qui correspondront à une règle spécifique définie dans le groupe.

Vous pouvez ajouter un groupe de sécurité en cliquant sur le bouton "Add" (petit "+" vert).

![](images/AddSecurityGroup.PNG){.thumbnail}

Vous pouvez ensuite sélectionner les membres de critères. Dans l'exemple ci-dessous, le groupe inclura toutes les VMs dont le nom dans vSphere contiendra "Test" ou "Trial". Vous pouvez cliquer sur "Add" pour ajouter des règles au membre.

Le champ "Match" permet de définir si toutes les règles doivent correspondre pour l'appartenance au groupe ou si un seul critère est nécessaire.

Les critères peuvent se baser sur des informations différents. Ainsi, un critère peut se baser sur le contenu du nom d'une VM, et un second dont le nom commence par des caractères particulier.

![](images/DefineDynamicMembership.PNG){.thumbnail}

L'étape suivante permet d'indiquer si d'autres objets sont inclus dans cette règle de sécurité, qu'ils correspondent ou non aux critères configurés précédemment.

Les objets peuvent être d'autres groupes de sécurité, des cluster, et biens d'autres choses.

Cette étape est optionnelle, vous pouvez directement poursuivre si vous ne souhaitez pas d'exception.

![](images/selectObjectToInclude.PNG){.thumbnail}

L'étape suivante est similaire mais pour que des éléments ne soient pas ajoutées au groupe de sécurité même si ils répondent aux critères.

![](images/SelectObjectsToExclude.PNG){.thumbnail}

Obtenez finalement le résumé du groupe de sécurité que vous pouvez vérifier avant de valider.

![](images/ReadyToComplete.PNG){.thumbnail}

Le groupe de sécurité est fonctionnel et peut être utilisé en tant que source ou destination d'une règle de firewall.

![](images/Result.PNG){.thumbnail}

IP Sets
-------

Les "IP Sets" permettent de créer des groupes d'IPs qui peuvent ensuite être utilisés dans des règles de firewall ou de NAT ensuite.

Rendez-vous dans la partie "IP Sets" pour avoir accès au tableau associé.

![](images/IPSets.PNG){.thumbnail}

Cliquez sur "Add" (petit "+" vert) pour ajouter un groupe d'IP. Vous pouvez renseigner les champs suivants :

- Name : Le nom du groupe d'IP, explicite pour vous afin de différenciez vos différents groupes.
- Description : Une description facultative du groupe afin de les différencier entre eux.
- IP Addresses : Les IPs inclues dans le groupe (IP unique, sous réseau entier ou plage précise en réspéctant la syntaxe rappelée sous le champ).

![](images/NewIPSets.PNG){.thumbnail}

Le groupe est créé.

![](images/SummaryIPSets.PNG){.thumbnail}

MAC Sets
--------

Les "MAC Sets" permettent de créer des groupes d'adresses MAC qui peuvent ensuite être utilisés dans des règles de firewall ensuite.

Rendez-vous dans la partie "MAC Sets" pour avoir accès au tableau associé.

![](images/MACSets.PNG){.thumbnail}

Cliquez sur "Add" (petit "+" vert) pour ajouter un groupe d'adresses MAC. Vous pouvez renseigner les champs suivants :

- Name : Le nom du groupe d'IP, explicite pour vous afin de différenciez vos différents groupes.
- Description : Une description facultative du groupe afin de les différencier entre eux.
- MAC Addresses : Les adresses MAC inclues dans le groupe (au moins deux, séparées par des virgules).

![](images/NewMACSet.PNG){.thumbnail}

Le groupe est créé.

![](images/SummaryMACSets.PNG){.thumbnail}

Service
-------

La partie "Service" vous permet d'avoir accès à une liste prédéfinie de services connus. Vous pourrez par exemple retrouver le service "HTTP" qui correspond au protocole TCP sur port 80 ou encore le service "HTTPS" en TCP sur le port 443.

![](images/Service.PNG){.thumbnail}

Cliquez sur "Add" (petit "+" vert) pour ajouter un service personnalisé. Dans le cas présent, nous ajouterons un port personnalisé pour l'accès en SSH, afin de ne pas utiliser le port 22 par défaut.

Les options avancées permettent, dans l'exemple du TCP, d'ajouter des ports sources pour détailler le type de traffic attendu par ce service.

![](images/AddService.PNG){.thumbnail}

Le nouveau service est maintenant disponible pour la création de règles, par exemple firewall.

![](images/SummaryService.PNG){.thumbnail}

Service Groups
--------------

La partie "Service Groups" vous permet de gérer les services abordés dans la partie précédente, et d'en faire des groupe qui sont complémentaires pour vos utilisations.

![](images/ServiceGroups.PNG){.thumbnail}

Cliquez sur add (petit "+" vert) pour ajouter un groupe de services personnalisé. Cet ajout vous permet de définir les services inclus dans votre groupe de service.

Afin d'ajouter les services au groupe, sélectionnez les dans la colonne de gauche et ajoutez-les dans la colonne de droite.

Via le menu déroulant "Object Type", vous pouvez également inclure des groupes de service dans ce groupe de service plutôt que des services seuls.

Dans l'exemple suivant, nous allons créer un service appelé "Web" permettant de gérer le HTTP et HTTPS simultannément ensuite dans les règles NSX.

![](images/AddServiceGroups.PNG){.thumbnail}

Le groupe de services personnalisés est ensuite disponible.

![](images/SummaryServiceGroups.PNG){.thumbnail}
