# Sanity-Check-Technical-Breakdown WIP
Snippet and technical breakdown of the elements worked on for the game, Sanity Check, a 5-person submission for the Brackey's Game Jam.

- Currently Being Worked On

Current Link to the Project
https://saisgonerogue.itch.io/sanity-check 

# Sanity Check - Systems Engineer, Systems Designer, and Audio Engineer

The purpose of this README, is to serve as a means of explaining my contributions to the game, Sanity Check, for the Brackey's Game Jam, developed by Christopher, Jack, Logan, Sai, and Tyler. 

Link to the project: https://saisgonerogue.itch.io/sanity-check

## :busts_in_silhouette: Roles

### System Engineer & Designer
During development, I focused on general architecture, procedural systems, and object data management. For the general architecture, Imade sure every file was properly communicating only the information needed, keeping a standard of encapsulation and decoupling systems from one another which never needed any connection. The procedural algorithms were managed between me and Logan, incorporating seeding and static helper functions to avoid overreliance on any single file. Object data management, was separated between what was made in scene, versus universal details all objects of the type shared, built around template standards. 

### Audio Engineer
As an audio engineer, I focused on creating the ambience and music composition for the project. For the software, early on we settled on FMod (this may or may not have caused issues later), used Musescore for composing, and Reaper for audio mixing. Because I was also the audio engineer and the system engineer, I worked on a procedural audio generator inspired by how events are handled in SCP: Containment Breach. 

## :memo: Quick Breakdown and Overview
### Procedural Room Generator
- Random seed-based system, communicating with a logic solver for a knight & knaves problem, to generate following rooms with the correct solution
- Places objects and doors in the room at random, using a range data following a 2d list, with designated positional values along the x and y plane, to prevent overlapping placements
- Objects generated, provide instanced variations of cases and logical facts from their Scriptable Objects to the logic solver to create new factual statements. All facts are dynamically stored to allow for future rooms to reference any n number of rooms back of that object's logical fact
### Procedural Audio Generator
- Random seed-based, weighted system, split between audio events (ordered_set) and audio environments (list)
- Coroutine management of dynamic audio file sizes
### General Architecture
- Game manager, audio manager, coroutine manager, and an event manager
- Event manager tracks signals/actions/triggers, decoupling systems from each one another
- 
### Object Data Management
- The data for all room placed objects handled through Scriptable Objects
- Every object has a template script, for any methods, or dedicated features those objects may continue in the feature

Still Work In Progress, will be posting Miro and Whiteboard design research and exploration


