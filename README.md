# Lahmacun-Modpack
Das Modpack für unsere lahmacun-Server (Minecraft 1.21.11, Fabric), gebaut mit [packwiz](https://packwiz.infra.link/).
Ihr müsst hier nichts runterladen: Eure Prism-Instanz holt sich bei jedem Start selbst die neueste Version.
Eure eigenen Mods bleiben dabei, wie sie sind. Angefasst werden nur die Mods, die hier im Pack stehen.

## Für euch: einmal einrichten
1. [Prism Launcher](https://prismlauncher.org/) installieren und mit eurem Microsoft-Konto anmelden.
2. Die Lahmacun-Zip, die ich euch schicke, in Prism reinziehen.
3. Starten. Beim ersten Mal lädt er das ganze Pack, danach nur noch Updates.
4. Eigene Mods könnt ihr ganz normal über Bearbeiten → Mods → Mods herunterladen dazupacken. Falls Prism dabei eine Mod mitinstallieren will, die schon im Pack ist (z. B. Fabric API): Haken raus.

## Für mich: das Pack pflegen
Alles im Pack-Ordner ausführen (`packwiz` liegt in `%USERPROFILE%\go\bin`).

| Was | Befehl |
|---|---|
| Mod von Modrinth dazu (am besten) | `packwiz modrinth install <slug>` (Slug steht in der URL der Mod, z. B. `sodium`) |
| Mod von CurseForge dazu | `packwiz curseforge install <slug>` |
| Mod nur für den Client | danach in `mods/<mod>.pw.toml` auf `side = "client"` stellen, dann `packwiz refresh` |
| Eine Mod / alle Mods updaten | `packwiz update <mod>` / `packwiz update --all` |
| Mod raus | `packwiz remove <mod>` |
| Neue lahmacun-mod-Version | Jar als Release `lahmacun-mod-<version>` hier hochladen, dann `packwiz url add Lahmacun <Jar-Link> --meta-name lahmacun-mod` (überschreiben) |
| Was ist drin? | `packwiz list` |

Danach raushauen: `git add -A`, `git commit -m "..."`, `git push`.
GitHub cached die Dateien bis zu 5 Minuten. Also nach dem Pushen kurz warten, bevor alle neustarten.

Aufpassen: `packwiz update` nimmt immer die neueste Version, auch Betas (war bei Sodium so). Nach dem Updaten kurz in `mods/<mod>.pw.toml` gucken, welche Version drin ist, oder die Mod gezielt mit einer stabilen Version neu hinzufügen.

## Für mich: die Zip für alle exportieren
In Prism: Lahmacun → Exportieren → Prism-Zip. Meine eigenen Mods (alles in `mods/`, was nicht im Pack steht) und `packwiz.json` abwählen. Drin bleiben müssen `packwiz-installer-bootstrap.jar` und die Instanz-Einstellungen mit dem Pre-Launch-Befehl:

```
"$INST_JAVA" -jar packwiz-installer-bootstrap.jar https://raw.githubusercontent.com/ardacpp/lahmacun-pack/main/pack.toml
```
