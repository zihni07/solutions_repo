# Repozytorium Dokumentacji MkDocs

To repozytorium zawiera konfigurację do automatycznego budowania i publikowania dokumentacji za pomocą MkDocs i GitHub Pages.

## Struktura Repozytorium

- `.github/workflows/deploy.yml` – Konfiguracja GitHub Actions do automatycznego wdrażania.
- `docs/` – Katalog zawierający pliki dokumentacji w formacie Markdown.
- `mkdocs.yml` – Plik konfiguracyjny MkDocs.
- `README.md` – Ten plik z instrukcją obsługi.

## Jak Używać

1. **Dodawanie lub Edycja Dokumentacji:**
   - Edytuj istniejące pliki Markdown w katalogu `docs/` lub dodaj nowe.

2. **Publikacja Zmian:**
   - Po dokonaniu zmian, wykonaj następujące polecenia:
     ```bash
     git add .
     git commit -m "Aktualizacja dokumentacji"
     git push origin main
     ```
   - GitHub Actions automatycznie zbuduje i opublikuje zaktualizowaną dokumentację na GitHub Pages.

## Konfiguracja GitHub Pages

1. Przejdź do ustawień repozytorium na GitHub.
2. W sekcji "Pages" ustaw źródło na gałąź `gh-pages`.
3. Po skonfigurowaniu, dokumentacja będzie dostępna pod adresem:
