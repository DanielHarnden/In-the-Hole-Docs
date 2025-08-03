# Payouts

Payouts are triggered when a row of [icons](icons.md) matches a predetermined payout.
<br><br>



## Payout Logic

The slot machine works based on a 3x3 grid. Icons are considered "matching", triggering a payout, if one of the following rows matches an existing payout: 

* The top row.
* The middle row.
* The bottom row.
* The diagonal row from top left to bottom right.
* The diagonal row from bottom left to top right.

In the following example, the rows would be as follows:

| ![Cherry](images/icon_cherry.png) -|- ![Grapes](images/icon_grapes.png) -|- ![Cherry](images/icon_cherry.png) |<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/<br>
| ![Cherry](images/icon_cherry.png) -|- ![Lemon](images/icon_lemon.png) -| ![Cherry](images/icon_cherry.png) |<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<br>
| ![Cherry](images/icon_cherry.png) -|- ![Grapes](images/icon_grapes.png) |- ![Cherry](images/icon_cherry.png) |

* Cherry, Grapes, Cherry
* Cherry, Lemon, Cherry
* Cherry, Grapes, Lemon
* Cherry, Lemon, Cherry
* Cherry, Lemon, Cherry

A payout row can be in any order, meaning that the row `Cherry, Cherry, Lemon` would be handled identically as `Lemon, Cherry, Cherry`.

<br><br>



## Fruit Payouts
| Row | Payout | Payout Name |
| :-: | :----: | :---------: |
| ![Cherry](images/icon_cherry.png)![Cherry](images/icon_cherry.png)![Cherry](images/icon_cherry.png) | <span class="payout-money">$1</span> | Triple Cherries |
| ![Cherry](images/icon_cherry.png)![Cherry](images/icon_cherry.png)![Grapes](images/icon_grapes.png) | <span class="payout-money">$5</span> | Double Cherries, Single Grape |
| ![Cherry](images/icon_cherry.png)![Cherry](images/icon_cherry.png)![Lemon](images/icon_lemon.png) | <span class="payout-money">$25</span> | Double Cherries, Single Lemon |
| ![Grapes](images/icon_grapes.png)![Grapes](images/icon_grapes.png)![Grapes](images/icon_grapes.png) | <span class="payout-money">$10</span> | Triple Grapes |
| ![Grapes](images/icon_grapes.png)![Grapes](images/icon_grapes.png)![Lemon](images/icon_lemon.png) | <span class="payout-money">$35</span> | Double Grapes, Single Lemon |
| ![Lemon](images/icon_lemon.png)![Lemon](images/icon_lemon.png)![Lemon](images/icon_lemon.png) | <span class="payout-money">$50</span> | Triple Lemon |
| ![Cornucopia](images/icon_cornucopia.png)![Cornucopia](images/icon_cornucopia.png)![Cornucopia](images/icon_cornucopia.png) | <span class="payout-money">$5,000</span> | Triple Cornucopia |

<br>



## Weapon Payouts
| Row | Payout | Payout Name |
| :-: | :----: | :---------: |
| ![Spoon](images/icon_spoon.png)![Spoon](images/icon_spoon.png)![Spoon](images/icon_spoon.png) | ![Spoon](images/icon_spoon.png) | Triple Spoon |

<br>



## Ability Payouts
| Row | Payout | Payout Name |
| :-: | :----: | :---------: |

<br>



## Wild Payouts
| Row | Payout | Payout Name |
| :-: | :----: | :---------: |
| ![Joker](images/icon_joker.png)![Joker](images/icon_joker.png)![Joker](images/icon_joker.png) | N/A | Joker Fever |

<br>



## Curse Payouts
| Row | Payout | Payout Name |
| :-: | :----: | :---------: |
| ![Mafia Man](images/icon_mafia_man.png)![Mafia Man](images/icon_mafia_man.png)![Mafia Man](images/icon_mafia_man.png) | <span class="debt-money">-$1,000</span> added to the player's debt | Triple Mafia Man |

<br>



## Developer Information

Icons are imported from `.json` files located in the `res://Data/Icons` folder. Each `.json` file must define a set of properties for the icon. Invalid information is discarded. The following fields are parsed:

``` json
tag                 Required. If missing, the icon will NOT be imported.
match               Required. An array of the icon IDs required to achieve the match. If missing, defaults to "NULL", meaning the payout can never be achieved.
reward_money        Optional. The amount of money rewarded. If missing, the payout will not reward money.
reward_item         Optional. The tag (or array of tags) of the item reward. If missing, the payout will not reward an item.

match_array_str     Auto-Generated. A string version of the match array to speed up processing of matches.
```

Here is an example of a payouts in a `.json` file:
``` json
{
    {
		"tag" : "trip_cherry",
		"match" : ["cherry", "cherry", "cherry"],
		"reward_money" : 5,
	},

    {
		"tag" : "trip_spoon",
		"match" : ["spoon", "spoon", "spoon"],
		"reward_item" : "spoon",
	},
}
```