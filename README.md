# CÀNONE Template Community

Template pronti per [CÀNONE Studio](https://github.com/marcozeus/canone) — il visual builder desktop per siti statici professionali.

Ogni template è un file `.canone` che si apre direttamente nell'app: zero setup, zero dipendenze, zero abbonamenti.

---

## Template disponibili

| Template | Categoria | Pagine |
|----------|-----------|--------|
| **Business Starter** | business | Home, Contatti |
| **Portfolio Creativo** | portfolio | Home, Lavori, Contatti |
| **Landing Conversion** | landing | Pagina singola |
| **Ristorante & Locale** | business | Home (menù, prenotazioni, storia) |
| **Blog Minimal** | blog | Home, Chi Sono |

Scaricabili direttamente dalla HomeScreen di CÀNONE → pulsante **TEMPLATE COMMUNITY**.

---

## Struttura del repository

```
index.json                          ← indice letto dall'app ogni 24h (cache localStorage)
templates/
  <slug-template>/
    progetto.canone                 ← file progetto (JSON, rinominabile)
    preview.jpg                     ← anteprima 1200×800px (obbligatoria per PR esterne)
```

---

## Contribuire un template

Hai creato un template con CÀNONE e vuoi condividerlo con la community? Benvenuto.

### 1. Crea il tuo template in CÀNONE Studio

Costruisci il tuo sito come sempre nell'editor. Usa blocchi della libreria, immagini da Unsplash o placeholder, testi credibili (non solo "Lorem ipsum"). Quando sei soddisfatto, salva il file `.canone`.

### 2. Prepara i file

```
templates/
  nome-del-tuo-template/
    progetto.canone     ← il file salvato da CÀNONE Studio
    preview.jpg         ← screenshot 1200×800px (usa il tuo browser, strumento Stampa → Salva PDF → converti)
```

### 3. Aggiorna index.json

Aggiungi la tua voce all'array `templates`:

```json
{
  "id": "nome-del-tuo-template",
  "nome": "Nome Leggibile",
  "descrizione": "Una frase che descrive cosa fa il template (max 120 caratteri).",
  "categoria": "business",
  "autore": "Il Tuo Nome",
  "badge": null,
  "preview": "https://raw.githubusercontent.com/marcozeus/canone-templates/main/templates/nome-del-tuo-template/preview.jpg",
  "rawUrl": "https://raw.githubusercontent.com/marcozeus/canone-templates/main/templates/nome-del-tuo-template/progetto.canone"
}
```

### 4. Apri una Pull Request

Titolo: `Template: Nome Leggibile [categoria]`

Descrizione: breve spiegazione del template, per chi è pensato, cosa contiene.

---

## Regole di accettazione

**Contenuto**
- Il template deve aprirsi correttamente in CÀNONE Studio 3.0+
- Testi placeholder credibili (non solo "Lorem ipsum ovunque")
- Immagini solo da CDN approvati: Unsplash (`images.unsplash.com`), placeholder SVG inline
- Categoria obbligatoria tra: `business` `portfolio` `landing` `blog` `ecommerce` `evento`

**Codice e dipendenze**
- CDN esterni solo se già nel whitelist CÀNONE: GSAP, Google Fonts, Tailwind CDN
- Form solo verso: Web3Forms, Mailchimp, Brevo — nessun backend proprietario
- Nessuna chiamata a API esterne che richiedano autenticazione
- File `.canone` < 5MB, immagini base64 < 2MB totali

**Preview**
- JPG o PNG, 1200×800px minimo
- Deve mostrare la Home del template (non una pagina interna)
- Nessun watermark, nessun logo personale in evidenza nell'immagine

**Licenza**
- Contribuendo accetti che il tuo template sia distribuito sotto licenza MIT
- Il tuo nome rimane nell'array `autore` a tempo indeterminato

---

## Schema completo index.json

```json
{
  "versione": "1",
  "aggiornato": "YYYY-MM-DD",
  "templates": [
    {
      "id": "slug-kebab-case",
      "nome": "Nome Leggibile",
      "descrizione": "Descrizione breve (max 120 caratteri).",
      "categoria": "business | portfolio | landing | blog | ecommerce | evento",
      "autore": "Nome Autore o Team",
      "badge": "nuovo | popolare | premium | null",
      "preview": "https://raw.githubusercontent.com/marcozeus/canone-templates/main/templates/<slug>/preview.jpg",
      "rawUrl": "https://raw.githubusercontent.com/marcozeus/canone-templates/main/templates/<slug>/progetto.canone"
    }
  ]
}
```

Il campo `badge` è assegnato dal maintainer — non includerlo nelle PR esterne o mettilo a `null`.

---

## Domande frequenti

**Posso usare immagini reali dei miei clienti?**
No. Usa immagini da Unsplash (licenza libera) o placeholder grafici. Le immagini dei clienti non devono finire in un repo pubblico.

**Il template può avere più lingue?**
Sì, CÀNONE supporta multi-lingua. Includi tutte le varianti che vuoi.

**Posso fare un template "premium" che vendo altrove?**
I template in questo repo sono liberi per tutti. Se vuoi vendere template premium, aspetta la release di CÀNONE Pro (in arrivo) dove ci sarà un canale dedicato.

**Il badge "premium" o "popolare" lo posso mettere io?**
No, li assegna il maintainer in base ai download e alla qualità.

---

*Creato e mantenuto dal CÀNONE Team. Issues e suggerimenti benvenuti.*
