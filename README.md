# MappaItalia – Visualizzatore Interattivo delle Regioni Italiane

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Leaflet](https://img.shields.io/badge/Leaflet-199900?style=flat&logo=leaflet&logoColor=white)
![GeoJSON](https://img.shields.io/badge/GeoJSON-4CAF50?style=flat&logo=geojson&logoColor=white)

Mappa web interattiva dell'Italia per visualizzare **tassi ipotetici** per Regione. L'applicazione è basata su **HTML, CSS e JavaScript**, utilizza **Leaflet** come libreria di mappe e carica dati geospaziali in formato **GeoJSON** (`Italia.geojson`). La classificazione dei valori avviene tramite **metodi statistici** (Jenks, intervalli uguali, quartili), modificabili dinamicamente dalla barra laterale.

---

## 📋 Indice

- [Descrizione](#-descrizione)
- [Funzionalità](#-funzionalità)
- [Demo](#-demo)
- [Tecnologie](#-tecnologie)
- [Struttura del progetto](#-struttura-del-progetto)
- [Installazione e utilizzo](#-installazione-e-utilizzo)
- [Uso dell'interfaccia](#-uso-dellinterfaccia)
- [Classificazione statistica](#-classificazione-statistica)
- [Palette di colori](#-palette-di-colori)
- [Formato GeoJSON](#-formato-geojson)
- [Personalizzazione](#-personalizzazione)
- [Roadmap](#-roadmap)
- [Licenza](#-licenza)
- [Autore](#-autore)

---

## 📖 Descrizione

**MappaItalia** è un visualizzatore di mappe interattivo delle **20 Regioni italiane** (15 a statuto ordinario e 5 a statuto speciale: Valle d'Aosta, Trentino-Alto Adige, Friuli-Venezia Giulia, Sicilia e Sardegna). La mappa viene renderizzata con **Leaflet** e popolata tramite il file `Italia.geojson` contenente i confini regionali. Ogni Regione viene colorata in base a un **tasso ipotetico** (`Tax_rate`). La classificazione dei valori in classi di colore avviene tramite **metodi statistici** selezionabili, così gli stessi dati possono essere mostrati in modo diverso a seconda della procedura scelta.

L'applicazione serve come materiale didattico per la **classificazione dei dati**, le **mappe coropletiche** e la **visualizzazione geospaziale**.

---

## ✨ Funzionalità

- 🗺️ Mappa interattiva dell'Italia con **Leaflet**.
- 🎨 Tre **metodi di classificazione statistica**: Jenks, intervalli uguali, quartili.
- 🌈 Quattro **schemi di colore**: scale di blu, rosso, lilla e verde.
- 🛰️ Tre **mappe di base**: Satellite (Esri), OpenStreetMap, CartoCDN Dark.
- 📥 **Importazione del livello** tramite pulsante (`IMPORTA LIVELLO`) – ricarica il file `Italia.geojson`.
- 🔍 **Selezione della Regione** tramite menu a tendina.
- 📊 **Riquadro informativo** con l'unità amministrativa e il valore corrente.
- 🖱️ **Tooltip al passaggio del mouse** su ogni Regione.
- 📱 Design responsive con barra laterale e immagini laterali.

---

## 🖥️ Demo

L'applicazione richiede un server locale, poiché il file GeoJSON viene caricato tramite `fetch()`.

```bash
# Opzione 1: Python
python -m http.server 8000

# Opzione 2: Node.js
npx serve .
```

---

## 🛠️ Tecnologie

| Tecnologia | Versione | Uso |
|------------|----------|-----|
| HTML5 | — | Struttura dell'interfaccia |
| CSS3 | — | Stili e design responsive |
| JavaScript (ES6+) | — | Logica dell'applicazione |
| [Leaflet](https://leafletjs.com/) | 1.9.x | Libreria di mappe interattive |
| GeoJSON | — | Formato di dati geospaziali |
| [simple-statistics](https://simple-statistics.github.io/) | 7.x | Calcolo di Jenks e quantili |

---

## 📁 Struttura del progetto

```
mappaitalia/
│
├── index.html              # Pagina principale
├── css/
│   └── styles.css          # Stili dell'applicazione
├── js/
│   ├── app.js              # Logica principale (mappa, livelli, eventi)
│   ├── classification.js   # Metodi di classificazione statistica
│   └── palettes.js         # Palette di colori
├── data/
│   └── Italia.geojson      # Confini delle Regioni italiane
├── img/
│   └── (immagini laterali)
└── README.md
```

---

## ⚙️ Installazione e utilizzo

1. **Clona il repository:**

   ```bash
   git clone https://github.com/italgiro-blip/mappaitalia.git
   cd mappaitalia
   ```

2. **Avvia un server locale** (necessario per `fetch()`):

   ```bash
   # Opzione 1: Python
   python -m http.server 8000

   # Opzione 2: Node.js
   npx serve .
   ```

3. **Apri il browser** su `http://localhost:8000`.

---

## 🖱️ Uso dell'interfaccia

| Elemento | Azione |
|----------|--------|
| **Menu a tendina** | Seleziona una Regione e centra la mappa su di essa |
| **Metodo di classificazione** | Cambia tra Jenks, intervalli uguali e quartili |
| **Palette di colori** | Cambia lo schema di colore (blu, rosso, lilla, verde) |
| **Mappa di base** | Cambia tra satellite, OpenStreetMap e CartoCDN Dark |
| **Pulsante `IMPORTA LIVELLO`** | Ricarica il file `Italia.geojson` |
| **Hover sulla mappa** | Mostra un tooltip con il nome e il valore |
| **Riquadro informativo** | Mostra l'unità amministrativa e il valore corrente |

---

## 📊 Classificazione statistica

L'applicazione permette di classificare i valori di `Tax_rate` tramite tre metodi:

### 1. Jenks (Natural Breaks)
Minimizza la varianza all'interno di ogni classe e massimizza la varianza tra le classi. Ideale per dati con distribuzioni irregolari.

### 2. Intervalli uguali
Divide l'intervallo dei valori in classi di uguale ampiezza. Semplice, ma sensibile ai valori anomali.

### 3. Quartili
Divide i dati in quattro gruppi con lo stesso numero di osservazioni. Utile per confrontare posizioni relative.

---

## 🎨 Palette di colori

| Palette | Colori |
|---------|--------|
| **Blu** | `#f7fbff` → `#08306b` |
| **Rosso** | `#fff5f0` → `#67000d` |
| **Lilla** | `#fcfbfd` → `#3f007d` |
| **Verde** | `#f7fcf5` → `#00441b` |

Ogni palette contiene **5 classi** di colore, assegnate automaticamente in base al metodo di classificazione scelto.

---

## 🗺️ Formato GeoJSON

Il file `data/Italia.geojson` deve contenere una `FeatureCollection` con una `Feature` per ogni Regione. Esempio minimo:

```json
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "properties": {
        "name": "Lombardia",
        "Tax_rate": 23.4
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [[[...]]]
      }
    }
  ]
}
```

**Proprietà richieste:**

| Proprietà | Tipo | Descrizione |
|-----------|------|-------------|
| `name` | string | Nome della Regione |
| `Tax_rate` | number | Valore numerico da visualizzare |

> Se il tuo GeoJSON utilizza altri nomi di campo (ad esempio `NOME_REG`, `reg_name`, `DEN_REG`), modifica il riferimento in `js/app.js`.

---

## 🔧 Personalizzazione

### Modificare i valori
Modifica la proprietà `Tax_rate` in `data/Italia.geojson`.

### Aggiungere nuove palette
Modifica `js/palettes.js` e aggiungi un nuovo array di colori:

```javascript
export const palettes = {
  blu: ['#f7fbff', '#c6dbef', '#6baed6', '#2171b5', '#08306b'],
  // nuova palette:
  arancione: ['#fff5eb', '#fdd0a2', '#fd8d3c', '#d94801', '#7f2704']
};
```

### Cambiare le mappe di base
Modifica l'oggetto dei livelli in `js/app.js` e aggiungi nuovi URL di tile (TileLayer).

---

## 🗺️ Roadmap

- [x] Mappa interattiva con Leaflet
- [x] Classificazione statistica (Jenks, intervalli uguali, quartili)
- [x] Palette di colori intercambiabili
- [x] Mappe di base (satellite, OSM, dark)
- [x] Tooltip e riquadro informativo
- [ ] Esportazione della mappa in PNG
- [ ] Filtro per intervallo di valori
- [ ] Grafico a barre con i valori per Regione
- [ ] Supporto per province e comuni
- [ ] Modalità scura

---

## 📄 Licenza

Questo progetto è distribuito sotto licenza **MIT**. Consulta il file `LICENSE` per maggiori informazioni.


## Crediti ed Esclusione di Responsabilità (Disclaimer)

Questo progetto è un visualizzatore GIS indipendente realizzato esclusivamente a scopo informativo, didattico o dimostrativo. Non è in alcun modo affiliato, associato, autorizzato o approvato dal Governo della Repubblica Italiana o da altri enti istituzionali.

Gli elementi grafici utilizzati per rappresentare il territorio italiano (inclusa la rielaborazione illustrativa dell'emblema) hanno unicamente funzione descrittiva e geografica all'interno dell'interfaccia. Il codice sorgente del progetto è distribuito secondo i termini della licenza indicata nel repository.

---

## 👤 Autore
- GitHub: https://github.com/italgiro-blip/
- Email: italgiro@gmail.com
