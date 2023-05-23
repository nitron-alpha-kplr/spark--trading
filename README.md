# spark--trading

Synthèse du projet SPARK :
Création du interface qui permettra de collecter les cours de bourse en continue sur des valeurs technologiques (APPLE, AMAZON, IBM et MICROSOFT), effectuer des analyses de cours (evolution, correlétion, moyennes mobiles) et créér des visualisations
permetant de représenter les résultats.
La technonologie utilisée sera SPARK (Spark Stream)
Les différent MARKDOWN seront les suivants :
1) Créer un diagramme
2) Récupération de la clés sur Alpha Vantage :
3) Création d'un dossier "Projet_SPARK dans DataBricks afin d'y enregistrer les futurs notebooks
4) On se familiarise aux manipulation des spark stream en "jouant avec les worshop de databricks spark stream
5)on cherche l'url, le token pour initaliser un flux 
Comment récupérér un stream depuis une API rest?
6/ON TESTE les api pour trouver le flux qui nous interresse
ex"
import requests

# replace the "demo" apikey below with your own key from https://www.alphavantage.co/support/#api-key
url = 'https://www.alphavantage.co/query?function=TIME_SERIES_INTRADAY&symbol=IBM&interval=5min&apikey=demo'
r = requests.get(url)
data = r.json()

print(data)"

Il faut hierachiser son étude de projet et construire brique par brique chaque etapes
