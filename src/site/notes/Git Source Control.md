---
{"dg-publish":true,"permalink":"/git-source-control/"}
---

Related: #programming 
Contents: [[CGRA251 MOC\|CGRA251 MOC]]
[CGRA Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CGRA251_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# Git

- Tracks *changes* made to file
- Changes get tracked and staged
- Can add multiple *remotes*
- Can use a **cron** to setup automatic actions

## .gitignore

- Files in here won't get tracked

## .gitattributes

- Contains files that you want to upload to [[Git Source Control#Git LFS\|Git LFS]]
- Treats these files as a *symbolic link*

```
*.FBX filter=lfs diff=lfs merge=lfs -text
*.OBJ filter=lfs diff=lfs merge=lfs -text
*.WAV filter=lfs diff=lfs marge=lfs -text
```

## Git LFS

- When you pull, everything listed in gitatttributes gets **streamed** in
- Accesses them asynchronously 
- So when pulling, you'll get all your text files straight away, but maybe not everything that's loaded in Git LFS
