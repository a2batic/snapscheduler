# Upgrading the operator-sdk version

Generate the scaffolding like it is a new project:

```
$ mkdir ~/temp
$ cd temp/
$ operator-sdk new SnapScheduler --repo github.com/backube/SnapScheduler
INFO[0000] Creating new Go operator 'SnapScheduler'.
...
INFO[0003] Project creation complete.
$ cd SnapScheduler/
$ operator-sdk add api --api-version snapscheduler.backube/v1alpha1 --kind SnapshotSchedule
INFO[0000] Generating api version snapscheduler.backube/v1alpha1 for kind SnapshotSchedule.
...
INFO[0016] API generation complete.
$ operator-sdk add controller --api-version snapscheduler.backube/v1alpha1 --kind SnapshotSchedule
INFO[0000] Generating controller version snapscheduler.backube/v1alpha1 for kind SnapshotSchedule.
...
INFO[0000] Controller generation complete.
```

In the existing repo, switch to the `sdk-scaffolding` branch:

```
$ cd <existing-repo>
$ git checkout sdk-scaffolding
Switched to branch 'sdk-scaffolding'
```

Replace the files w/ the newly generated ones:

```
$ rm -rf *
$ cp -a ~/temp/SnapScheduler/* .
$
```

Commit the result:

```
$ git add .
$ git commit -m 'Upgrade to operator-sdk v0.10.0'
[sdk-scaffolding 0192b10] Upgrade to operator-sdk v0.10.0
 5 files changed, 24 insertions(+), 20 deletions(-)
```

Merge this branch into `master` via merge commit or PR.