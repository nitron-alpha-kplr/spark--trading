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

les notions d'indice synthetique et jointure sur le temps pour créeéer sa propre mécanique :

Il faut hierachiser son étude de projet et construire brique par brique chaque etapes
je scrute chaque repertoire de fichier que je veux construire dans databricks
l'idée cest de voir si je suis capable de faire fonctionner un stream correctement
J Y vais progressivement et je cherche a connecter mon stream

SI on veut crééer un "indice synthetique" on utilise par exemple une moyenne (mean)
on va crééer des string pour utiliser nos tickers on va faire la "jointure" sur le temps 
les notions "eventtime et reveal time " c'est l'exchange qui l'a pour avoir l'info en temps reel.
par exemple ecouter 5mn et faire des jointures internes puis on réecoute les flux (on peut merger les flux) puis on fait une jointure avec un id de machine par exemple.
Le fait d'avoir un fichier par valeur on peut avoir un visuel sur chaque flux et on pourra avoir envi d'automatiser l'application
faire une boucle defstream-data
créer des listes de streamall(tickerlist) /des dictionnaires de list/Une list d'objet
    for ticker in tickerlist
    je crée mon dictionnaire 
    !point super important SPARK recoit et lit d'un fichier non distribué de par sa nature distribue il ne va pas ecrire à un seul endroit !
    Delta (repertoire native) est activé par defauts 
    il va falloir structurér le dataframe (struct) ,il faut un schema, l implementer, faire un display le mapper avec une viz et ensuite 
checkpoint pour nommer les fichier? gerer en interne, on ecoute un repertoire en mettant en place des strategies de lecture.

IL faut voir SPARK comme un "moteur". UN JOB esr un calcul parralele et chaque STAGE est une sequence de tache qui peut etre faite en parralele sans avoir a regroupé les données entre ellles. EX: je fais un FILTER la task cest la plus petite unite de travail

il faut vraiment comprendre DF1  +  spark.read. csv(---).FILTER().SORT(                              IMPLICIT
                                                             DF    DF        
                                                             
                        DF1 = [""""]
                        df2 = df1.FILTYER()
                        df3 = df2.SORT()                                  EXPLICIT
                        
                        VOIR NOTIONS DE LINEAGE MAGIE DE LA PROGRAMMATION ORIENTEE OBJET
                        
                        notions SPARK STAND ALONE avec GITPOD SIMPLENODE START SMELL/SCALITER
                        AFFICHAGE REAL TIME DISPLAY
                        GENERATION DE SIGNAUX PROPRES
                        DIFFERENTES TIOMES AGGREGATIONS (TIME WINDOW)
                        streamjoin (stream/STATIC/BATCH)
                        
                        
 En ce qui concerne les formats a utliser a savoir le CSV COMMAT SEPARATE VALUE txt / ON distincte le code ASCI AUQUEL ON ASSIGNE un binaire a chaque caractere - ainsi on deoule un long ruban - ce modéle n'est pas optmiser pour lire une infos-ce nest pas un format dense- si je fais par exemple un feature selection je suis obligé d'aller chercher l info une a une.
 Ainsi PARQUET correspond beaucoup mieux comme format a utiliser binaire compact structuré snapy et indexé stockage colonaire;
