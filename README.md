# Retro-data-structures
Construct type definitions for Retro Studios game

| Format   | Prime 1 (Read) | Prime 1 (Write) | Prime 2 (Read) | Prime 2 (Write) | Prime 3 (Read) | Prime 3 (Write) |
| -------- | -------------- | --------------- | -------------- | --------------- | -------------- | --------------- |
| PAK      | &check;        | &check;         | &check;        | &check;         | &cross;        | &cross;         |
| MLVL     | &check;        | &cross;         | &check;        | &cross;         | &check;        | &cross;         |
| MREA     | &cross;        | &cross;         | &check;        | &cross; [2]     | &cross;        | &cross;         |
| CMDL     | &check;        | &check;         | &check;        | &check;         | &cross;        | &cross;         |
| ANCS     | &check;        | &check;         | &check;        | &check;         | &cross;        | &cross;         |
| ANIM     | &check;        | &check;         | &check;        | &check;         | &cross;        | &cross;         |

* [1] File offsets must be changed manually
* [2] Missing re-calculation of how sections are split between blocks.


## Example Usage

```python
from retro_data_structures.pak import PAK

def read_file(path):
    with open(path, "rb") as f:
        return f.read()
    
PAK.build_file({
    'named_resources': [
        {"asset": {"type": 'TXTR', "id": 201335801}, "name": 'TXTR_ElevatorIcon_1'},
        {"asset": {"type": 'TXTR', "id": 239414538}, "name": 'TXTR_ElevatorIcon'},
        {"asset": {"type": 'TXTR', "id": 564256465}, "name": 'TXTR_QuaterCurve'},
        {"asset": {"type": 'TXTR', "id": 568030977}, "name": 'TXTR_SaveStationIcon_1'},
    ],
    'resources': [
        {
            "asset": {"type": 'TXTR', "id": 201335801},
            "compressed": 1,
            "contents": {"value": read_file("ElevatorIcon_1.TXTR")},
        },
        {
            "asset": {"type": 'TXTR', "id": 201335801},
            "compressed": 1,
            "contents": {"value": read_file("ElevatorIcon.TXTR")},
        },
        {
            "asset": {"type": 'TXTR', "id": 201335801},
            "compressed": 1,
            "contents": {"value": read_file("QuaterCurve.TXTR")},
        },
        {
            "asset": {"type": 'TXTR', "id": 201335801},
            "compressed": 1,
            "contents": {"value": read_file("SaveStationIcon_1.TXTR")},
        },
    ]
}, "Game.pak")

```
