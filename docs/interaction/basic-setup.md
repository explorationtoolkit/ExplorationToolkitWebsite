icon: material/gesture-tap-hold

# :material-gesture-tap-hold: Basic Setup

## What is an Interaction?

When you look at an object or hover your mouse over an object, certain things can happen. You could interact with a door to open it, click on a keypad button to enter the number, or interact with a lever to pull it.

YOUTUBE VIDEO

## Setup

If you want an object to be interactable, add the **Interactable** component.

In order for these Interactable components to work, you also need one **InteractionController** component in the scene. This sends out raycasts to detect what you're currently looking at.

## Interact Methods

On the Interactable component, you may notice there's an interact method property. There are 2 types of interactions that can occur and you can filter Interactable components to detect all or one of them:

* **World** - Detected when you aim the center of the camera at something. E.g. opening a door, picking up an item.

* **Cursor** - Detected when you aim the mouse cursor at something. E.g. clicking buttons on a keypad when the camera is zoomed into it, clicking on hints when inspecting an item.