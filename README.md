## 🏡 Home (LLM) — Esempi di Utilizzo e Raccomandazioni

In questa sezione vengono mostrati gli esempi d'uso della schermata **Home (LLM)**. Il modello interpreta le query in linguaggio naturale, estrae i parametri di intent e restituisce la ricetta consigliata con la relativa spiegazione e il punteggio ibrido.

---

### 1. Ingrediente Singolo + Stanchezza

![Home LLM - Ingrediente e Stanchezza](assets/Schermata%20del%202026-09-04%2015-48-21.png)

* **Query:** `"Sono stanco, ho soltanto petto di pollo in frigorifero, cosa mi consigli?"`
* **Intent estratto:** `ingrediente: chicken` | `time: -4.0`
* **Risultato:** **My Famous Shredded Chicken** (90 min, 321.5 kcal)
* **Score:** `0.5`
* **Note:** Risultato con spiegazione che sottolinea l'utilizzo prioritario dell'ingrediente segnalato come disponibile.

---

### 2. Dettaglio Ricetta Espanso

![Home LLM - Dettaglio Espanso](assets/Schermata%20del%202026-09-04%2015-48-33.png)

* **Vista UI:** Dettaglio espanso di **My Famous Shredded Chicken** (90 min, 321.5 kcal, score `0.5`).
* **Ingredienti:** `chicken breasts`, `chicken broth`
* **Preparazione:** Scheda integrata con i 10 step di preparazione.
* **Note:** Dimostrazione dell'integrazione dei dettagli completi della ricetta consultabili direttamente all'interno della schermata Home.

---

### 3. Tempo e Dieta

![Home LLM - Tempo e Dieta](assets/Schermata%20del%202026-09-04%2015-49-28.png)

* **Query:** `"Ho molto tempo per cucinare, sono vegano"`
* **Intent estratto:** `time: +5.0` | `tag: vegan` | `profilo: balanced`
* **Risultato:** **Pinto Beans And Rice In A Crock Pot Or On Stove Top** (185 min, 1898.7 kcal)
* **Score:** `0.2`

---

### 4. Vincoli Calorici e Tempo
![Home LLM - Vincoli Calorici e Tempo](assets/Schermata%20del%202026-09-04%2015-50-40.png)

* **Query:** `"Voglio provare qualcosa di nuovo, sotto le 600 calorie e con una preparazione di al massimo 30 minuti"`
* **Intent estratto:** `modification: +3.0` | `time: -4.0` | `max_calories: 600` | `profilo: balanced`
* **Risultato:** **Sassy S Beef And Broccoli** (20 min, 445.4 kcal)
* **Score:** `0.4574`
* **Note:** Rispetta contemporaneamente sia il vincolo calorico (< 600 kcal) che il limite di tempo (< 30 min).

---

### 5. Query Economica / Leggera

![Home LLM - Query Economica](assets/Schermata%20del%202026-09-04%2015-52-21.png)

* **Query:** `"Ho pochi soldi, voglio qualcosa di fresco ma non troppo calorico"`
* **Intent estratto:** `body: -5.0` | `price: -5.0`
* **Risultato:** **Funfetti Cookies** (35 min, 83.5 kcal)
* **Score:** `0.6`
* **Note:** Mostra un caso limite in cui l'interpretazione congiunta dei termini *"fresco"* ed *"economico"* porta alla scelta di un dolce leggero a basso costo per porzione.

---

### 6. Query Mood Senza Vincoli Stringenti

![Home LLM - Query Mood](assets/Schermata%20del%202026-09-04%2015-53-57.png)

* **Query:** `"Voglio qualcosa di leggero, ho molti soldi a disposizione ma sono stanco"`
* **Intent estratto:** `body: -3.0` | `price: +5.0` | `time: -4.0`
* **Risultato:** **Quesadillas For One Or Two** (15 min, 394.3 kcal)
* **Score:** `0.6`
* **Note:** Generazione di una spiegazione LLM coerente con l'insieme dei parametri estratti dalla query.

## 🏆 Sezioni della Dashboard e Algoritmi di Raccomandazione

I seguenti esempi mostrano il funzionamento delle sezioni della piattaforma, dettagliando l'uso di filtri, la corrispondenza degli ingredienti, i vincoli nutrizionali ed il mood.

---

### 1. Pagina Popularity

![Popularity](assets/Schermata%20del%202026-09-04%2015-55-05.png)

* **Filtro per tag:** `60-minutes-or-less`, `dinner-party`, `european`, `summer`
* **Risultato:** **Summer Memories Jumbleberry Crumble With Shortbread Topping** (50 min, 357.8 kcal)
* **Metriche:** Rating medio `5.0` | Score bayesiano `4.7871` (+0.27 sopra la media)
* **Badge:** `"fiducia bassa"` (solo 13 voti)
* **Note:** Utile per mostrare il compromesso della Bayesian Average nel bilanciare il rating con il numero di voti.

---

### 2. Pagina Svuota-frigo 
![Svuota-frigo](assets/Schermata%20del%202026-09-04%2015-56-21.png)

* **Ingredienti inseriti:** `chicken breasts`, `fresh mushrooms`
* **Tolleranza:** Massimo 4 ingredienti extra
* **Risultato:** **Poached Chicken Breast** (33 min, 124.7 kcal)
* **Metriche:** Corrispondenza ingredienti `100%` | Similarità coseno `0.7687`
* **Badge:** `"pronta subito"`

---

### 3. Pagina Salutistico

![Salutistico](assets/Schermata%20del%202026-09-04%2015-56-55.png)

* **Vincoli e filtri:** Max `900 kcal` | Proteine minime `50% DV` | Tag `"gluten-free"` | Obiettivo `bilanciato`
* **Risultato top:** **Maple Mustard Glazed Salmon 3 Ingredients** (15 min, 416.9 kcal)
* **Metriche:** `130% DV` proteine | `21% DV` grassi | Compatibilità con l'obiettivo `100%`

---

### 4. Pagina Mood 

![Pagina Mood](assets/Schermata%20del%202026-09-04%2015-57-36.png)

* **Slider impostati:** `body: -3.0` | `time: +3.0` | `taste: 0.0` | `price: -2.0` | `mental: 0.0` | `modification: +3.5`
* **Risultato migliore:** **Armenian Nutmeg Cake** (75 min, 335 kcal)
* **Metriche:** Affinità col mood dell'utente `86%`

---

### 5. Radar Mood — Dettaglio 

![Radar Mood Dettaglio](assets/Schermata%20del%202026-09-04%2015-57-46.png)

* **Grafico isolato:** Confronto tra il vettore mood dell'utente (verde) e quello della ricetta consigliata (rosso).
* **Dimensioni analizzate:** `body`, `time`, `taste`, `price`, `mental`, `modification`
* **Note:** Le due forme sono quasi sovrapposte, a conferma della buona corrispondenza trovata dal modello.
