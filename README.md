# Authentification twitter 

On commence par récupérer le fichier du challenge (./ch3.pcap)
Puis l'ouvre dans Wireshark
On peut trouver dans ce fichier une requête HTTP 
On retrouve dans l'entête une information sur le mode de connexion après l'avoir ouvert
C'est une authentification Basic dans un format user:password
Wireshark déchiffre pour nous ce chiffrement. 
Ont trouve donc le nom d'utilisateur et le mot de passe correspondant :
usertest:password => Le mot de passe du challenge est donc password


# Javascript -Webpack

Je lance le challenge et je me retrouve sur une page web 
Ensuite j’inspecte la page web et je vais dans source 
J’ouvre "webpack" puis srx et ensuite composants
pour arriver sur YouWillNotFindThisRouteBecauseItIsHidden.vue
Ou je trouve le mot de passe et je le récupère 
Le mot de passe qui est BecauseSourceMapsAreGreatForDebuggingButNotForProduction


# Bluethooth 

Télécharger le fichier du challenge (./ch18.bin)
Il s'agit d'un fichier .bin . Je ne peux l'ouvrir avec le logiciel de traitement de texte
Donc on essayer de le lire en utilisant le package File System de NodeJS

const fs = require('fs')

const data = fs.readFileSync("./ch18.bin")
console.log(data.toString());

En exécutant le script précédent, on peut récupérer un morceaux de texte => GT-S7390G
On remarqur qu'il s'agit d'un modèle de téléphone.	
Ensuite, on essaye d'ouvrir le fichier dans Wireshark
On repère une requête dans laquelle on retrouve le modèle du téléphone précédement trouvé. 
Dans cette même requête on trouve l'adresse mac du téléphone.
Il nous reste juste à convertir notre chaine de caractère (0C:B3:19:B9:4F:C6GT-S7390G) en SHA1 avec un convertisseur en ligne
On obtient le résultat suivant => c1d0349c153ed96fe2fadf44e880aef9e69c122b

#
