# temporal-clustering-retail-analysis
Segmentation temporelle des clients et embedding des produits à partir de données de ventes e-commerce.


## Clustering des clients

Nous avons comparé plusieurs méthodes de clustering pour regrouper les clients selon leur comportement dans le temps :

- **KMeans sans transformation** : crée un cluster géant dominé par les petits acheteurs et isole les très gros clients — peu utile pour la segmentation.
- **KMeans avec `log(1 + dépense)`** : équilibre les distances et distingue clairement deux profils : clients réguliers (B2B) et clients saisonniers (Noël).
- **Agglomératif (Ward)** : confirme cette même structure à deux groupes, plus stable et cohérente.
- **TimeSeriesKMeans (DTW)** : détecte les comportements similaires décalés dans le temps (ex. achats en novembre vs décembre).
- **K-Shape** : regroupe les clients selon la *forme* de leurs dépenses (corrélation temporelle), indépendamment du montant.

### 📊 Résumé

Les méthodes **DTW** et **K-Shape** capturent mieux la **saisonnalité et les motifs temporels**, tandis que **KMeans log** et **Ward** offrent une vision plus simple et exploitable pour la segmentation marketing.
