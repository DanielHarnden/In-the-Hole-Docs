# JSON Loader

Various databases for *In the Hole* are stored in JSON files that can be reloaded at runtime. Since multiple different databases use the same logic to obtain data from JSON, a **JsonLoader** class has been created to make it easier to load data from JSON.

## Using the JSON Loader

To use the JSON Loader in GDScript, you must first reference the JSON Loader in your script. It's best to put this with other `@onready` or constant variables. After the JSON Loader is referenced, simply call any functions you wish to use from that reference. Below is an example.

``` gdscript
@onready var json_loader = JsonLoader
var data : Array = []

func _ready() -> void:
    data = json_loader.load_all_json_from_folder([folder path])
```

## JSON Loader Functionality

Currently, the JSON Loader only has one function:

- Load all JSON files from a given folder path. This returns an array containing dictionaries of all the loaded data.