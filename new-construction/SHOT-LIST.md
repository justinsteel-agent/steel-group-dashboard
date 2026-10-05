# New Construction — Mission Shot List

Every community gets the same 7 shots. Same slots on the community page, the explorer card, and social. Shoot all 7 on one visit; the Mission Report maps each file to a slot.

| Slot | Shot | Crop | Where it shows |
|---|---|---|---|
| `hero` | Community entrance / monument sign, straight-on, late light | 16:9 (1920×1080) | Page header (fixed height, no parallax), explorer card image, social cover |
| `streetscape` | One finished street, standing in the road, homes both sides | 3:2 (1500×1000) | Page gallery tile 1 |
| `model_exterior` | Model home front elevation, 3/4 angle, no cars | 3:2 | Page gallery tile 2, floor-plan fallback |
| `amenity` | The signature amenity (pool, clubhouse, trail, pond) | 3:2 | Page gallery tile 3 |
| `interior` | Model home main living space, wide, natural light | 3:2 | Page gallery tile 4 |
| `lots` | Available lots / phase under construction (shows runway) | 3:2 | Page gallery tile 5 |
| `context` | What's next door: the drive-in, the nearest shopping, the water, the highway — honest | 3:2 | Page "Things buyers should consider" |

Per floor plan (optional, from the sales center's plan sheets): `plan_<name>` at 4:3 — this switches on the AgentFire Floorplans block.

Rules
- Horizontal only. Phone is fine; hold it level. No people, no cars with plates, no builder signage close-ups other than the monument.
- Files go to the mission folder `01 — Raw Uploads`; the Mission Report names which file is which slot. The audit/ingest step writes URLs into `communities.json` → `media.<slot>`.
- A slot with no image renders as a flat ivory panel with the slot label — never a stock photo.
