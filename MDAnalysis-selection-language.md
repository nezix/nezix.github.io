# MDAnalysis selection language

Please refer to MDAnalysis documentation ([here](https://www.mdanalysis.org/docs/documentation_pages/selections.html)) for a detailed explanation about the language and some examples.

## Select from the python console
```python
select("water within 3.0 not protein") #default name of the selection will be "selection"
select("chain A and resid 1:10","name of my selection")
```
### Note that `select` applies to all loaded molecules. If you want to apply only on a molecule do:

```python
select("1KX2 and not protein")
```

## Create a selection in C# #

```csharp
MDAnalysisSelection selec = new MDAnalysisSelection("protein and water", s.currentModel.allAtoms); #A list of UnityMolAtom
UnityMolSelection ret = selec.process();
```

### Note that one can name a selection and use it in another selection, example:
```python
select("1KX2 and ligand", "myLigandSel")
addSelectionKeyword("myLigand","myLigandSel")#Record the myLigand keyword associated to myLigandSel selection
select("myLigand and type FE","FELigand")
```
## Examples of selections
```python
select("prop y > 0.0", "aboveZero")
```
