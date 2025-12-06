## CS3100 Project 6 - MultiSet
**Sidra Ali**

The data set I'm intending to use for my game design is Project 4's Hashtable. 

### 1. Introduction:

A multiset is a set that has elements that appear more than once. As such, multisets will serve as a core data structure for the game in any situation where elements appear multiple times. I've chosen the example of the player's inventory. 

My design models a player inventory for a game where elements are identified by string names and may appear multiple times (e.g. "Potion" × 3, "Arrow" × 12). The MultiSet is built atop a HashTable(HashMap) implementation: HashTable<string, unsigned int> where the value stores the count (quantity of item in inventory) for each string key.

### 2. Design Philosophy:

Since the player is going to often use the inventory feature, it needs to be **efficient** enough to load quickly and **simple** enough that it doesn't distract from the actual gameplay. I would want the inventory to have a user-friendly interface and make sure it's **accessible** for players of various demographics (like age, fluency in English, people who have difficulty reading a screen, etc.). Another quality the inventory requires is **robustness**, as in it doesn't show any errors or undefined messages if a player does something unconventional. Keeping in mind that I may have future updates or newer versions of my game, the inventory feature needs to be easily **extensible** so I can add features without breaking the pre-existing interface. 

The inventory is a core container of the game, but the game will also have other contained systems that may need to work with it (like how Minecraft's inventory needs to work with the crafting table) so the main client will be other game subsystems. Besides that, users of multiset would most likely be game developers.

### 3. Core Operations:

![core operations table](https://github.com/WSU-janderson/project6-multiset-design-tragity7/blob/main/core%20operations%20table.png)

Table 1: Core Operations
Source: me on powerpoint

## Set Operations:

The two set operations I'm going to expand on are `union_with()` and `intersection_with()`

**union_with()**
- What it accomplishes in gameplay: combines two or more items together. so if I pick up a chest with multiple items in it, I don't have to individually add each item to inventory, they're counted as one thing/union
- How it manipulates my data structure: uses hash lookups on result
- Its conceptual complexity: O(n1 + n2) expected, where n1 and n2 are distinct-key counts/items in the two multisets
- Relevant edge cases: if the order of items being grouped together matters, then you can't use union, you need to add them separately

**intersection_with()**
- What it accomplishes in gameplay: teo features which share the same item (if I'm crafting a bed and a table, wood is an item that is found in both)
- How it manipulates my data structure: lookup per key in the other table and an insert into result 
- Its conceptual complexity: O(k) where k is number of shared keys
- Relevant edge cases: there's no intersection, return null set

## Extension Feature

I'm choosing to add the `craftRecipe()` feature because I'm designing an inventory using multisets. It would be very convenient if items from the inventory can be combined to create other items because when I gain a new item, the intersection can tell me what things I can potentially make from it. 

