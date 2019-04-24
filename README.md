## a) Niveau facile

# Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ?
--> Album.count

# Qui est l'auteur de la chanson "White Room" ?
--> 

# Quelle chanson dure exactement 188133 milliseconds ?
--> Track.find_by(duration: 188133).title

# Quel groupe a sorti l'album "Use Your Illusion II" ?
--> ALbum.find_by(title: "Use Your Illusion II").artist


## b) Niveau Moyen

# Combien y a t'il d'albums dont le titre contient "Great" ? (indice)
--> Album.where("title LIKE ?", "%great%").count

# Supprime tous les albums dont le nom contient "music".
--> Album.where("title LIKE ?", "%music%").destroy_all

# Combien y a t'il d'albums écrits par AC/DC ?
--> Album.where(artist: "AC/DC").count

# Combien de chanson durent exactement 158589 millisecondes ?
--> Track.where(duration: 158589).count


## c) Niveau Difficile

# puts en console tous les titres de AC/DC.
--> Track.where(artist: "AC/DC").each do |t|
      puts t.title
    end

# puts en console tous les titres de l'album "Let There Be Rock".
--> Track.where(album: "Let There Be Rock").each.each do |t|
      puts t.title
    end

# Calcule le prix total de cet album ainsi que sa durée totale.
--> prix = 0
    durée = 0
    Track.where(album: "Let There Be Rock").each.each do |t|
      prix = prix + t.price
      durée = durée + t.duration
    end

# Calcule le coût de l'intégralité de la discographie de "Deep Purple".
--> prix = 0
    
    Track.where(artist: "Deep Purple").each do |t|
      prix = prix + t.price
    end

# Modifie (via une boucle) tous les titres de "Eric Clapton" afin qu'ils soient affichés avec "Britney Spears" en artist.
--> Track.where(artist: "Eric Clapton").each do |t|
      t.update(artist: "Britney Spears")
    end