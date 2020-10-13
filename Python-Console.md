# Python Console in UnityMol X
----------

## Exhaustive list of functions

See [API.md](https://gist.github.com/nezix/fd15bafcdd339ac5e5e3d22dee4812de)

------

Python integration in UnityMol X is done using IronPython. It is a powerful python integration without needing to do every bindings for a function meaning that you can call every C# and Unity class/methods (for example `GameObject.Find("Main Camera").transform.position = Vector3(0.1,0.2,0.3)`).

However, **not every python modules are available** (eg. numpy, scipy, ...).

An API is defined to perform all the actions from the UI.

### To show (and hide) the console press the ```CTRL```+```<space bar>``` key combination

## Some examples of commands in the APIPython

```python
load("filePath")
```
```python
fetch("1KX2")
```
```python
select("1KX2 and resname CYS", "mySelection")
```
```python
show("cartoon")
```
```python
hide("hb")
```
```python
showSelection("mySelection", "line")
```
```python
hideSelection("mySelection", "line")
```
```python
centerOnSelection("mySelection")
```
```python
loadTraj("structureName", "filePath.xtc")
```
```python
delete("structureName")
```
```python
colorSelection("mySelection", "line", "red")
```
```python
colorByChain("mySelection", "s")
```
```python
renameSelection("mySelection", "myNewSelection")
```
```python
screenshot("C:/Users/myUserName/Desktop/UMolScreenshot1.png")
```
```python
startVideo("C:/Users/myUserName/Desktop/UMolVid1.mp4")
stopVideo()
```
```python
connectIMD("myStructure", "127.0.0.1", 8888)
disconnectIMD("myStructure")
```


---------------------------------

