---



copyright:
  years: 2018, 2019
lastupdated: "2019-02-20"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:note: .note}
{:table: .aria-labeledby="caption"}

# Tarification de {{site.data.keyword.vsi_is_short}} 
{: #pricing-for-virtual-servers-for-vpc}

{: #vsi-for-vpc-pricing}
{{site.data.keyword.vsi_is_full}} est proposé dans certaines régions avec jusqu'à 62 unités centrales virtuelles et 248 Go de mémoire RAM, pour s'adapter à toutes les charges de travail. Vous êtes facturé en fonction d'un taux horaire uniquement, avec des remises appliquées selon la durée d'exécution de votre instance. Les durées d'utilisation des serveurs virtuels sont calculées à la seconde, aussi bien pour la durée d'utilisation que pour la durée de suspension de votre instance. Par exemple, si votre instance s'exécute pendant 45 minutes et 32 secondes, vous êtes facturé pour 45 minutes et 32 secondes.
{:shortdesc}

## Utilisation prolongée
Alors que les instances sont facturées en fonction d'un taux horaire, plus la durée d'exécution de votre instance est longue, moins le taux est élevé. Au fur et à mesure que vous avancez dans le mois de facturation, vous bénéficiez des remises horaires ci-après. 

| Durée d'utilisation en un mois   | Remise sur la facturation | 
| ----------------------------- | ----------------- | 
| 0 à 20 %                         | tarif normal |                 
| 21 à 40 %                        | 5 %        |                  
| 41 à 60 %                        | 10 %       |                  
| 61 à 80 %                        | 15 %        |                  
| 81 à 100 %                       | 20 % |
{: caption="Tableau 1. Remises différenciées " caption-side="top"}  

Ces remises différenciées permettent une économie de 10 % si vos instances s'exécutent mensuellement et non à l'heure. La remise s'applique uniquement aux taux horaires de base ; elle ne s'applique pas aux frais liés aux logiciels, au stockage, au réseau, et autres. 

<!-- As your workload demands change, you can always increase or decrease the size of your instance. If you resize to a larger instance size, the discounts reset and you pay the regular rate again. If you resize to a smaller instance size, the discounted rate does not reset. You continue to progress through the hourly discount tiers. -->

### Exemple d'utilisation prolongée 
Supposons que vous achetiez une instance de la famille des serveurs virtuels équilibrés, avec 16 unités centrales et 64 Go de mémoire RAM, au tarif de base de 0,0795 $ de l'heure. Au cours du mois, votre tarif décroit comme suit : 

| Durée d'utilisation en un mois   | Remise sur la facturation |  Exemple de prix |
| ----------------------------- | ----------------- | -------- |
| 0 à 20 %                         | tarif normal (0,0795 $) | 116,07 $   |                
| 21 à 40 %                        | 5 %        |   110,27 $  |                 
| 41 à 60 %                        | 10 %       |   104,46 $ |            
| 61 à 80 %                        | 15 %        |  98,66 $   |                
| 81 à 100 %                       | 20 % |       92,86 $     |
{: caption="Tableau 2. Exemple de remises différenciées " caption-side="top"}  

Sur ce modèle, si votre instance s'exécute pendant tout le mois, votre facture totale est de 522,32 $. Les remises permettent d'effectuer une économie de 10 % par rapport au taux horaire. 

## Tarifs de base d'une instance 

Les tarifs de base d'une instance commencent à 0,087 $ de l'heure. Lorsque vous créez un serveur virtuel, vous êtes invité à sélectionner une famille de serveurs virtuels et une configuration de profil. Lorsque vous effectuez votre sélection, le taux horaire associé est affiché dans le tableau. <!-- You can also use the Pricing Calculator to estimate your costs. --> 

## Systèmes d'exploitation inclus 
Les systèmes d'exploitation suivants sont inclus gratuitement :

* L'édition CentOS 7 la plus récente 
* Ubuntu 16.04 LTS, 18.04 (minimal) 
* L'édition Debian 8. la plus récente et 9 la plus récente (minimal)

Des systèmes d'exploitation premium et d'autres modules complémentaires sont disponibles. Leurs prix sont affichés dans le récapitulatif des coûts. 

## Délai de facturation
{: #billing-delay}

Une fois que des serveurs virtuels {{site.data.keyword.vsi_is_short}} ont été mis à disposition, il peut s'écouler jusqu'à six heures avant que les informations de facturation ne soient disponibles. En général, les informations de facturation pour les instances de serveur virtuel sont affichées avec un décalage de six heures. 

## Suspension de la facturation 

Lorsque vous arrêtez une instance, vous n'augmentez pas les coûts pour certaines ressources de calcul. La facturation s'arrête immédiatement lorsque vous arrêtez l'instance. La fonction de suspension de la facturation vous permet de réduire les coûts et d'éviter d'avoir à recréer une instance lorsque vous avez à nouveau besoin de ses ressources. 

Si vous voulez mettre votre infrastructure à l'échelle en fonction des besoins liés aux charges de travail, vous pouvez utiliser la fonction de suspension de la facturation comme alternative plus rapide à la création et à la suppression d'instances.
{:tip}

### Détails de facturation

Il est important de savoir quels sont les coûts qui n'augmentent pas et ceux qui continuent d'augmenter lorsque votre instance de serveur virtuel est arrêtée. 

La facturation est suspendue uniquement lorsque vous arrêtez votre instance de serveur virtuel depuis la console IBM Cloud, l'interface de ligne de commande ou l'API. Si vous mettez arrêtez votre instance de serveur virtuel directement via le système d'exploitation, la facturation n'est pas suspendue pour cette instance.
{:note}

Consultez le tableau ci-dessous pour des détails sur l'impact de la suspension de la facturation sur diverses ressources facturées. 

| Ressource                      | Arrêt de la facturation   | Poursuite de la facturation |
| ----------------------------- | ----------------- | ---------------- |
| Unité centrale virtuelle      |          X        |                  |
| Mémoire RAM                   |          X        |                  |
| Mises à niveau de la bande passante |          X        |                  |
| Licences de système d'exploitation     |          X        |                  |
| Adresses IP flottantes, équilibreurs de charge ou autres offres de mise en réseau associées |                   |         X        |
| Stockage                       |                   |         X        |
{: caption="Tableau 1. Détails de facturation des ressources" caption-side="top"}   

Les durées d'utilisation sont calculées à la seconde, aussi bien pour la durée d'utilisation que pour la durée de suspension de votre instance de serveur virtuel. Même si vous n'avez jamais initié la fonction de suspension de la facturation en arrêtant votre instance, les coûts sont calculés à la seconde pour le cycle de vie de l'instance.
{:note}

#### Suspension de la facturation et remises en cas d'utilisation prolongée 
Pour les remises en cas d'utilisation prolongée, une image suspendue reprend là où l'utilisation s'est arrêtée, au niveau de la remise. En d'autres termes, une remise en fonction de l'utilisation n'est appliquée que pour la durée d'utilisation de l'image, et non pour la durée de suspension de l'image. 

#### Facturation minimale pour l'utilisation 
Un tarif mensuel minimal est facturé pour l'utilisation des instances de serveur virtuel. Si l'utilisation est supérieure à 25 % au cours du cycle de facturation, l'utilisation réelle est facturée. Si elle est inférieure à 25 % du temps d'existence au cours du cycle de facturation, un tarif minimal correspondant à une utilisation de 25 % est appliqué.  

Par exemple, imaginons qu'une instance s'exécute pendant toute la durée du cycle de facturation (720 heures). Au cours de ce cycle de facturation, l'instance a été suspendue pendant 577 heures et exécutée pendant 143 heures. Une utilisation de l'instance de 180 heures (le minimum des heures disponibles au cours de cette période de facturation) est facturée.   

Par contre, imaginons qu'une instance qui a été créée et arrêtée au cours d'un cycle de facturation a été exécutée pendant 400 heures. Au cours de ce cycle de facturation, l'instance a été suspendue pendant 120 heures et exécutée pendant 280 heures. Une utilisation de l'instance de 280 heures sera facturée. 

#### Facture 
Lorsque vous suspendez la facturation pour un serveur virtuel, des modifications sont apportées sur votre facture. Les prix respectifs apparaissent avec des détails relatifs à l'utilisation. Par exemple, vous pouvez voir les ajouts suivants, qui reflètent les heures disponibles, les heures d'utilisation et le nombre total d'heures facturées :

```
Computing instance usage...
RAM usage...
Operating system usage...
```
{:screen}

### Détails des ressources

#### Stockage 

Lorsque vous suspendez la facturation pour une instance de serveur virtuel, le stockage associé est conservé, mais vous ne pouvez pas accéder aux données tant que l'instance de serveur virtuel est arrêtée. Lorsque vous reprenez la facturation pour l'instance, vous pouvez à nouveau accéder à vos données et la facturation normale recommence.

#### Adresses IP

Toutes les configurations de réseau et les adresses IP flottantes (adresses IP privées de la plage de sous-réseaux) sont conservées pendant la suspension de l'instance. 

Vous pouvez voir si votre unité est arrêtée dans la page des détails de l'instance. Pour savoir quand le statut a changé, cliquez sur **Activité** dans le panneau de navigation.  

#### Limitations

Les serveurs virtuels suspendus continuent d'être comptabilisés dans le quota d'unités au niveau de votre compte. 
