# MAIDAY 2026: analýza dat s Claude Code

Repozitář k workshopu. Obsahuje data a připravené prostředí pro Python.

**Připravte si ho prosím předem, doma.** Zabere to asi 15–20 minut. Na workshopu na instalaci nebude čas.

Návod projděte krok za krokem. Všechny příkazy se píšou do **terminálu**: na Windows je to PowerShell (Start → napište „PowerShell“), na Macu aplikace Terminál. Příkaz zkopírujte, vložte a potvrďte Enterem.

## Krok 1: Co potřebujete mít
- **Účet Claude Pro** (nebo vyšší). S free účtem Claude Code nefunguje.
- Notebook s Windows 10/11 nebo macOS 13+.
- Právo instalovat programy. Na firemním notebooku si to ověřte včas.

## Krok 2: Nainstalujte nástroje
Budete potřebovat sedm programů a jedno rozšíření:

| Program | K čemu |
|---|---|
| Python (3.12 nebo novější) | jazyk, ve kterém analyzujeme data |
| Git | stažení repozitáře |
| uv | Python a knihovny |
| Node.js (verze 22.20 nebo novější) | pomocné nástroje |
| DuckDB CLI | práce s daty |
| Claude Code | AI asistent |
| VS Code | editor, ve kterém budeme pracovat |
| Rozšíření Claude Code do VS Code | Claude přímo v editoru |

### Windows
V PowerShellu spusťte jeden řádek po druhém a vždy počkejte, až doběhne:
```powershell
winget install Python.Python.3.13
winget install Git.Git
winget install astral-sh.uv
winget install OpenJS.NodeJS.LTS
winget install DuckDB.cli --version 1.5.6
irm https://claude.ai/install.ps1 | iex
winget install Microsoft.VisualStudioCode
```
Pokud se `winget` zeptá na souhlas s podmínkami, odpovězte `Y`.

### macOS (postup zatím neověřený)
Potřebujete [Homebrew](https://brew.sh). V Terminálu spusťte:
```bash
brew install python git uv node duckdb
brew install --cask visual-studio-code
curl -fsSL https://claude.ai/install.sh | bash
```

### Ověřte instalaci
**Zavřete terminál a otevřete nový** (pokud máte otevřený VS Code, zavřete i ten). Jinak nové programy nebudou vidět. Pak spusťte:
```
python --version
git --version
uv --version
node --version
duckdb --version
claude --version
code --version
```
Každý příkaz musí vypsat číslo verze. Na Macu místo `python` pište `python3`. U `node` musí být verze 22.20 nebo vyšší. Když některý příkaz napíše, že ho nezná, nainstalujte daný program znovu a otevřete nový terminál.

### Nainstalujte rozšíření Claude Code do VS Code
V novém terminálu spusťte:
```
code --install-extension anthropic.claude-code
```
Jde to i ručně: ve VS Code otevřete Rozšíření (Ctrl+Shift+X, na Macu Cmd+Shift+X), vyhledejte **Claude Code** od vydavatele **Anthropic** a klikněte na Install.

Ověření: `code --list-extensions` musí ve výpisu obsahovat `anthropic.claude-code`.

## Krok 3: Stáhněte repozitář
Vytvořte si třeba složku `projekty` a přejděte do ní:
```powershell
mkdir C:\projekty
cd C:\projekty
```
Na Macu: `mkdir ~/projekty` a `cd ~/projekty`. Pak stáhněte repozitář:
```bash
git clone https://github.com/honzapetr/MAIDAY-workshop-boilerplate.git maiday-analyza-dat
cd maiday-analyza-dat
```

## Krok 4: Připravte Python
Ve složce repozitáře spusťte:
```bash
uv sync
```
Tím se stáhne Python 3.13 a všechny knihovny ve správných verzích do složky `.venv`. Nic dalšího instalovat nemusíte.

## Krok 5: Přihlaste se do Claude Code
Ve složce repozitáře spusťte:
```bash
claude
```
1. Při prvním spuštění projdete několik úvodních obrazovek (vzhled, způsob přihlášení). Pohybujete se šipkami a Enterem. Jako přihlášení zvolte účet Claude s předplatným.
2. Otevře se prohlížeč. Přihlaste se svým účtem Claude Pro a vraťte se do terminálu.
3. Claude Code se zeptá, jestli této složce důvěřujete. Potvrďte.
4. Napište `/exit` a Claude Code zavřete.

Pak otevřete složku repozitáře ve VS Code:
```bash
code .
```
Otevřete panel Claude Code (ikona Claude v horní liště editoru nebo v postranním panelu). Pokud se zeptá na přihlášení, přihlaste se stejným účtem Claude Pro. Panel pak zavřete.

## Krok 6: Ověřte, že je vše připraveno
Ve složce repozitáře spusťte `claude` (nebo otevřete panel Claude Code ve VS Code) a napište:
```
Zkontroluj prostředí
```
Claude spustí kontrolu a pomůže vám opravit případné chyby. Když je vše v pořádku, zeptá se, jestli může dokončit přípravu (smaže kontrolní skript a tento návod nahradí krátkým popisem dat). Souhlaste. Pak vás vyzve, abyste konverzaci ukončili a začali novou. Tím je repozitář připravený na workshop.

Kontrolu jde spustit i ručně: `uv run python scripts/kontrola.py`. Na konci musí být **„Vše připraveno na workshop.“**

### Kontrolní seznam
Než přijdete na workshop, měli byste mít:
- [ ] účet Claude Pro,
- [ ] nainstalované Python, Git, uv, Node.js, DuckDB CLI, Claude Code a VS Code (krok 2),
- [ ] rozšíření Claude Code ve VS Code (krok 2),
- [ ] stažený repozitář (krok 3),
- [ ] proběhlé `uv sync` (krok 4),
- [ ] přihlášení do Claude Code v terminálu i ve VS Code (krok 5),
- [ ] kontrolu s výsledkem „Vše připraveno na workshop.“ a dokončenou přípravu (krok 6),
- [ ] nabitý notebook a nabíječku.

Hotovo, na workshopu začnete rovnou.

## Data
Ve složce `data/` jsou dopravní data Waze z otevřených dat města Brna za dny 14. 9. – 25. 10. 2026:

| Soubor | Obsah |
|---|---|
| `waze_jams.parquet` | Zácpy |
| `waze_alerts.parquet` | Hlášení řidičů |
| `manifest.json` | Zdroj, období, počty řádků |

Zdroj: statutární město Brno, [data.brno.cz](https://data.brno.cz), data poskytuje Waze. Při dalším použití uveďte Waze a statutární město Brno.

## Když něco nejde
- **Program „není rozpoznán“ nebo „command not found“:** otevřete nový terminál. Pokud běží VS Code, zavřete ho celý a otevřete znovu.
- **`uv sync` hlásí chybu sítě:** zkuste to znovu, případně bez firemní VPN.
- **`python --version` otevře Microsoft Store nebo nic nevypíše:** Python ještě není nainstalovaný (Windows má jen zástupce do Storu). Spusťte `winget install Python.Python.3.13` a otevřete nový terminál.
- **`winget` není rozpoznán:** nainstalujte z Microsoft Store aplikaci „App Installer“ (Instalační program aplikace), nebo stáhněte programy z jejich webů.
- **Nemáte `uv`:** knihovny jdou nainstalovat i přes pip ze souboru `requirements.txt` (Python 3.13).
