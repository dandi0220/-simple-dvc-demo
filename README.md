create env

```
conda create -n wineq python=3.7 -y
```

activate env
```
conda activate wineq
```

create a req file

install the packages in the req file
```
pip install -r requirements.txt
```
data source

https://drive.google.com/drive/folders/18zqQiCJVgF7uzXgfbIJ-04zgz1ItNfF5

```
git init
```
```
dvc init
```
```
dvc add data_given/winequality.csv
```
```
git add .
```

```
git commit -m "first commit"
```
Oneliner update for readme file
```
git add . && git commit -m "update Readme.md"
```

```
git remote add origin https://github.com/dandi0220/-simple-dvc-demo.git
git branch -M main
git push origin main
```

tox command  
```
tox
```
for rebuilding  
```
tox -r
```
pytest command 
```
pytest -v
```

setup command
```
pip install -e .
```
build your own package command
```
python setup.py sdist bdist_wheel
```
---
create an artifacts folder

mlflow server command -
```
mlflow server --backend-store-uri sqlite:///mlflow.db --default-artifact-root ./artifacts --host 0.0.0.0 -p 1234
mlflow server \
    --backend-store-uri sqlite:///mlflow.db \
    --default-artifact-root ./artifacts 
    --host 0.0.0.0 -p 1234


mlflow server --backend-store-uri sqlite:///mlflow.db --default-artifact-root ./artifacts --host 127.0.0.1 -p 5000
```

