# How to register your uv environment into jupyter lab in Sagemaker Instance  

## Steps to follow:  
- install uv
- initialize uv project structure, note: uv init -p python3.11 # specified python version is a-must
- initialize project environment, uv run main.py # for the previous uv version hello.py
- activate environment, in linux: . ./venv/bin/activate or source ./venv/bin/activate, in window powershell: ./venv/Scripts/activate.ps1

```cmd
pip install uv  
uv init -p python3.11
. .venv/bin/activate
uv add ipykernel
python -m ipykernel install --user --name myenv --display-name "uv-env"  
```  

## Test and Check your Kernel
- open Jupyter Lab
- select kernel named "uv-env" # you may have to restart notebook or wait a few seconds
- check for version with

```python
import sys
print(sys.version) # it should return your sepcified python version in "uv init -p pythonX.XX"
```

## List all kernels in jupyter lab
```cmd
jupyter kernelspec list
```

## Remove your kernel 
- find your kernel variable based on the displayname # this is found in the register stage after --name

```cmd
jupyter kernelspec uninstall -f myenv
```
