# Rebase TIL

## delete branches
``` bash
gco main;
git branch -D feature1 feature2;
```




## 1. tag initial commit for easier reset later
``` bash
git tag -d initial;
git checkout main
git tag initial;
```

## 2. code feature 1
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
## 3. code feature 2
``` bash
git checkout main;
git checkout -b feature2;
touch feature2-1;
git add .; 
git commit -am "feature2-1";
touch feature2-2;
git add .; 
git commit -am "feature2-2";
```

## 4. fast forward merge feature1
- fast forward main to the head of branch feature1, since main is just an ancestor of feature1. 
``` bash
git checkout main;
git merge feature1;
```

## 5. merge new main into feature2
- since feature2 was written, main has changed (feature1 has been included). lets merge main back to feature2 branch
``` bash
git checkout feature2;
git tag pre-merge1; # tag the commit so we can reset easily
git merge main;
```

## 6. reset feature2
``` bash
git reset --hard pre-merge1;
```

## 7. rebase new main into feature2
- since feature2 was written, main has changed (feature1 has been included). lets rebase main back to feature2 branch to keep the history linear
``` bash
git rebase main;
```

## 8. merge it to main (fast forward)
``` bash
git checkout main;
git merge feature2;
```


---


# ONTO, changing the parent branch


## 1. code feature 3
``` bash
git checkout main;
git checkout -b feature3;
touch feature3-1;
git add .; 
git commit -am "feature3-1";
touch feature3-2;
git add .; 
git commit -am "feature3-2";
```

## 2. code feature 4
- we code feature 4 from feature 3
``` bash
git checkout -b feature4;
touch feature4-1;
git add .; 
git commit -am "feature4-1";
touch feature4-2;
git add .; 
git commit -am "feature4-2";
```

## 3. rebase onto main
- Now we want to change the parent branch of feature4. i.e. we want to pretend we started feature4 from main, rather than feature 3. see the rebase --help diagram for onto
``` bash
git rebase --onto main feature3 feature4;
```


# Interactive (do mad stuff)
## lets rebase and squash some stuff
## 1. rebase feature3 to get all the stuff again
``` bash
git checkout feature4;
git rebase feature3;

git rebase -i main;
```

# ...Profit