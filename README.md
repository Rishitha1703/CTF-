This challenge involves recovering a deleted flag using Git version control. The process follows these steps:

1. **Download and Extract the Challenge Files**  
   - Use `wget` to download `challenge.zip`.  
   - Extract it using `unzip challenge.zip`.  

2. **Locate the Hidden Git Repository**  
   - Navigate into the extracted directory (`cd drop-in/`).  
   - Use `ls -a` to reveal hidden files, including the `.git` directory.  

3. **Investigate the Git History**  
   - The only visible file is `message.txt`, which currently contains "TOP SECRET."  
   - Use `git log` to check previous commits. One commit is labeled **"create flag"**, with an ID of `3d5ec8a26ee7b092a1760fea18f384c35e435139`.  

4. **Retrieve the Deleted Flag**  
   - Use `git checkout 3d5ec8a26ee7b092a1760fea18f384c35e435139` to switch to that commit.  
   - Running `cat message.txt` now reveals the previously deleted flag:  
     ```
     picoCTF{s@n1t1z3_30e86...}
     ```

### **Key Takeaways**
- Git retains history even if a file is deleted, allowing recovery of lost data.
- Using `git log` helps track commit messages and IDs.
- `git checkout <commit-id>` enables restoring previous file states.

This challenge reinforces the importance of understanding Git’s history and how it can be used to retrieve lost information.
