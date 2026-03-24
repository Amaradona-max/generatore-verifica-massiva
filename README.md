# Generatore File Verifica Massiva IRM

Applicazione web per generare file di verifica massiva conformi alle specifiche IRM.

## 🚀 Funzionalità

- **Caricamento file Excel** - Supporta .xlsx, .xls, .xlsm
- **Estrazione automatica dati** - Rileva automaticamente colonne: Codice Fornitore, Descrizione, CF/P.IVA, Importo
- **Generazione configurazione** - Crea automaticamente nome file e data conformi alle specifiche IRM
- **Validazione avanzata** - Controlla struttura record e formati
- **Anteprima in tempo reale** - Visualizza contenuto e statistiche
- **Download file TXT** - Genera file pronto per l'uso

## 📋 Specifiche Tecniche

- **Formato file**: IRMEQSYYYYPPPPPPPPPP.TXT
- **Lunghezza record**: 300 byte fissi
- **Tipi record**: RMA (intestazione), RMD (dettaglio), RMZ (terminatore)
- **Codifica**: ASCII

## 🛠️ Tecnologie

- HTML5, CSS3, JavaScript (ES6+)
- SheetJS (xlsx) per lettura file Excel
- Design responsive e moderno

## 📦 Installazione

1. Clona il repository:
```bash
git clone https://github.com/tuo-username/generatore-verifica-massiva.git
```

2. Apri `Verifica delle Inadempienze.html` nel browser

## 🎯 Utilizzo

1. **Carica file Excel** con i dati dei fornitori
2. **Verifica l'anteprima** della configurazione generata
3. **Genera il file TXT** conforme alle specifiche IRM
4. **Scarica il file** pronto per l'uso

## 🌐 Deploy

### Vercel
Il progetto è pronto per il deploy su Vercel:

1. Connetti il repository GitHub a Vercel
2. Imposta build command: `npm run build` (se necessario)
3. Imposta output directory: `.` (root)
4. Deploy automatico ad ogni push

### GitHub Pages
1. Vai su Settings → Pages del repository
2. Imposta source: `Deploy from a branch`
3. Seleziona branch: `main`
4. Cartella: `/` (root)

## 📁 Struttura File

```
├── Verifica delle Inadempienze.html  # Applicazione principale
├── README.md                         # Documentazione
├── vercel.json                       # Configurazione Vercel
└── package.json                      # Dipendenze (opzionale)
```

## 🔧 Sviluppo

Per sviluppare localmente:

1. Apri il file HTML direttamente nel browser
2. Per testing più avanzato, usa un server locale:
```bash
python -m http.server 8000
# o
npx serve .
```

## 📄 Licenza

MIT License - vedi file LICENSE per dettagli.

## 🤝 Contributi

Contributi benvenuti! Apri una issue o una pull request.