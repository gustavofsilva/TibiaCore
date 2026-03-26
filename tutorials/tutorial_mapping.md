# Tutorial: Mapping and World Editing

TibiaCore uses the `.otbm` map format, compatible with the **Remere's Map Editor (RME)**.

## Map Location
The world files are located in `data/world/`:
*   `map.otbm`: The actual map file.
*   `houses.xml`: Definitions of player houses.
*   `spawns.xml`: Locations where monsters will spawn.

## Editing the Map
1.  **Download RME**: Obtain a version compatible with your Tibia client version.
2.  **Configuration**: Load the `items.otb` (usually in `data/items/`) and the client's `Tibia.dat`/`Tibia.spr`.
3.  **Opening the Map**: Open `data/world/map.otbm`.

### Common Tasks:
*   **Drawing Terrain**: Use the Ground/Walls brushes.
*   **Creating Houses**: Use the House Tool to define doors and tiles.
*   **Setting Spawns**: Place "Spawn" fire effects on the map and add monsters to them.

---

## Applying Changes
1.  Save the map in RME.
2.  Ensure the file name in `config.lua` matches (`mapName = "map"`).
3.  **Restart the server** to load the new map data.

> **Note**: Always keep backups of your `map.otbm` before making large changes!
