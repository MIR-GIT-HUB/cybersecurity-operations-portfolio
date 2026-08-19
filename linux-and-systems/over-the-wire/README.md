#### 🔹 Level 0 ➡️ Level 1: Initial Server Access and Resource Ingestion
*   **The Goal:** Connect to the remote game server and extract the hidden Level 1 password from a file located in the home directory.
*   **My Initial Mistake:** 
    *   I ran `cat pass` assuming the password file would simply be named `pass`. This threw a `No such file or directory` error because I jumped straight to guessing rather than auditing the filesystem first.
    *   I also tried running `grep pass` blindly, which trapped my terminal in an open input stream loop because `grep` requires a specified target string or file pattern to look through. I had to manually cancel it out using `Ctrl+C`.
*   **How I Solved It:**
    1.  I ran `pwd` to verify my current location, confirming I was in the `/home/bandit0` folder.
    2.  I ran the `find` command to display all elements in the folder. This revealed a file named `./readme`.
    3.  I successfully bypassed terminal path ambiguities by target-reading the specific relative path of the file: `cat ./readme`. 
*   **Key Defensive Command Takeaway:** Never guess filenames on an infected or unknown host. Always audit the environment using structural reconnaissance tools like `find` and `pwd` first.
