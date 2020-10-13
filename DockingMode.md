# Docking mode

### UnityMol 1.36

This page presents the implementation of the docking mode for UnityMol, developed by João Rodriguez and Xavier Martinez mostly at Stanford University.

The docking mode is designed to work in VR (although it can be activated in desktop mode).

## Docking Mode details

The code behind the docking mode uses the AMBER force field and is designed to work for proteins. A separated thread computes the potential energy of the system, UnityMol displays the last computed energy value.
The code is in C++ (not yet multi-threaded) but there is a C# implementation in case the C++ shared library is not found or does not exist for your platform.

You can find workarounds to make simple ligand molecules work (change atom names to match AMBER nomenclature) but this would be a coarse energy approximation.

Scale both VdW and electrostatic terms to reduce the impact of one term on the displayed energy by using the UI fields :
![image](uploads/cab62d14ae1bc86a83962b06e1a78307/image.png)

By default, all loaded structures take part of the docking. Structures can be ignored if you set the flag ```mystructure.ignoreDocking = True```.

## How to activate

- Using the UI :
![image](uploads/ec64f350a4d5586d8346937366dec833/image.png)

- Using the command line : 
```python
switchDockingMode()
```

## Docking interaction

For performance reasons (Nvidia PhysX engine), only alpha carbons have colliders and bump into each others. You will see red circles around atoms that collide and the VR controllers will vibrate to make you feel the collisions.

I recently added a way to change colliders based on residue names or atom names.

Note that it is still quite hard to slightly move molecules without having a large energy variation and interaction will be improved to tackle this issue.

### Freeze and Unfreeze

The default behavior of the docking mode makes molecules react when you bump them with another molecule. Using the freeze button, you fix the molecules so that when you collide with them, they will not move.

## Save docking conformation

You can save the current docking conformation in a PDB file by using the command :
```python
saveDockingState("path/dockingState1.pdb")
```
Clicking on the UI menu will save the current docking state in a PDB file named "Unitymol_dock_N.pdb" where N is the number of existing files starting with "Unitymol_dock_" in "current_user_desktop/UnityMolDocking/".

