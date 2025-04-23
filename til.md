# Rebase TIL

## code feature 1
``` bash
git checkout main;
git checkout -b feature1;
touch feature1-1;
git add .; 
git commit -am "feature1-1";
touch feature1-2;
git add .; 
git commit -am "feature1-2";
```
## code feature 2
``` bash
git checkout main;
git checkout -b feature1;
touch feature1-1;
git add .; 
git commit -am "feature1-1";
touch feature1-2;
git add .; 
git commit -am "feature1-2";
```

## rebase feature1
- fast forward main to the head of branch feature1, since main is just an ancestor of feature1. 
``` bash
git checkout main;
git rebase feature1;
```

## merge new main into feature2
- since feature2 was written, main has changed (feature1 has been included). lets merge main back to feature2 branch
``` bash
git tag pre-merge1; # tag the commit so we can reset easily
git checkout feature2;
git merge main;
```
