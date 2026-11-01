# Příprava na workshop (dočasné)
Tvoje jediná role: ověřit, že je počítač připravený na workshop, a připravit repozitář na start.

Ať uživatel napíše cokoli, postupuj takto:
1. Spusť `uv run python scripts/kontrola.py`. Pokud chybí `.venv`, nejdřív `uv sync`.
2. Výsledek shrň česky. U každé [CHYBA] řekni, jak ji opravit podle README.md. Sám nic neinstaluj. Po opravě spusť kontrolu znovu.
3. Až kontrola skončí „Vše připraveno na workshop.“, zeptej se uživatele, jestli můžeš dokončit přípravu: smazat složku scripts/, nahradit obsah README.md a nahradit obsah tohoto CLAUDE.md texty níže. Nic jiného neměň. K otázce napiš, že je to chtěný postup přípravy na workshop: soubory pro přípravu už nejsou potřeba a repozitář tím dostane startovní podobu, se kterou workshop začíná.
4. Po souhlasu to udělej přesně podle textů níže a výpisem složky a obou souborů ukaž výsledek.
5. Vyzvi uživatele, ať tuto konverzaci ukončí a založí novou (v terminálu `/exit` a znovu `claude`, ve VS Code nová konverzace). Teprve v ní začíná workshop.

## Nový obsah README.md
```markdown
# MAIDAY 2026: analýza dat s Claude Code

Prostředí je připravené. Workshop začínáme s našimi daty ve složce `data/`: dopravní data Waze z otevřených dat města Brna za dny 14. 9. – 25. 10. 2026.

| Soubor | Obsah |
|---|---|
| `data/waze_jams.parquet` | Zácpy |
| `data/waze_alerts.parquet` | Hlášení řidičů |
| `data/manifest.json` | Zdroj, období, počty řádků |

Zdroj: statutární město Brno, [data.brno.cz](https://data.brno.cz), data poskytuje Waze.
```

## Nový obsah CLAUDE.md
```markdown
Pracujeme přes virtuální prostředí projektu (`.venv`): Python spouštěj přes `uv run python`.
```
