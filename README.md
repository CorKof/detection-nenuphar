# Detection-nenuphar
De l'IA pour détecter les nénuphars et mesurer leur superficie à partir d’images satellites d’étangs

## Contexte

* **Rééquilibrer la présence de nénuphars dans les étangs** est une préoccupation pour les Fédérations de Pêche, les collectivités et les particuliers
propriétaires puisque en avoir trop a des conséquences environnementales.
* Partant de ce constat, j’ai décidé de **créer un algorithme détectant les nénuphars et leur superficie à partir d’images satellites**

### **Avantages de la présence de nénuphars dans les étangs**

* **Réduction de la prolifération des algues** en protégeant l’eau des rayons
du soleil et en absorbant les nutriments nécessaires à l’alimentation des
algues

* **Protection des poissons en apportant de l’ombre,** évitant à l'eau de se
réchauffer trop vite lors des chaudes journées estivales


### **Risques liés à une prolifération trop abondante**

* **Risque de prolifération de moustiques** par une hausse de la
température
* **Risque de destruction des espaces aquatiques** par une réduction de la
pénétration de la lumière et de l’oxygène dans l’eau


## Résultats obtenus

L’algorithme encadre en vert chaque nénuphar qu’il identifie et calcule leur superficie que l’on peut retrouver dans le texte en dessous des images

<img width="582" alt="res1" src="https://user-images.githubusercontent.com/71772293/122955650-91c7d800-d380-11eb-9b9b-7bc7407181ca.PNG">
<img width="590" alt="res2" src="https://user-images.githubusercontent.com/71772293/122955828-c045b300-d380-11eb-89fd-951155727c49.PNG">
<img width="601" alt="res3" src="https://user-images.githubusercontent.com/71772293/122955921-d8b5cd80-d380-11eb-8fb8-7ba5b291bcac.PNG">

## Présentation générale des modèles utilisés

### **1er modèle** : détection des nénuphars

Ce modèle détecte les nénuphars présents et les encadre

**Préparation des données**

* Récupération de 150 images satellites d’étangs avec présence de nénuphars sur [Géoportail](https://www.geoportail.gouv.fr/)
* Encadrement de chaque zone de nénuphar via LabelImg, un logiciel open source
* Utilisation de la librairie Img-aug pour augmenter le nombre d’images et en obtenir 7 200. Utilisation de Script pour ajuster les encadrements de
chaque image
**Création et entrainement du modèle**

* Utilisation de Google Colab pour entraîner le modèle dans le Cloud
* Entrainement : 4 000 itérations du modèle réalisées avec test d’efficacité toutes les 500 itérations
* Graphique de la fonction de perte (loss function) ci-dessous


## **2nd modèle** : détection de l’échelle 

Ce modèle détecte l’échelle de chaque image satellite

**Préparation des données**

* Récupération d’images satellites avec échelle : images d’étangs, forêts, terrains, etc. sur [Géoportail](https://www.geoportail.gouv.fr/)
* Encadrement de chaque échelle, l’échelle étant constituée d’une barre et d’un nombre exprimé en mètre
* Utilisation de 5 classes : 1 pour la barre d’échelle et 4 pour les 4 nombres exprimés en mètre : 5, 10, 20 et 50

**Création et entrainement du modèle**

* Utilisation de la librairie Img-aug pour augmenter le nombre d’images et en obtenir 950
* Modification des images pour zoomer sur l’échelle
* Utilisation de Google Colab pour entraîner le modèle dans le Cloud
* Entrainement : 2 000 itérations du modèle réalisé
* Graphique de la fonction de perte (loss function) ci-contre


## Technologie utilisée

* Transfert learning
* YoloV3, YoloV5
* images augmentation
* Numpy, Pandas, Opencv2, ...
* Cloud, Drive (google colab) 














