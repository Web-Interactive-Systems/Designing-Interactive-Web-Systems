---
type: NoteCard
tags: []
---

# Designing Desktop Apps
Interactive digital landscape as we known it today has emerged in 1980’s. Prior to that, user computers were mainly operated by programmers using command line interfaces (i.e., writing programming code).

## Window

Invention of the concept of the “window” with Xerox PARC Star project, in 1980’s was a turing point in the interactive computing. Inspired by the metaphor of physical desktops (aka. desktop metaphor), researchers designed a system based on Windows, Icons, Menus, and Pointers (aka., WIMP). WIMP model brought to life most interactive GUI elements, such as buttons, navigation menus, dialogs, scroll bars, and other widgets.

> **Problem**
>
> *How to enter, fit, view, and navigate a vast amount of content larger than a screen size*

Windows are the main interfaces through which users interact with programs and perform various tasks. For example clicking on “My Documents” opens a window with interface to manipulate documents.

Mutitasking required users to access mutiple programms and functionalities at the same time, which led to techniques to managing mutiple windows along with moving, resizing, and masking windows.

*   A window is a containers of a given application.
*   Primary window: displays main functionalities of a given application (e.g., canvas+palettes).
*   Secondary window: displays secondary windows through dialogs and popovers
*   Window browser: helps view and navigate active windows

### Window organization and structure

Computer user often needs to access mutliple applications at the same time, thus organizing multiple windowns is important. Techniques to organize mutliple windows include: overlapping or floating, stacking, spliting, and panning.

Most windows structure information as scrollable, zoomable, and/or panned interfaces.

## Icons

Before the Star computer, users needed to remember and write commands to operate computer programs. Invention of icons, a small picture that represent computer objects, make it easier to interact with computers. User can click on icons to perform various tasks, such as openning a file, searching, browsing, and finding applications and documents.

## Menus

There was a need to provide users with quick access to all the different options and functionalities of a given application. Menus list the options of an given application so that users can quickly perform actions. Earliest forms of menus were linear lists. Other forms of menus includes hierachical, radial, tracking, and fisheye menus.

## Pointers

All the Star computing concepts, rely on pointing, a concept that enables selecting target objects in a two-dimensional space using pointers. Pointing rely on well-known concepts of direct manipulation. Pointers can be any device (finger, mouse, stylus, etc.).

The concept of pointing can be routed to Paul M. Fitts work on aimed movement, in the 1950’s. Fitts developed the known model of Fitts’ law that predicts how a user move a pointer (e.g., hand) to select a target.

$$
MT=a+b∗log2(A/W+1)
$$

*   MT: motion time
*   a: a user+device constant
*   b: a mouvment constant (a slow mouse)
*   A: distance to target
*   W: size of the target

## Cursor

## Caret

## Selection

## Tabs

## Toolbars, palettes, sidebars

They provide advanced controls and/or frenquently used functionalities.

Palettes are often found in Canvas-based interfaces (aka. canvas+palettes).

## Dialogs and tooltips

Secondary window: displays secondary windows through dialogs and popovers

## File system

## Desktop metaphor

Support the individual user of a stand-alone computer—typically in the context of a traditional office environment, mostly in launching apps, sorting, and retrieving documents

displaying active documents

hierarchical file system

familiarity with physical workspaces

## Challenges with desktop metaphor

*   Multitasking: accessing and viewing content
*   Context-switching: cause distraction
*   Incompatibility: different apps use different standards
*   Syncing: accessing information from any device
*   Subjectivity: individuals work with information in their own ways

In desktop, files are first-class citizen (store, copy, move, etc.), while in internet files are not

## Window management

This includes opening, moving, and resizing, scrolling content

fast task switching, fast task resumption, and easy reacquisition of mental task context after interruptions (Card and Henderson, Rooms system, 1987)