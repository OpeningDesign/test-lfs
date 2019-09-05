# Git-LFS test

This repo is here to test LFS support

### Procedure

1. Install Git-LFS on your computer
2. Warning, this works only fully for a new repo. You can go further on an 
   existing repo, but only revisions after this point will be handled by LFS. 
   That is, all revisions committed before now will stay as they are. There is a 
   way to migrate all previous commits to LFS, but it will rewrite all your 
   history, which one should not do (will un-sync will all other copies of the  
   repo)
3. Inside the repo: `git lfs install`
4. Inside the repo: `git lfs track "*.rvt"
5. Check that a `.gitattributes` is created
6. Commit some files
7. Push

Normally that's all. After that everything should "just work" as normal...

### Running the test

1. I committed one .rvt file of 1.8Mb. The total repo size is around 3.5Mb, 
   that is, 1.8 for the .rvt file itself, and about 1.8 inside the .git repo, 
   which is where the actual git-handled file revision is stored
2. I'll try to make a change to the file. Under normal git, the new revision
   should also weight around 1.8Mb, so the .git folder should double its
   size and now weight 3.6Mb.
3. Unfortunately after committing the change, thw content of the git folder
   still weights 3.7Mb. Although .rvt files are well managed by git lfs, as
   shown by `git lfs ls-files` and alsoinside the .git folder, the two
   revisions are indeed inside a lfs folder.
4. Trying to push and let others make changes to see what happens...

### Resources

* https://dzone.com/articles/git-lfs-why-and-how-to-use
* https://docs.gitlab.com/ee/workflow/lfs/manage_large_binaries_with_git_lfs.html