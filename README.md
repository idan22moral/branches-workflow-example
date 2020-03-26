# Branches Workflow Example

This repository is an example for Magshimim 2nd year students on how to work with git branches.  
This workflow is publicly known as _Gitflow Workflow_.

To learn more about the Gitflow Workflow, I highly recommend reading [this article](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow).

## Detailed Example

```console
$ # cloning the repository
$ git clone git@github.com:idan22moral/branches-workflow-example.git
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 6 (delta 0), reused 6 (delta 0), pack-reused 0
Receiving objects: 100% (6/6), done.
$ cd branches-workflow-example

$ # work on a development branch!
$ git checkout -b develop
Switched to a new branch 'develop'

$ # checkout to a new branch for features that you work on.
$ # we do that to make the develop branch clean from work-in-progress stuff,
$ # and to make integration with your team's code cleaner and easier.
$ git checkout -b feature/feature_1
Switched to a new branch 'feature/feature_1'
$ echo "feature_1 content" > feature_1
$ git add feature_1
$ git commit -m "added feature_1 files"
[feature/feature_1 fc2ae6b] added feature_1 files
 Date: Thu Mar 26 19:51:10 2020 +0000
 1 file changed, 1 insertion(+)
 create mode 100644 feature_1

$ # we can see that the feature branch is derived from the develop branch
$ git log
commit fc2ae6bf5fbbdbb6f0a1bcaaa93213a99b2743bf (HEAD -> feature/feature_1)
Author: Idan Moral <idan22moral@gmail.com>
Date:   Thu Mar 26 19:51:10 2020 +0000

    added feature_1 files

commit fd284e2ccccd07fa3aa065a9fff9547e003ad467 (main, develop)
Author: Idan Moral <idan22moral@gmail.com>
Date:   Thu Mar 26 19:49:39 2020 +0000

    Initial commit

$ # finished working on the feature.
$ # let's merge the feature back into the develop branch!
$ git checkout develop
Switched to branch 'develop'
$ git merge feature/feature_1
Updating fd284e2..fc2ae6b
Fast-forward
 feature_1 | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 feature_1

$ # new we can see that both the feature and develop branches are pointing to the same commit (which is now the HEAD of the develop branch)
$ git log
commit fc2ae6bf5fbbdbb6f0a1bcaaa93213a99b2743bf (HEAD -> develop, feature/feature_1)
Author: Idan Moral <idan22moral@gmail.com>
Date:   Thu Mar 26 19:51:10 2020 +0000

    added feature_1 files

commit fd284e2ccccd07fa3aa065a9fff9547e003ad467 (main)
Author: Idan Moral <idan22moral@gmail.com>
Date:   Thu Mar 26 19:49:39 2020 +0000

    Initial commit

$ # when we're confident with the current state of the develop branch
$ # and we think that the code is production-ready, we can merge develop into main/master.
$ # I'll skip that part for this example.
```