[![endorse](http://api.coderwall.com/runexec/endorsecount.png)](http://coderwall.com/runexec)
### Roov [roo-vee]. Rotten Tomatoes Movie API Wrapper
    
###### API Key Setup
Set your Rotten Tomatoes API key in Roov/core.clj
    
###### Quick Example
        (ns Roov.example
          (:use [Roov.core :only (movieSearch)]))
        
        (defn -main [& args]
        ; Find "The Shinning", 15 results p/page, page 1 
          (println (movieSearch 
                            "The Shinning" 15 1))   
        );-main
    
###### Available Functions
    
      
    (defn movieSearch
      [query page_limit page]
        (httpGET  (str urlMovieSearch
                       "?apikey=" api_key
                        "&q=" (. URLEncoder encode query)
                        "&page_limit=" page_limit
                        "&page=" page)
                 );httpGet 
    );movieSearch
    
    (defn movieAlias
      [imdb_id]
        (httpGET (str urlMovieAlias
                      "?id=" imdb_id
                      "&type=imdb"
                      "&apikey=" api_key))
    );movieAlias
    
    (defn movieSimilar
      ([movie_id]
        (httpGET (str urlMovie
                      "/" movie_id
                      "/similar.jon?apikey=" api_key)))
      ([movie_id page_limit]
        (httpGET (str urlMovie
                      "/" movie_id
                      "/similar.jon?apikey=" api_key
                      "&limit=" page_limit)))
    );movieSimilar
    
    (defn movieReviews
      ([movie_id]
        (httpGET (str urlMovie
                      "/" movie_id
                      "/reviews.json?apikey=" api_key)))
      ([movie_id review_type]
        (httpGET (str urlMovie
                      "/" movie_id
                      "/reviews.json?apikey=" api_key
                      "&review_type=" review_type)))
      ([movie_id review_type page_limit]
        (httpGET (str urlMovie
                      "/" movie_id
                      "/reviews.json?apikey=" api_key
                      "&review_type=" review_type
                      "&page_limit=" page_limit)))
      ([movie_id review_type page_limit page]
        (httpGET (str urlMovie
                      "/" movie_id
                      "/reviews.json?apikey=" api_key
                      "&review_type=" review_type
                      "&page_limit=" page_limit
                      "&page=" page)))
      ([movie_id review_type page_limit page country]
        (httpGET (str urlMovie
                      "/" movie_id
                      "/reviews.json?apikey=" api_key
                      "&review_type=" review_type
                      "&page_limit=" page_limit
                      "&page=" page
                      "&country=" country)))
    );movieReviews
    
    (defn movieClips
      [movie_id]
        (httpGET (str urlMovie
                      "/" movie_id
                      "/clips.json?apikey=" api_key))
    );movieClips
    
    
    (defn castInfo
      [movie_id]
        (httpGET (str urlMovie
                      "/" movie_id
                      "/cast.json?apikey=" api_key))
    );castInfo
    
    (defn movieInfo
      [movie_id]
      (httpGET (str urlMovie
                    "/" movie_id
                    ".json?apikey=" api_key))
    );movieInfo
    
    (defn upcomingDVDs
      ([page_limit]
        (httpGET (str urlList
                      jsonUpcomingDVDs
                      "?page_limit=" page_limit
                      "&apikey=" api_key)))
      ([page_limit page]
        (httpGET (str urlList
                      jsonUpcomingDVDs
                      "?page_limit=" page_limit
                      "&page=" page
                      "&apikey=" api_key)))
      ([page_limit page country]
        (httpGET (str urlList
                      jsonUpcomingDVDs
                      "?page_limit=" page_limit
                      "&page=" page
                      "&country=" country
                      "&apikey=" api_key)))
    );upcomingDVDs
    
    (defn newDVDs
      ([page_limit]
        (httpGET (str urlList
                      jsonNewDVDs
                      "?page_limit=" page_limit
                      "&apikey=" api_key)))
      ([page_limit page]
        (httpGET (str urlList
                      jsonNewDVDs
                      "?page_limit=" page_limit
                      "&page=" page
                      "&apikey=" api_key)))
      ([page_limit page country]
        (httpGET (str urlList
                      jsonNewDVDs
                      "?page_limit=" page_limit
                      "&page=" page
                      "&country=" country
                      "&apikey=" api_key)))
    );newDVDs
    
    (defn currentRelease
      "Current release dvds."
      ([page_limit]
        (httpGET (str urlList
                      jsonCurrentRelease
                      "?page_limit=" page_limit
                      "&apikey=" api_key)))
      ([page_limit page]
        (httpGET (str urlList
                      jsonCurrentRelease
                      "?page_limit=" page_limit
                      "&page=" page
                      "&apikey=" api_key)))
      ([page_limit page country]
        (httpGET (str urlList
                      jsonCurrentRelease
                      "?page_limit=" page_limit
                      "&page=" page
                      "&country=" country
                      "&apikey=" api_key)))
    );currentRelease
    
    (defn topRentals
      ([page_limit]
        (httpGET (str urlList
                      jsonTopRentals
                      "?limit=" page_limit
                      "&apikey=" api_key)))
      ([page_limit country]
        (httpGET (str urlList
                      jsonTopRentals
                      "?limit=" page_limit
                      "&country=" country
                      "&apikey=" api_key)))
    );topRentals
    
    (defn upcomingMovies
      ([page_limit]
        (httpGET (str urlList
                      jsonUpcomingMovies
                      "?page_limit=" page_limit
                      "&apikey=" api_key)))
      ([page_limit page]
        (httpGET (str urlList
                      jsonUpcomingMovies
                      "?page_limit=" page_limit
                      "&page=" page
                      "&apikey=" api_key)))
      ([page_limit page country]
        (httpGET (str urlList
                      jsonUpcomingMovies
                      "?page_limit-" page_limit
                      "&page=" page
                      "&country=" country
                      "&apikey=" api_key)))
    );upcomingMovies
    
    (defn openingMovies
      ([page_limit]
        (httpGET (str urlList
                      jsonOpeningMovies
                      "?limit=" page_limit)))
      ([page_limit country]
        (httpGET (str urlList
                      jsonOpeningMovies
                      "?limit=" page_limit
                      "&country=" country)))
    );openingMovies
    
    (defn boxOffice
      "Top grossing movies"
      ([page_limit]
        (httpGET (str urlList
                      jsonBoxOffice
                      "?limit=" page_limit
                      "&apikey=" api_key)))
      ([page_limit country]
        (httpGET (str urlList
                      jsonBoxOffice
                      "?limit=" page_limit
                      "&country=" country
                      "&apikey=" api_key)))
    );boxOffice
    
    (defn inTheaters
      "Latest movies in theaters"
      ([page_limit]
        (httpGET (str urlList
                      jsonInTheaters
                      "?page_limit=" page_limit
                      "&apikey=" api_key)))
      ([page_limit page]
        (httpGET (str urlList
                      jsonInTheaters
                      "?page_limit=" page_limit
                      "&page=" page
                      "&apikey=" api_key)))
      ([page_limit page country]
        (httpGET (str urlList
                      jsonInTheaters
                      "?page_limit=" page_limit
                      "&page=" page
                      "&country=" country
                      "&apikey=" api_key)))
    );inTheaters
    
