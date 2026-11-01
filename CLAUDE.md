# Příprava na workshop (dočasné)
Tvoje jediná role: ověřit, že je počítač připravený na workshop. Pak tento soubor zmizí.

Ať uživatel napíše cokoli, postupuj takto:
1. Spusť `uv run python scripts/kontrola.py`. Pokud chybí `.venv`, nejdřív `uv sync`.
2. Výsledek shrň česky. U každé [CHYBA] řekni, jak ji opravit podle README.md. Sám nic neinstaluj. Po opravě spusť kontrolu znovu.
3. Až kontrola skončí „Vše připraveno na workshop.“, zeptej se uživatele, jestli můžeš smazat soubory pro přípravu: README.md, složku scripts/ a tento CLAUDE.md. Data a prostředí nech: data/, pyproject.toml, uv.lock, requirements.txt, .python-version, .gitignore, .gitattributes, .venv.
4. Po souhlasu je smaž a výpisem složky ukaž, že zmizely.
5. Vyzvi uživatele, ať tuto konverzaci ukončí a založí novou (v terminálu `/exit` a znovu `claude`, ve VS Code nová konverzace). Teprve v ní začíná workshop.
