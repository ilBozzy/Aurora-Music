# Aurora-Music
Music Audio Tagger

# 🌅 Aurora
**Audio Metadata Analyzer & Tagger**  
_by Bozzy_

---

## 🎯 Obiettivo
**Aurora** è un software in Python che analizza le tracce audio per recuperare e aggiornare automaticamente i **metadata musicali e tecnici**.  
È pensato per DJ, produttori e appassionati che vogliono avere una libreria musicale pulita, precisa e completa, **senza dover editare i tag a mano**.

---

## ⚙️ Come funziona
Quando avvii Aurora:
1. Ti chiede di **trascinare una cartella o un file audio** nel terminale;  
2. Ti fa scegliere il **tipo di analisi** da eseguire:  

| Modalità | Descrizione | Metadata aggiornati |
|-----------|--------------|--------------------|
| **BASIC** | Recupera solo informazioni ufficiali (senza analisi audio). | Titolo, Artista, Album, Anno, Artwork |
| **ADVANCED** | Analizza i parametri tecnici del suono. | BPM, Tonalità, Decibel (RMS) |
| **FULL** | Combina i due livelli: lookup + analisi audio. | Tutto |
| **AUTO (in sviluppo)** | Inserisce solo i tag mancanti, senza sovrascrivere quelli già presenti. | Dinamico |

---

## 🔍 Analisi e lookup
Aurora combina due approcci:

### 🧠 1. Lookup online (BASIC / FULL)
Se disponi di una **chiave API AcoustID**, Aurora:
- genera un’impronta digitale della traccia;  
- la confronta con il database **MusicBrainz / AcoustID**;  
- recupera i **metadata ufficiali** dell’artista, dell’album e dell’anno;  
- scarica anche la **copertina** dell’album, se disponibile.  

Aurora ignora versioni non ufficiali (es. “Lyric Video”, “Live”, “Remix” non dichiarati).

### 🎧 2. Analisi audio locale (ADVANCED / FULL)
Quando serve estrarre dati tecnici, Aurora usa **librosa** e **soundfile** per:
- Calcolare il **BPM** (velocità del brano);  
- Stimare la **tonalità musicale** (chiave armonica);  
- Misurare il livello medio in **decibel RMS** (volume percepito).  

---

## 💾 Output
- I **metadata vengono scritti direttamente nei file audio** (`.mp3`, `.flac`, `.wav`, `.ogg`, `.m4a`, ecc.);  
- Viene creato anche un file di report `tagger_report.json`, con tutti i risultati dell’analisi.  

---

## 🧰 Stack Tecnico
- **Python 3.11+**
- Librerie principali:
  - `mutagen` → lettura/scrittura metadata  
  - `librosa`, `soundfile`, `numpy` → analisi audio  
  - `requests` → accesso ai database online  
  - `tqdm` → barra di progresso  
  - *(in futuro: `sqlite3` per database locale e `rich` per interfaccia CLI)*

---

## 🚀 Roadmap
- [x] Modalità BASIC / ADVANCED / FULL  
- [x] Scrittura diretta nei tag audio  
- [x] Pulizia percorso Windows (drag & drop)  
- [ ] Modalità **AUTO** (aggiornamento parziale)  
- [ ] Cache locale per risultati ripetuti  
- [ ] Interfaccia CLI colorata  
- [ ] Integrazione con **Traktor / Rekordbox / Spotify API**  

---

## 🌿 Filosofia
Aurora nasce dalla filosofia del **chilling**:  
niente fretta, niente presura — solo un flusso naturale dove musica e tecnologia si incontrano.  

È uno strumento tecnico, ma con l’anima calma e lucida di chi vive la musica **con consapevolezza e precisione**.  
Aurora non tagga solo file: **riordina il tuo suono**.

---

## 💡 Esecuzione
```bash
python aurora.py
