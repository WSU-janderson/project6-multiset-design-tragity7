## CS3100 Project 6 - MultiSet
**Sidra Ali**

The data set I'm intending to use for my game design is Project 4's Hashtable. 

###Introduction:

A multiset is a set that has elements that appear more than once. As such, multisets will serve as a core data structure for the game in any situation where elements appear multiple times. I've chosen the example of the player's inventory. 

My design models a player inventory for a game where elements are identified by string names and may appear multiple times (e.g. "Potion" × 3, "Arrow" × 12). The MultiSet is built atop a HashTable(HashMap) implementation: HashTable<string, unsigned int> where the value stores the count (quantity of item in inventory) for each string key.
