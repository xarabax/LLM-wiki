---
title: "Clean Code e Ottimizzazione Lighthouse"
type: topic
domain: research
tags: [clean-code, web-performance, lighthouse, core-web-vitals, optimization]
sources: 1
created: 2026-06-10
updated: 2026-06-10
---

## Sintesi

Scrivere codice pulito e ottimizzare le performance web sono requisiti fondamentali per offrire un'esperienza utente eccellente. **Google Lighthouse** è lo strumento di riferimento per analizzare la qualità delle pagine web su quattro pilastri: Performance, Accessibilità, Best Practices e SEO. 

Questa guida raccoglie le migliori pratiche moderne per mantenere pulito il codice frontend e ottimizzare l'architettura per ottenere punteggi eccellenti (100/100) e soddisfare i **Core Web Vitals** di Google: **LCP** (Largest Contentful Paint), **INP** (Interaction to Next Paint) e **CLS** (Cumulative Layout Shift).

---

## 1. Ottimizzazione del Critical Rendering Path (CRP)

Il Critical Rendering Path stabilisce la velocità con cui il browser converte HTML, CSS e JavaScript in pixel disegnati sullo schermo.

### Buone Pratiche (DOs)
- **Inline del CSS critico:** Estrai gli stili necessari per la visualizzazione immediata (above-the-fold) e inseriscili direttamente nel tag `<style>` dentro l'tag `<head>`. Carica il resto del foglio di stile in modo asincrono.
- **Script non bloccanti (`async`/`defer`):** Usa `defer` per gli script che dipendono dal DOM e `async` per script indipendenti (es. tracciamenti). I moderni moduli JavaScript (`type="module"`) sono differiti (`deferred`) per impostazione predefinita.
- **Suddividi il CSS per Media Query:** Utilizza l'attributo `media` sui tag `<link>` per fare in modo che il browser scarichi stili non critici (es. fogli di stile desktop su dispositivi mobile) a priorità inferiore senza bloccare il rendering.
- **Utilizza i Resource Hints:** Stabilisci connessioni anticipate verso domini di terze parti essenziali.

### Cose da Evitare (DON'Ts)
- **NON usare `@import` nel CSS:** Crea catene di richieste sequenziali che ritardano la costruzione del CSSOM (CSS Object Model).
- **NON inserire script JS pesanti non critici nel `<head>`:** Questo interrompe la costruzione del DOM finché lo script non viene scaricato, analizzato ed eseguito.

### Navigatore dei Resource Hints
- **Preconnect:** Risolve TLS/DNS per domini esterni noti (es. API, Google Fonts).
- **DNS-Prefetch:** Risolve il DNS per domini di terze parti non critici (es. fallback analitici).
- **Preload:** Forza lo scaricamento di risorse locali necessarie *ora* per il rendering (es. l'immagine LCP, font principali).
- **Prefetch:** Scarica risorse che saranno necessarie per la pagina *successiva* (es. bundle delle rotte adiacenti).

> **Regola a mente:** *"Preconnect per i domini, Preload per la viewport, Prefetch per il futuro."*

#### Esempio di Codice HTML
```html
<head>
  <!-- Inline css critico -->
  <style>
    body { margin: 0; font-family: system-ui, sans-serif; }
    .hero { min-height: 100vh; background: #0f172a; }
  </style>

  <!-- Preconnect a domini terzi per le API -->
  <link rel="preconnect" href="https://api.esempio.com">

  <!-- Caricamento asincrono del CSS non critico -->
  <link rel="preload" href="stile-completo.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
  <noscript><link rel="stylesheet" href="stile-completo.css"></noscript>

  <!-- Script differito -->
  <script defer src="app.js"></script>
</head>
```

---

## 2. Ottimizzazione del Largest Contentful Paint (LCP)

L'LCP misura il tempo necessario per visualizzare il blocco di testo o l'immagine più grande visibile all'interno della viewport iniziale.

### Buone Pratiche (DOs)
- **Usa `fetchpriority="high"` sull'elemento LCP:** Indica al browser di dare priorità assoluta all'immagine o risorsa LCP rispetto a script ed elementi non critici.
- **Dichiara l'immagine LCP in HTML standard:** Assicurati che l'elemento `<img>` sia presente nell'HTML grezzo restituito dal server. Evita di montare l'elemento LCP dinamicamente tramite JavaScript.
- **Usa `fetchpriority="low"` per elementi secondari above-the-fold:** Riduci la priorità per immagini secondarie o slider non visibili immediatamente.

### Cose da Evitare (DON'Ts)
- **NON usare il lazy-loading sull'immagine LCP:** Non inserire mai `loading="lazy"` sulle immagini above-the-fold. Ritarda inutilmente il rendering.
- **NON abusare di `fetchpriority="high"`:** La prioritizzazione è a somma zero; se tutto è prioritario, nulla lo è.

#### Esempio di Codice Immagine LCP
```html
<picture>
  <!-- Formati moderni (AVIF/WebP) responsive -->
  <source type="image/avif" srcset="hero-mobile.avif 600w, hero-desktop.avif 1200w" sizes="(max-width: 600px) 100vw, 50vw">
  <source type="image/webp" srcset="hero-mobile.webp 600w, hero-desktop.webp 1200w" sizes="(max-width: 600px) 100vw, 50vw">
  
  <img 
    src="hero-fallback.jpg" 
    alt="Descrizione dell'immagine" 
    width="1200" 
    height="600"
    fetchpriority="high"
    loading="eager"
    decoding="sync"
  >
</picture>
```

---

## 3. Interaction to Next Paint (INP) e Unblocking del Main Thread

L'INP misura la latenza di tutti gli eventi di interazione (click, tap, tastiera) durante il ciclo di vita della pagina. Un INP scarso è causato da script pesanti che bloccano il thread principale del browser.

### Buone Pratiche (DOs)
- **Scomponi i Long Tasks:** Qualsiasi esecuzione JavaScript superiore a 50ms dovrebbe essere frammentata per restituire il controllo al browser (yielding).
- **Usa `scheduler.yield()`:** Questa moderna API consente di mettere in pausa l'esecuzione corrente e riprenderla subito dopo che il browser ha gestito gli input dell'utente.
- **Batching delle letture e scritture del DOM:** Evita il *Layout Thrashing*. Non alternare letture del DOM (es. `offsetHeight`) e scritture (es. `style.height`) nello stesso ciclo di codice. Leggi tutto prima, scrivi tutto dopo.
- **Usa i Web Workers per il calcolo pesante:** Sposta elaborazioni di dati o logiche complesse (>250ms) fuori dal thread principale.

#### Esempio JS: scheduler.yield() con Fallback
```javascript
// Funzione helper per cedere il controllo al Main Thread
async function yieldToMain() {
  if ('scheduler' in window && 'yield' in scheduler) {
    return await scheduler.yield();
  }
  return new Promise(resolve => setTimeout(resolve, 0));
}

// Elaborazione di una lista pesante senza bloccare l'interfaccia
async function processaDati(items) {
  for (let i = 0; i < items.length; i++) {
    elaboraElemento(items[i]);
    
    // Cedi il controllo ogni 50 iterazioni
    if (i % 50 === 0) {
      await yieldToMain();
    }
  }
}
```

---

## 4. Stabilità del Layout (CLS)

Il CLS misura la stabilità visiva di una pagina, tracciando gli spostamenti improvvisi degli elementi durante il caricamento.

### Buone Pratiche (DOs)
- **Dimensioni esplicite per i media:** Specifica sempre gli attributi `width` e `height` su tag `<img>`, `<video>` e `<iframe>`. Questo consente al browser di calcolare l'aspect ratio istantaneamente e riservare lo spazio corretto nel layout.
- **Minimizza gli inserimenti dinamici di contenuto:** Evita di inserire banner, annunci o widget sopra contenuti esistenti senza aver precedentemente riservato spazio tramite scheletri (skeleton loaders) o min-height CSS.

---

## 5. CSS Rendering e Contenimento (Containment)

Su pagine complesse e ricche di elementi, i calcoli di stile e layout possono degradare le performance.

- **Usa `content-visibility: auto`:** Applica questa proprietà CSS alle sezioni below-the-fold. Il browser salterà i calcoli di layout e disegno per gli elementi fuori dallo schermo finché l'utente non vi si avvicina.
- **Accoppia `content-visibility` con `contain-intrinsic-size`:** Fornisci un'altezza segnaposto (es. `contain-intrinsic-size: auto 500px`) per evitare salti della barra di scorrimento laterale durante lo scrolling.
- **Containment isolato (`contain`):** Per componenti isolati o widget che cambiano frequentemente stile (es. modali, dashboard), usa `contain: layout style paint` per evitare che le modifiche causino reflow dell'intera pagina.

#### Esempio di CSS Performance
```css
/* Ottimizzazione di articoli lunghi sotto la fold */
.articolo-lista {
  content-visibility: auto;
  contain-intrinsic-size: auto 600px; /* Altezza stimata segnaposto */
}

/* Isolamento di un widget dinamico */
.widget-dashboard {
  contain: layout style paint;
}
```

---

## 6. Caching Strategico con Service Workers

Un Service Worker permette di aggirare la rete memorizzando in cache risorse statiche e API sul dispositivo dell'utente.

- **CacheFirst (Static Assets):** Per file immutabili dotati di hash nel nome (CSS, JS bundle, Font). Servili direttamente dalla cache per un caricamento istantaneo.
- **StaleWhileRevalidate (Dynamic Content):** Per API o dati dinamici non critici. Mostra subito i dati in cache e aggiornali silenziosamente in background effettuando una chiamata di rete.
- **NetworkFirst (HTML/Documenti):** Per la pagina HTML principale, per assicurarsi che l'utente riceva sempre l'ultima versione dell'app, usando la cache solo come fallback offline.

---

## Checklist Finale per il Punteggio 100/100 su Lighthouse

1. [ ] **HTML Pulito:** Tutte le immagini below-the-fold hanno `loading="lazy"`. LCP ha `fetchpriority="high"` e `loading="eager"`.
2. [ ] **Media Dimensionati:** Tutti gli elementi `<img>`, `<video>` e `<iframe>` definiscono `width` e `height` espliciti.
3. [ ] **Font Ottimizzati:** I font principali sono precaricati (`preload`) usando l'attributo `crossorigin` e hanno `font-display: swap` definito nel CSS.
4. [ ] **Bundling & Code Splitting:** I fogli di stile e i file JavaScript sono minimizzati, compressi (Brotli/Gzip) e suddivisi per rotte tramite caricamenti dinamici (`import()`).
5. [ ] **Zero Layout Thrashing:** I listener di eventi scroll/resize sono ottimizzati (tramite debounce o throttle) e non alternano letture/scritture sincrone del DOM.
6. [ ] **Strategia di Caching:** Le risorse statiche sono servite con intestazioni `Cache-Control` a lungo termine o gestite da un Service Worker.

---

## Connections

- [[marco-cassani]] — Profilo del consulente/docente che applica queste pratiche nello sviluppo full-stack e nell'insegnamento.
- [[ai-automazione]] — L'integrazione di interfacce veloci e stabili è cruciale per massimizzare l'adozione e il ROI delle automazioni aziendali.

---

## Fonti

- [Modern Web Guidance: Performance Guide](file:///Users/xarabax/.gemini/antigravity-ide/brain/edd096f9-89e2-40ee-ac33-8dd067f23f43/scratch/performance.md) — Dati e specifiche estratti dal database di guida web.
