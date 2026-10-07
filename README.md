# Sanity-Check-Technical-Breakdown (WIP)
Snippet and technical breakdown of the elements worked on for the game, Sanity Check, a 5-person submission for the Brackey's Game Jam.

- Currently Being Worked On

Current Link to the Project
https://saisgonerogue.itch.io/sanity-check 

# Sanity Check - Systems Engineer, Systems Designer, and Audio Engineer

The purpose of this README, is to serve as a means of explaining my contributions to the game, Sanity Check, for the Brackey's Game Jam, developed by Christopher, Jack, Logan, Sai, and Tyler. Sanity Check is a logical puzzle game, inspired by the Knight and Knaves which can be solved through propositional logic. Each door either tells the truth or lies, and only one door provides a safe path to the next room.

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
- Multiple managers for different systems, which keep the number of MonoBehaviour scripts lower
### Object Data Management
- The data for all room placed objects handled through Scriptable Objects
- Every object has a template script, for any methods, or dedicated features those objects may continue in the feature

# Technical Breakdown
## Initial Conceptualiazation
For early conceptualization and planning was conducted through Miro, with several different boards to demonstrate our goals and direction.
Below are some of the boards we had.

<img width="1212" height="547" alt="image" src="https://github.com/user-attachments/assets/646d8e04-719f-48a4-8e77-b4139f369376" />
<img width="1117" height="633" alt="image" src="https://github.com/user-attachments/assets/74aa709d-ea8e-42c8-af46-361b2e8f7af0" />

Below was a reference to different propositional logic.

<img width="648" height="255" alt="image" src="https://github.com/user-attachments/assets/759c13ac-e1bb-43e2-bd20-3e1afd5b5ac2" />

When getting into specific systems, often we communicated our ideas through whiteboard drawings as well to help quickly iterate through concepts on the fly.

## Room Generation
Room gen and object gen within those rooms are considered separate. When generating a room, there is a general procedure, due to communication between the logic solver and the procedural generator. The logic solver provides a safe door, but only once given all possible facts and details in the room. For example, the code snippet below is part of the logic solver, which is the information it requires.

<img width="572" height="832" alt="image" src="https://github.com/user-attachments/assets/fbae3876-90c9-46f8-8ae6-278d74b41a5b" />

Because the logic solver needs information, we ended up dividing a back and forth system. The process starts by providing all current facts to the logic solver, and saving the solution. Once the solution is saved, it grabs the location of the current safe door, and places the next room of increasing size after, to keep the player always entering a new room in the center rather than an edge. Much of the process is abstracted or separated into specific functions which are reused throughout the codebase. 

<img width="727" height="606" alt="image" src="https://github.com/user-attachments/assets/e6d0d748-db1e-42be-b09d-78242a442e8c" />

Each room is stored in a class data, structured as WorldState >> RoomState >> RoomSpace >> RoomRow. By organizing the data through this format, it makes providing a series of data of the current room, and all past rooms to the logic solver.

<img width="183" height="121" alt="image" src="https://github.com/user-attachments/assets/5ad20674-deff-40a1-86bb-b8d7f2948277" />



## Object Generation (WIP)
<img width="500" height="750" alt="image" src="https://github.com/user-attachments/assets/a78f0e4b-2e4f-4164-b2e7-d2aed96c2902" />
<img width="500" height="560" alt="image" src="https://github.com/user-attachments/assets/bde63e2b-4535-4eaf-8a79-68651c77290a" />



# Still Work In Progress, will be posting Miro and Whiteboard design research and exploration


