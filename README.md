# VivaVoce Releases & Delta Distribution

Repository di distribuzione per **VivaVoce — World of Warcraft: Forever (1.12.1)**.

Questo repository ospita:
- `manifest.json`: Il catalogo ufficiale dei pacchetti completi e delle patch incrementali delta.
- [GitHub Releases](https://github.com/Master-Antonio/Vivavoce-Releases/releases): Tutti gli archivi di gioco compressi ad altissima densità con **Zstandard** (`.tar.zst`).

## ⚡ Come Funzionano gli Aggiornamenti Delta
- **Nuove installazioni**: Il launcher scarica i pacchetti base (`VivaVoce_Core`, `VivaVoce_Sounds_part1/2/3`).
- **Aggiornamenti (Updates)**: Il launcher non riscarica mai l'intero archivio audio di 3–4 GB. Scarica esclusivamente la patch delta (`patch-vX.X.X.tar.zst`) contenente solo le battute vocali nuove o ri-sintetizzate e gli script modificati (solitamente tra 2 MB e 10 MB).
- **Verifica Integrità**: Ogni singolo file è indicizzato con il proprio checksum crittografico verificato dal launcher prima e dopo ogni installazione.

## 🛠️ Gestione Release (Per gli Sviluppatori)
Tutte le operazioni sono completamente automatizzate tramite lo script `tools/release_manager.py`:

```bash
# 1. Costruzione release base (v1.0.0)
python tools/release_manager.py build-base --version 1.0.0

# 2. Creazione patch incrementale (confronta i file modificati rispetto a v1.0.0)
python tools/release_manager.py build-patch --version 1.0.1

# 3. Pubblicazione su GitHub Releases e sincronizzazione del manifest.json
python tools/release_manager.py publish --version 1.0.1
```
