# WebGL Portfolio — Model Assets

## Adding new GLB files (Git LFS)

We store large `.glb` assets using Git LFS to avoid bloating the repository and to ensure large binary uploads are managed correctly.

Steps to add a new `.glb` file (example: `Climbing.glb`):

1. Install Git LFS (if you haven't already):

```bash
brew install git-lfs
git lfs install
```

2. Ensure `.glb` is tracked by LFS in this repo (the repo already uses `*.glb` in `.gitattributes`):

```bash
cat .gitattributes
# you should see a line like: *.glb filter=lfs diff=lfs merge=lfs -text
```

If you prefer to track a single file instead of the pattern, run:

```bash
git lfs track "Climbing.glb"
git add .gitattributes
git commit -m "Track Climbing.glb with Git LFS"
```

3. Add, commit, and push the file (push will upload the LFS object):

```bash
git add Climbing.glb
git commit -m "Add Climbing.glb (via Git LFS)"
git push origin <branch>
```

Notes:
- Pushing will upload the LFS object to the remote; this can take time depending on file size and network.
- GitHub has LFS storage and bandwidth quotas — confirm your account/org limits if you expect many large files.
- If a large file was mistakenly committed to history (not via LFS), use `git lfs migrate import --include="*.glb" --everything` or BFG to rewrite history (coordinate with collaborators because this requires force-push).

```
