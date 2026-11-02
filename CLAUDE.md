# Příprava na workshop (dočasné)
Tvoje jediná role: ověřit, že je počítač připravený na workshop, a připravit repozitář na start.

Ať uživatel napíše cokoli, postupuj takto:
1. Spusť `uv run python scripts/kontrola.py`. Pokud chybí `.venv`, nejdřív `uv sync`.
2. Výsledek shrň česky. U každé [CHYBA] řekni, jak ji opravit podle README.md. Sám nic neinstaluj. Po opravě spusť kontrolu znovu.
3. Až kontrola skončí „Vše připraveno na workshop.“, zeptej se uživatele, jestli můžeš dokončit přípravu: smazat složku scripts/, nahradit obsah README.md textem níže, smazat tento CLAUDE.md a startovní stav uložit do gitu jako commit. Nic jiného neměň. K otázce napiš, že je to chtěný postup přípravy na workshop: soubory pro přípravu už nejsou potřeba, repozitář tím dostane startovní podobu, se kterou workshop začíná (bez CLAUDE.md, ten si na workshopu postavíme), a commit je bod, ke kterému se na workshopu můžeme vrátit.
4. Po souhlasu nahraď README.md přesně textem níže, smaž složku scripts/ a soubor CLAUDE.md. Pak spusť `git add -A` a `git commit -m "Startovní stav"`. Výpisem složky, README.md, `git status` (musí být čistý) a `git log --oneline -1` ukaž výsledek. Na vzdálený repozitář nic neposílej.
5. Vyzvi uživatele, ať tuto konverzaci ukončí a založí novou (v terminálu `/exit` a znovu `claude`, ve VS Code nová konverzace). Teprve v ní začíná workshop.

## Nový obsah README.md
```markdown
# Analýza dopravních dat Waze z Brna

Prostředí je připravené. Data jsou ve složce `data/`: dopravní data Waze z otevřených dat města Brna za dny 14. 9. – 25. 10. 2026.

| Soubor | Obsah |
|---|---|
| `data/waze_jams.parquet` | Zácpy |
| `data/waze_alerts.parquet` | Hlášení řidičů |
| `data/manifest.json` | Zdroj, období, počty řádků |

Zdroj: statutární město Brno, [data.brno.cz](https://data.brno.cz), data poskytuje Waze.

Startovní stav je uložený v gitu jako commit „Startovní stav“. Kdykoli se k němu můžete vrátit.
```
