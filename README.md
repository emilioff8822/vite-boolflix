componeneti, partendo dal lavoro precedente di yugioh utilizzo pressoche gli stessi elementi

App.vue: componente principale che gestisce la logica dell'applicazione e il layout.
Header.vue: componente per l'intestazione dell'applicazione.
Search.vue: componente per la ricerca e la selezione del tipo di contenuto.
CardsContainer.vue: componente per visualizzare i risultati della ricerca in forma di card.
Card.vue: componente per le singole card che mostrano i dettagli dei film e delle serie TV.
footer vue: indica il numero di film/serie trovati dalla ricerca


Search bar e select :
in Search.vue, abbiamo due variabili nel componente data: searchText e selectedType. searchText tiene traccia del testo inserito nella barra di ricerca, mentre selectedType tiene traccia dell'opzione selezionata nella casella di selezione.

Quando l'utente digita nella barra di ricerca, il testo viene associato alla variabile searchText attraverso la direttiva v-model lo stesso per la selazione che viene associata alla variabile selectedType, sempre usando v-model.

Quando l'utente clicca sul pulsante "Search", viene chiamato il metodo emitSearch(). Questo metodo emette due eventi personalizzati: "search-input" e "type-selected", con i rispettivi valori di searchText e selectedType.

Nel componente App.vue, questi eventi personalizzati vengono gestiti dai metodi updateSearch() e updateType(), che aggiornano le variabili currentSearch e currentType nel componente data. Successivamente, viene chiamato il metodo getApi() con i valori aggiornati di searchText e type

Il metodo getApi() in App.vue costruisce l'URL per la chiamata API basandosi su searchText e type. In base al valore di type, viene selezionato il corretto endpoint dell'API (movie, tv o multi). Se type è "all", viene utilizzato l'endpoint "multi" per cercare sia film che serie TV.





Generazione immagine card

In Card.vue, creo una proprietà  chiamata posterUrl utilizzando una computed. Questa proprietà calcolata genera l'URL completo dell'immagine combinando l'URL base delle immagini di TMDB, la dimensione desiderata e la parte finale dell'URL passata dall'API.

Nel tag <template> di Card.vue, con un tag <img> all'inizio della car Imposto l'attributo :src dell'elemento <img> per utilizzare la proprietà calcolata posterUrl.

l'immagine del film o della serie TV verrà visualizzata nella card. L'URL completo dell'immagine viene generato dalla proprietà calcolata posterUrl, che combina l'URL base delle immagini di TMDB (https://image.tmdb.org/t/p/), la dimensione desiderata (w342) e la parte finale dell'URL passata dall'API (this.card.poster_path).