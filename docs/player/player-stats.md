icon: material/chart-box-outline

# :material-chart-box-outline: Player Stats

Player stats can be used to keep track of coins, keys, items, and other collectables.

## Creating a stat

A stat is represented via a ScriptableObject. To create one, right click in the Project window and go `Create > Exploration Toolkit > Player Stat`. Give the file a name, then you can fill in the properties.

IMAGE OF PLAYER STAT INSPECTOR

Set the properties as you see fit. This is merely an object that represents the rules and icon of the stat. It doesn't hold the stat value. That's controlled by the **PlayerStatManager**.

## Player Stat Manager

If you wish to use player stats in your scene, drag in the PlayerStatManager prefab, located in the `Core > Prefabs > Systems > Management` folder.

The main component keeps track of the current value of each stat assigned to it in the Inspector. So make sure, for every stat you wish to use, add it to the list.

The child canvas is used to render these stats on-screen. If you want to use another canvas, then you can do so.