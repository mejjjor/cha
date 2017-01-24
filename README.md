# La suite

### Irb

Tout d'abord, un petit outils pratique : `irb`.  
Tapes `irb` dans la console ruby et tu rentrera dans (au sens dedans!) l'intépreteur Ruby. Tu pourra alors taper directement du code :) .Tu valides une ligne par la touche *entrée*. C'est pratique pour tester un truc rapidement !  
Pour sortir, tu tapes `exit`.

### les types primitifs

Les variables contiennent des données (au sens large) qui sont de différents *types* :

- les *string* sont les chaine de caractères : `"une string"` ou encore `"Charlotte"`
- les *int* ou *integer* sont les nombres entier : `-1` ou encore `42`
- les *float* sont les nombres à virgule : `0.25` ou encore `-42.0`
- les *boolean* correspondent à un et un seul *bit* donc 0 ou 1 (ou alors *true* ou *false*). un *boolean* ne peut donc avoir que deux valeurs

Cependant, Ruby n'est pas un langage typé !  
C'est à dire qu'on à pas besoin de préciser de quel type est une variable.  
on écrit juste `answer = 42`. Ruby sait que la variable *answer* est de type *int*.  
Si on fait ensuite `answser += 0.5` alors Ruby transforme automatiquement le type de la variable *answer* en *float*.  
A noté que dans `answer = "4" + "2"`, comme 4 et 2 sont des *string* alors l'opérateur `+` n'aura pas le même effet qu'avec des *int*.

### Les opérateurs

Les opérateurs permettent d'effectuer des opérations.

- l'affectation : `=`. permet d'affecter une valeur à une variable comme dans `answer = 42`
- les comparateurs renvoi un *boolean* (donc *true* ou *false*) sur la comparaison effectué. Ils sont donc souvent (uniquement?) utilisés dans les conditions.
  - supérieur : `>` dans par exemple `10 > 42` renvoi *false*
  - supérieur ou égale : `>=` dans par exemple `42 >= 42` renvoi *true*
  - inférieur : `<` dans par exemple `10 < 42` renvoi *true*
  - inférieur : `<=` dans par exemple `10 <= 42` renvoi *true*
  - le *ET* logique : `&&` dans par exemple `true && false` renvoi *false*
  - le *OU* logique : `||` dans par exemple `true || false` renvoi *true*

Toutes ces opérations peuvent être effectuées entre des variables.

Pour aller plus loin : https://www.tutorialspoint.com/ruby/ruby_operators.htm   
Ce site est vraiment bien mais la doc est un peu rude ! Au moins c'est complet. Mais un conseil, lis pas tout ! (pareil pour les autres liens vers ce site)

### Les structures de controles

Les structures de controles sont des blocs de code qui peuvent être exécutées ou non grâce à des mots clefs. le block se terminent toujours par `end`.

- `if` permet d'executer du code en fonction du résultat d'une condition  
```ruby
if 10 < 42
  puts "10 est plus petit que 42"
end
```
On peut le compléter par un `else` et/ou un `elsif`
```ruby
if 10 > 42
  puts "ça métonnerait !"
elsif 10 = 42
  puts "ça métonnerait aussi !"
else
  puts "si c'est ni plus grand ni égale alors 10 est plus petit que 42 :)"
end
```

Pour aller plus loin : https://www.tutorialspoint.com/ruby/ruby_if_else.htm

### Les boucles

- Il existe différentes boucles :
  - `for`
  - `each`
  - `while`
  - `until`

Je te conseil de ne retenir pour l'instant que `for` et `each`  
par exemple :
```ruby
for i in 0..5
   puts "nombre #{i}/5"
end
```

```ruby
for item in [0, 1, 2, 3, 4, 5]
   puts "nombre #{item}/5"
end
```

```ruby
monTableau = [0, 1, 2, 3, 4, 5]
monTableau.each do |item|
  puts "item: #{item}"
end
```

```ruby
[0, 1, 2, 3, 4, 5].each do |unTruc|
  puts unTruc
end
```
Pour aller plus loin :
  https://www.tutorialspoint.com/ruby/ruby_loops.htm

### Les fonctions

C'est un bloc de code qui peut exécuté à la demande. Une fonction peut prendre des paramètres.
Les fonctions permettent d'appliquer l'un des pricincipes fondateur de la programmation : DRY. Pour "Don't Repeat Yourself".  
A partir de maintenant et de manière générale, le mieux c'est que tu copies les exemples (au clavier si possible) et que tu joues avec !

```ruby
def sayHello
  puts "hello"
end

for i in 0..3
  sayHello
end
```
Avec des paramètres
```ruby
def sayHello (name, surname)
  puts "hello #{name} #{surname}"
end

for i in 0..3
  sayHello("erik", i)
end
```

Pour aller plus loin :  
https://www.tutorialspoint.com/ruby/ruby_methods.htm

### Les tableaux et hashs

- Un tableau contient une suite de valeur et/ou __variable__.

```ruby
monTableau = [0, 1, 2, 42, "what ???", "je pars en couillllleee aahaha"]
```
Pour acceder à un élément du tableau, on donne son index :
```ruby
monTableau = [0, 1, 2, 42, "what ???"]
puts monTableau[3] #vaut 42. En informatique, un index commence à 0
```

- un hash est un ensemble de clef/valeur

```ruby
monHash = ["ville"=>"Paris", "age"=>42, "nom"=>"Smith"]
```
On y accède de la manière suivante :

```ruby
monHash = ["ville"=>"Paris", "age"=>42, "nom"=>"Smith"]
puts monHash.["age"] #vaut 42
```

comme pour un tableau, On peut ajouter, supprimer ou modifier un élément :

```ruby
# modification
monHash = ["ville"=>"Paris", "age"=>42, "nom"=>"Smith"]
monHash.["age"] = 30
puts monHash.["age"]
```
Un hash se parcourt de la manière suivante :

```ruby
monHash = ["ville"=>"Paris", "age"=>42, "nom"=>"Smith"]
monHash.each do |key, info|
  puts "#{key} : #{info}"
end
```
Pour aller plus loin :  
Array : https://www.tutorialspoint.com/ruby/ruby_arrays.htm  
Hash : https://www.tutorialspoint.com/ruby/ruby_hashes.htm

### Exemple, au hasard
```ruby
listeDepartements = []

for dep in 1..95
  listeDepartements << dep.to_s # convertit dep en string et l'ajoute dans la liste
end

dom = ["971", "972", "973", "974", "976"]
listeDepartements.concat(dom) #on ajoute les dom à la liste

# Allez, max 1000 bureaux par departement!
listeNums = []
listeDepartements.each do |dep|
  for bureaux in 1..1000
    listeNums << dep + bureaux.to_s.rjust(5,"0") # rjust permet de completer la string sur 5 digits (au maximum) avec des "0"
  end
end

puts listeNums
```

Si tu executes ce programme, je te rassure, ce qui est lent c'est l'affichage de la console pas la génération de *listNums* !

Tu peux complèter par :
```ruby
require "RestClient"
baseUrl =" https://ouvoter.lesprimairescitoyennes.fr/bureau-vote-primaires/"
listeNums.each do |num|
  RestClient.get(baseUrl+num)
end
```
PS: je te déconseille de mettre un *puts* devant RestClient .. trop de data pour le petit terminal. En revanche pas de problème pour écrire dans un fichier ...

PS2: Essaie de mettre une pause entre chaque *get* de RestClient .. C'est pour éviter de spammer leurs serveurs et qu'ils te banissent !
```ruby
sleep(1) # pause de 1 seconde
```

### Ecrire dans un fichier

```ruby
aFile = File.new("out.csv", "r+")
if aFile
aFile.syswrite("ABCDEF\n") # \n correspond au retour chariot
aFile.syswrite("\tYoupie\n") # \t à tab
else
puts "Unable to open file!"
end
aFile.close
puts "done !"
```
### Lire dans un fichier

```ruby
content = ""
IO.foreach("./out.csv") do |line|
  puts line
  content += line
end
puts content
```

### Parser du html

On va utiliser la gem nokogiri http://www.nokogiri.org/  
donc dans le terminal :
```
gem install nokogiri
```

Dans un fichier parse.rb :
```ruby
require "nokogiri"
doc = File.open("./exemple.html") do |f|
  Nokogiri::HTML(f)
end

puts "liste des li"
puts doc.css('li')

puts "Le 2ème li"
puts doc.css('li')[1]

puts "Le contenu du 2ème li"
puts doc.css('li')[1].content

puts "L'attribut href du du 2ème a dans un li"
puts doc.css("li a")[1]["href"]
```

Le mieux après c'est de lire la doc de nokogiri !


### Divers et ressources

- `gets` permet de demander une valeur à l'utilisateur  
exemple:
```ruby
puts "Enter a value :"
val = gets
puts val
```

- `nil` correspond à null
exemple:
```ruby
val = nil
puts val
```

Listes des mots réservés : https://www.tutorialspoint.com/ruby/ruby_syntax.htm


## Epilogue
Tu peux essayer de faire ton programme !
