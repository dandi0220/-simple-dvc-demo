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

```
git remote add origin https://github.com/dandi0220/-simple-dvc-demo.git
```
```
git branch -M main
```
```
git push origin main
```