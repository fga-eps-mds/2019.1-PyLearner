## Version control

|Date|Version|Update|Author|
|:--:|:----:|:-------:|:---:|
|17/03/2019|0.1|Git branching policies|Gabriel Ziegler|

# Branches policy

* Branches in English.

* Branches have a *TAG* that references the issue that this branch will resolve.

* Practical example:

A branch for the issue "#4 use significant variables names" should look like:

```git
git checkout -b 4-use-significant-variables-names
```

* If the issue title is way too big, use only the first significant words to create it, do not create text-sized branches. 

