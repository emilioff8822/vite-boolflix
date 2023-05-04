Creo un nuovo componente Search.vue nella cartella components.
Nel file Search.vue, aggiungo un input per la ricerca e una casella di selezione per il tipo di carta.
Utilizzo $emit per inviare l'input di ricerca e il valore della casella di selezione al componente padre (App.vue).
Modifico App.vue per ricevere gli eventi emessi dal componente figlio e aggiorna la chiamata API in base ai valori ricevuti.


currentSearch e currentType in App.vue sono utilizzati per memorizzare i valori correnti di ricerca e tipo che vengono passati al metodo getApi(). Questi valori vengono aggiornati quando gli eventi "search-input" e "type-selected" vengono emessi dal componente Search.vue

searchText e selectedType in Search.vue sono utilizzati per memorizzare i valori inseriti dall'utente nel campo di ricerca e nel menu a discesa del tipo. Quando l'utente fa clic sui pulsanti "Search" o "Reset", questi valori vengono emessi come eventi personalizzati che il componente App.vue ascolta e utilizza per aggiornare currentSearch e currentType.

quindi searchText e selectedType in search.vue memorizzano i valori inseriti dall'utente nel componente Search.vue, mentre currentSearch e currentType in app.vue memorizzano i valori attuali di ricerca e tipo utilizzati dal componente App.vue per effettuare le richieste all'API e aggiornare i risultati delle carte.