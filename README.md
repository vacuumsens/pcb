# PCB Schematic Projects

KiCad PCB design projects for VacuumSens.

## Project Structure

```
SchematicProjects/
├── libs/                    # Centralized component libraries
│   ├── easyeda2kicad.kicad_sym
│   ├── easyeda2kicad.pretty/
│   └── easyeda2kicad.3dshapes/
├── charging-circuit/V1/     # Charging circuit project
├── RS232-converter/V1/      # RS232 converter project
└── ...
```

## Importing Components from EasyEDA/LCSC

There are two methods to import components:

---

### Method 1: Command Line (easyeda2kicad)

Best for batch imports or when you know the LCSC part number.

#### Prerequisites

Install the `easyeda2kicad` Python tool:

```bash
pip install easyeda2kicad
```

#### Import a Component

Use the alias (already configured in `.zshrc`):

```bash
easyeda2kicad-import <LCSC_ID>
```

**Example:**
```bash
easyeda2kicad-import C49018
```

This downloads the symbol, footprint, and 3D model to the centralized `libs/` folder.

#### Manual Import (without alias)

```bash
easyeda2kicad --full --overwrite --output /Users/andrewyanez/Documents/KiCad/7.0/symbols/SchematicProjects/libs --lcsc_id C49018
```

---

### Method 2: KiCad Plugin (EasyEDA/LCSC Plugin)

Best for browsing and importing directly within KiCad.

#### Installation

1. In KiCad, go to **Plugin and Content Manager**
2. Search for "EasyEDA" or "LCSC"
3. Install the plugin

#### Usage

1. Open your KiCad project
2. Go to **Tools → EasyEDA Library** (or similar menu item)
3. Search for a component by name or LCSC part number
4. Click **Import** - the plugin will create:
   - `LCSC/EasyEDA.kicad_sym` (symbols)
   - `LCSC/EasyEDA.pretty/` (footprints)
   - `LCSC/EasyEDA.3dshapes/` (3D models)

**Note:** The plugin saves files locally in your project folder under `LCSC/`. This is project-specific, not centralized.

---

### After Importing (Both Methods)

1. Open your KiCad project
2. The library should be available in the schematic/PCB editor
3. Add the new symbol/footprint to your design
4. Commit changes to git:
   ```bash
   git add -A && git commit -m "Add component CXXXXX"
   git push
   ```

---

### Which Method to Use?

| Method | Pros | Cons |
|--------|------|------|
| **easyeda2kicad** (CLI) | Centralized in `libs/`, shared across projects | Requires terminal |
| **KiCad Plugin** | Visual browsing, integrated in KiCad | Project-local, can create duplicates |

**Recommendation:** Use the CLI for components you'll reuse. Use the plugin for quick project-specific imports.

## Library Configuration

Projects reference the centralized library using relative paths:

**sym-lib-table:**
```
(lib (name "easyeda2kicad")(type "KiCad")(uri "${KIPRJMOD}/../../libs/easyeda2kicad.kicad_sym"))
```

**fp-lib-table:**
```
(lib (name "easyeda2kicad")(type "KiCad")(uri "${KIPRJMOD}/../../libs/easyeda2kicad.pretty"))
```

## Finding LCSC Part Numbers

1. Go to [LCSC.com](https://www.lcsc.com) or [JLCPCB Parts](https://jlcpcb.com/parts)
2. Search for your component
3. The LCSC part number starts with "C" (e.g., C49018)
