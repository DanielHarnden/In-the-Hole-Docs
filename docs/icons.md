# Icons

Icons are the main mechanic of the slot machine. Different combinations of icons provide different [payouts](payouts.md).



## List of Icons

### ![Organic](images/icons/category_organic.png) Organic Icons
<div class="grid cards" markdown>
- [![](images/icon_cherry.png)Wood](index.md)
- [![](images/icon_cherry.png)Sap](index.md)
- [![](images/icon_cherry.png)Vine](index.md)
- [![](images/icon_cherry.png)Mushroom](index.md)
- [![](images/icon_cherry.png)Glowing Mushroom](index.md)
</div>

### ![Mineral](images/icons/category_mineral.png) Mineral Icons
<div class="grid cards" markdown>
- [![](images/icon_cherry.png)Dirt](index.md)
- [![](images/icon_cherry.png)Sand](index.md)
- [![](images/icon_cherry.png)Ruby](index.md)
- [![](images/icon_cherry.png)Sapphire](index.md)
- [![](images/icon_cherry.png)Emerald](index.md)
</div>

### ![Metal](images/icons/category_metal.png) Metal Icons
<div class="grid cards" markdown>
- [![](images/icon_cherry.png)Copper](index.md)
- [![](images/icon_cherry.png)Tin](index.md)
- [![](images/icon_cherry.png)Iron](index.md)
- [![](images/icon_cherry.png)Sulfur](index.md)
- [![](images/icon_cherry.png)Gold](index.md)
- [![](images/icon_cherry.png)Silver](index.md)
- [![](images/icon_cherry.png)Platinum](index.md)
- [![](images/icon_cherry.png)Cobalt](index.md)
- [![](images/icon_cherry.png)Tungsten](index.md)
- [![](images/icon_cherry.png)Uranium](index.md)
</div>

### ![Relic](images/icons/category_relic.png) Relic Icons
<div class="grid cards" markdown>
- [![](images/icon_joker.png)Ancient Coin](index.md)
- [![](images/icon_joker.png)Human Skull](index.md)
- [![](images/icon_joker.png)Plastic](index.md)
- [![](images/icon_joker.png)Pottery Sherd](index.md)
- [![](images/icon_joker.png)Pterosaur Fossil](index.md)
- [![](images/icon_joker.png)Tyrannosauridae Fossil](index.md)
</div>

### ![Alien](images/icons/category_alien.png) Alien Icons
<div class="grid cards" markdown>
- [![](images/icon_joker.png)Alien Egg](index.md)
- [![](images/icon_joker.png)Alien Skull](index.md)
- [![](images/icon_joker.png)Broken Alien Weapon](index.md)
- [![](images/icon_joker.png)UFO Hull Piece](index.md)
</div>

### ![Wild](images/icons/category_wild.png) Wild Icons
Only one of each wild icon can be in the slot machine at one time.
<div class="grid cards" markdown>
- [![](images/icon_joker.png)Clown](index.md)
- [![](images/icon_joker.png)Joker](index.md)
- [![](images/icon_joker.png)Jokesmith](index.md)
- [![](images/icon_joker.png)Prankster](index.md)
</div>

### ![Curse](images/icons/category_curse.png) Curse Icons
<div class="grid cards" markdown>
- [![](images/icon_mafia_man.png)Bomb](index.md)
- [![](images/icon_mafia_man.png)Durian](index.md)
- [![](images/icon_mafia_man.png)Loan Shark](index.md)
- [![](images/icon_mafia_man.png)Mafia Man](index.md)
- [![](images/icon_mafia_man.png)Wraith](index.md)
</div>



## Modding Tutorial



## Developer Information

Icons are imported from `.json` files located in the `res://Data/Icons` folder. Each `.json` file must define a set of properties for the icon. Invalid information is discarded. The following fields are parsed:

``` json
tag                 Required. If missing, the icon will NOT be imported.
category            Required. If missing, the icon will NOT be imported.

name                Optional. Defaults to "icon/[tag]".
category_name       Optional. Defaults to "category/[category]".
set_name            Optional. Defaults to "set/[set]".
texture             Optional. Defaults to "res://Slot Machine/Assets/Sprites/Icons/icon_[tag].png". If missing, a NULL texture is assigned.
```
***Note***: `name` and `category_name` are expected to correspond to localization keys. If not present in `localization.csv`, they may appear incorrectly in-game.

Here is an example of an icon in a `.json` file:
``` json
{
    {
        "tag" : "wood",
        "category" : "organic",
    }
}
```