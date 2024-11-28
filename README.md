# dvc-driver-demand-capstone
DVC (Data Version Control) is an open-source version control system designed to handle large datasets, machine learning models, and other files that are difficult to version with traditional Git. It extends Git to provide version control for data and machine learning workflows, enabling teams to collaborate more efficiently and manage large data artifacts.

## Initialize DVC repository:
Create a new GitHub repo

## Start a codespace

## Upload data (data/train.csv)

## Create and activate venv

## Install packages:
pip install dvc==3.55.2 dvc-s3==3.2.0

## Initialize dvc repository:
dvc init

## Configure Remote Storage:
Add remote storage:
dvc remote add -d myremote s3://<bucket>/<folder>/

## Provide AWS credentials: (will be stored locally)
dvc remote modify --local myremote access_key_id <>
dvc remote modify --local myremote secret_access_key <>

## Commit remote-storage config:
git add .dvc/config
git commit -m "remote storage configured"
git push

## Data Versioning:
Add data for dvc tracking:
dvc add data/train.csv

## Add metadata files for git tracking:
git add data/.gitignore data/train.csv.dvc

## Commit changes in git:
git commit -m "Initial data"

## Tag the data:
git tag -a v1.1 -m "Dataset v1.1"
The git tag command in Git is used to create a reference to a specific point in your repository’s history, typically to mark a particular commit as important. Tags are often used to denote releases (e.g., version 1.0, 2.0, etc.).

## Push data to remote-rtorage:## 
dvc push

## Push metadata file to git repo:
git push

## Push tag:
git push origin v1.1

## Whenever new data comes in, use the below commands in sequence:
dvc status
dvc add data/train.csv
git add data/train.csv.dvc
git commit -m "dataset updated"
git tag -a v1.x -m "Dataset v1.x"
dvc push
git push
git push origin v1.x
