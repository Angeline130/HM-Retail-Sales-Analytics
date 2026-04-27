# HM-Retail-Sales-Analytics
Analyse globale de la performance, des produits et du comportement client (2018-2020)

🔗 Liens
Jeu de données : https://www.kaggle.com/competitions/h-and-m-personalized-fashion-recommendations/data

## Problématique Métier
Comment optimiser les stocks et le marketing d'une enseigne de mode en exploitant les données clients et les transactions articles ?

## Architecture des Données 

1. Extraction & Chargement des données : Données issues de Kaggle (Ventes, Clients, Articles).

2. Transformation des données (Power Query) : Nettoyage des valeurs manquantes, formatage des colonnes, suppression des doublons...

3. Modélisation : Schéma en flocon de neige avec une table de faits (Transactions) et des tables de dimensions (Produits, Clients, Temps).
   
<img width="1067" height="697" alt="image" src="https://github.com/user-attachments/assets/a29bdeb8-8ca4-4aa5-bfb4-ff777877c7ef" />

## Focus DAX
Création d'une table contenant toutes les mesures DAX.
On y trouve notamment le chiffre d'affaire total , le nombre de clients , le nombre de clients ayant acheté, le nombre de produits dans le catalgue ainsi que le nombre de produit vendus, le taux d'activation et le pourcentage de client ayant effectués un achat.
Création d'une mesure rapide pour le taux de croissance mensuel (CA MoM%).

Exemple de formule DAX employées :

% attrition_client = [Nb_client_acheteur]/[Nb_client]

CA = SUM(Transactions[price (normalisé)])

Nb_client_acheteur = DISTINCTCOUNT(Transactions[customer_id])

Création également d'une table calculée à l'aide de la formule suivante :

Transaction_client = SUMMARIZE(Transactions,Transactions[Date transaction],Transactions[customer_id],"Nb-article", COUNTROWS(Transactions),"Nb-articles-distinct", DISTINCTCOUNT(Transactions[article_id]),"Total",SUM(Transactions[price (normalisé)]))

Afin de savoir pour chaque client et date de transaction le nombre d'articles achetés et la somme dépensée.

## Analyses et Insights (Ce que vous avez trouvé)

Insights Clients : La tranche 20-30 ans est le segment le plus rentable (43,8% du CA), mais les clients "Active" ne représentent qu'une fraction de la base totale.

Insights Produits : Les catégories "Ladieswear" et "Divided" dominent les ventes en volume tandis que les produits pour bébés représente le plus faible volume de vente. 
Les produits rapportant le plus sont les pantalons.
De plus, les ventes en magasins rapportent plus que les ventes en lignes.
Une saisonnnalité des ventes est observée. Elles sont plus nombreuses en Septembre et de Mars à Juin. Le pic de septembre correspond probablement aux stratégies de "Back to school" ou de changement de collection.
Enfin, les produits les plus vendus en quantité ne sont pas ceux qui rapportent le plus d'argent.

### 📊 Aperçu du Dashboard
Ce rapport Power BI se décompose en trois axes stratégiques comme le montre la page d'accueil permettant la navigation entre nos 3 grands axes :
<img width="1082" height="607" alt="image" src="https://github.com/user-attachments/assets/f5ca5bdb-6d24-4a89-8ff2-138314a4ffaa" />

1. Performance Commerciale : Analyse du CA global (884,65K) et suivi des tendances temporelles par canal (Online vs Store).

<img width="1076" height="608" alt="image" src="https://github.com/user-attachments/assets/5fd4f09f-6767-4546-8340-cbd7470235d9" />

2. Analyse Produit : Identification des articles "Top sellers" et analyse du taux d'activation (99,06%).

<img width="1078" height="601" alt="image" src="https://github.com/user-attachments/assets/f71be215-bcc6-41b7-94da-568ea25a66cf" />

3. Analyse Client : Étude de la base de 1,37M de clients, segmentation par tranche d'âge et statut de fidélité.

<img width="1076" height="603" alt="image" src="https://github.com/user-attachments/assets/11e005f6-8e49-4398-b7fe-59a1ef6ca723" />

🛠️ Compétences techniques démontrées
Modélisation de données : Création d'un schéma en étoile pour lier les ventes, les produits et les clients.
DAX (Data Analysis Expressions) : Création de mesures pour le panier moyen (0,10) et la variation du CA.
Data Visualisation : Utilisation de Treemaps, graphiques de rubans (Ribbon charts) pour la fréquentation, et jauges de KPI.

## Comment utiliser ce report

Instruction : "Téléchargez le fichier .pbit et connectez les sources de données pour visualiser le rapport."
