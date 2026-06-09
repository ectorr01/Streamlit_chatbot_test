# Chatbot WiData

Semplice chatbot RAG realizzato con Streamlit, Anthropic, ChromaDB e PDF upload.
L'app permette di caricare un PDF, indicizzarlo in chunk e fare domande usando il contenuto del documento come contesto.[1][2]

## Avvio locale in VS Code

1. Apri il progetto in VS Code.
2. Crea l'ambiente virtuale e installa le dipendenze del progetto.
3. Crea la cartella `.streamlit` nella root del progetto, cioè nella stessa cartella da cui esegui `streamlit run app.py`.[1][2]
4. Crea il file `.streamlit/secrets.toml` e inserisci la chiave:

```toml
ANTHROPIC_API_KEY = "la_tua_key"
```

5. Avvia l'app con:

```bash
streamlit run app.py
```

Streamlit legge i secret dal file `.streamlit/secrets.toml` nella working directory; se esiste anche un file globale, quello del progetto ha precedenza.[1]

## Secret su Streamlit Community Cloud

Quando pubblichi l'app su Streamlit Community Cloud, non devi caricare `secrets.toml` nel repository GitHub. I secret vanno inseriti nel pannello **Secrets** dell'app nelle impostazioni di deploy.[3][4]

Nel pannello Secrets inserisci ad esempio:

```toml
ANTHROPIC_API_KEY = "la_tua_key"
```

In questo modo la chiave resta fuori dal codice e l'app può leggerla con `st.secrets` durante il runtime.[5][3]

## Sicurezza

Aggiungi questo file al `.gitignore` per evitare di pubblicare accidentalmente la chiave:

```gitignore
.streamlit/secrets.toml
```

Se il file è già stato tracciato da Git, va rimosso dall'indice con `git rm --cached .streamlit/secrets.toml` prima del push.[5]
