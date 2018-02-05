### Word Stack

This repository contains the code for the Google: Applied CS with Android course. This course revisits and implements concept from Data Structures and Algorithms as well as Artificial Intelligence.
The app for this workshop is a single-user word game called WordStack. The idea of the game is to try to separate out two words of the same length whose letters have been scrambled (but the order of the letters has been preserved). For example, 'cat' and 'dog' might get scrambled in many ways but 'c' will always come before 'a' and 'a' will always come before 't'. Similarly, 'd' will always come before 'o' and 'o' will always come before 'g'. So we get permutations like:

* cdaotg
* cadogt
* catdog
* dogcat
* dcoagt
* ...
But never 'actdog' ('a' is out of order) or 'coatdg' ('o' out of order).

This is pretty easy to solve when you can see the whole scrambled string and for short words but it gets much harder when you can only see one letter at a time and attempt longer words.

**Tour of code**

The starter code is broken up into three classes:

* MainActivity which is at the heart of this app. It handles both initializing the app and responding to user input.
* onCreate loads up the dictionary and finishes creating the UI.
* TouchListener.onTouch moves the top tile to either of the white areas when the user touches the area.
* DragListener.onDrag handles dragging the tiles around the screen. We'll implement that functionality later in the workshop. It is disabled for now.
onStartGame and onUndo: handler for the on-screen buttons. Currently, they do nothing.
* StackedLayout: The Android SDK contains several ViewGroup classes which are used to organize UI items. Some of the most common are LinearLayout to line up the items horizontally or vertically and RelativeLayout that allows items to be placed relative to each other. For this game, we will subclass LinearLayout to make a special layout that only shows the last View added to it. We will use this to represent the stack of tiles.
  * push, pop: you will need to implement
  * peek, empty are simple wrappers around Java's Stack
  * clear will remove all tiles from the ViewGroup
* LetterTile: A subclass of the TextView class that draws a single letter in the appropriate size and colors. You may need to adjust the tile and font size to fit your screen.
  * moveToViewGroup: Move the current tile to a different ViewGroup. Removes the current tile from whatever ViewGroup it is currently in and adds it to the other specified ViewGroup. Returns true if that moves concludes the game.
  * freeze, unfreeze: Will be used to keep a tile from being moved after it is placed.
  * onTouchEvent: Handles the tile being touched by the user. So far it just calls its superclass but we will add more functionality to make the tile draggable.
