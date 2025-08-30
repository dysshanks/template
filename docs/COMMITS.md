
## updated logger
- **Commit:** `3f2b9e291a5841f85323464fce2e2e9e50489216`
- **Date:** 2025-08-30 17:11:29 +0200
- **Author:** dysshanks

### Preview (first 3 lines of changes)
```diff
commit 3f2b9e291a5841f85323464fce2e2e9e50489216
Author: dysshanks <ryanvdvorst@outlook.com>
Date:   Sat Aug 30 17:11:29 2025 +0200
```

<details><summary>Full changes</summary>

```diff
commit 3f2b9e291a5841f85323464fce2e2e9e50489216
Author: dysshanks <ryanvdvorst@outlook.com>
Date:   Sat Aug 30 17:11:29 2025 +0200

    updated logger
    
    hopefully made the permissions work and it should not loop on itself

diff --git a/.github/workflows/commit-log.yml b/.github/workflows/commit-log.yml
index 08479d6..ab27135 100644
--- a/.github/workflows/commit-log.yml
+++ b/.github/workflows/commit-log.yml
@@ -5,8 +5,12 @@ on:
     branches:
       - main
 
+permissions:
+  contents: write
+
 jobs:
   log-commits:
+    if: github.actor != 'github-actions[bot]'
     runs-on: ubuntu-latest
 
     steps:
@@ -14,6 +18,7 @@ jobs:
         uses: actions/checkout@v3
         with:
           fetch-depth: 0
+          token: ${{ secrets.GITHUB_TOKEN }}
 
       - name: Gather commit info
         run: |
```

</details>

