# Modellbildung

Kleines Python-Projekt mit Formatierungs- und Linting-Anweisungen.

## Voraussetzungen

- Python installiert (empfohlen: virtuelles Umfeld/venv)
- Die Entwicklungswerkzeuge sind in `requirements.txt` gelistet (z. B. `isort`, `black`, `ruff`).

Installiere Abhängigkeiten (in einem virtuellen Umfeld):

```bash
python -m pip install -r requirements.txt
```

## Formatierung und Linting

Hier sind die empfohlenen Befehle, um Importe zu sortieren, Code zu formatieren und Linting-Probleme zu prüfen und (so weit möglich) zu beheben.

Hinweis: Die Beispiele sind für macOS / zsh ausgelegt, funktionieren aber auf den meisten UNIX-ähnlichen Systemen.

- isort: Sortiert und organisiert Importe

```bash
# Für das gesamte Projekt
python -m isort .

# Für eine einzelne Datei
python -m isort path/to/file.py
```

- black: Formatiert Code nach Black-Style

```bash
# Für das gesamte Projekt
python -m black .

# Für eine einzelne Datei
python -m black path/to/file.py
```

- ruff: Schnell-Linter; prüft und kann viele Probleme automatisch beheben

```bash
# Nur prüfen
python -m ruff check .

# Prüfen und versuchen, Probleme zu beheben
python -m ruff check --fix .

# Alternativ, wenn Ihre ruff-Version 'format' unterstützt:
python -m ruff format .
```

## Empfohlene Reihenfolge (einfacher Einzeiler)

Eine sichere Reihenfolge ist: isort -> black -> ruff (fix). Dadurch werden Importe zuerst geordnet, dann der Code formatiert und anschließend Lint-Fixes angewendet.

```bash
python -m isort . && python -m black . && python -m ruff check --fix .
```

Für eine rein prüfende Pipeline (ohne automatische Fixes):

```bash
python -m isort --check-only . || true
python -m black --check . || true
python -m ruff check . || true
```

Die `--check` / `--check-only` Flags sind nützlich in CI, weil sie mit einem Fehlercode abbrechen, wenn Änderungen nötig sind.

## Hinweise

- Wenn du ein anderes Tooling (z. B. poetry, pipx, pre-commit) verwendest, kannst du die Befehle entsprechend anpassen.
- Falls du die Tools global installiert hast, kannst du `python -m` weglassen und direkt `isort .`, `black .`, `ruff check .` verwenden.

Viel Erfolg!
