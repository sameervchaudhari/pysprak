# pysprak
# Create SSH Password less connectivity between 2 mac computers
    # Check for Existing SSH Key Pair:   ls -al ~/.ssh  This lists the contents of the hidden .ssh directory in your home directory, where SSH keys are typically         stored
    # ls -al ~/.ssh/id_*.pub
        Lists files in the .ssh directory: It displays a list of files located in the .ssh directory, which is often used to store SSH keys.
        Includes hidden files: The -a option ensures that any hidden files (starting with a dot) are also included in the listing.
        Provides detailed information: The -l option presents a long listing format, showing file permissions, ownership, size, modification dates, and names.
        Specifically targets public keys: The pattern "id_*.pub" filters the results to show only files that match the naming convention for SSH public keys.
      # id_rsa (private key)
        id_rsa.pub (public key)
        id_dsa (alternative private key)
        id_dsa.pub (alternative public key)
        id_ecdsa (ECDSA private key)
        id_ecdsa.pub (ECDSA public key)

      # View Key Contents (Optional):cat ~/.ssh/id_rsa.pub

    # 1. Generate SSH Key Pair on the Master Laptop:
        #ssh-keygen -t rsa -b 4096 -C "your_email@domain.com"
        At this point, you can either press Enter to accept the default file location and file name (/Users/sameerchaudhari/.ssh/id_rsa), or you can enter a new           path and filename if you wish to save the key with a different name or in a different location.
        sameerchaudhari@Sameers-MBP ~ % ls -al ~/.ssh         
        total 32
        drwx------   6 sameerchaudhari  staff   192 Dec 28 11:45 .
        drwxr-x---+ 32 sameerchaudhari  staff  1024 Dec 28 11:34 ..
        -rw-------   1 sameerchaudhari  staff  3434 Dec 28 11:45 id_rsa
        -rw-r--r--   1 sameerchaudhari  staff   752 Dec 28 11:45 id_rsa.pub
        -rw-------   1 sameerchaudhari  staff   834 Dec 26 19:16 known_hosts
        -rw-r--r--   1 sameerchaudhari  staff    94 Dec 26 19:16 known_hosts.old

   #  2 Copy the Public Key: Copy the Public Key to the Slave Laptop:
       # ssh-copy-id username@slave-laptop-ip
         Use the ssh-copy-id command to transfer the public key to the slave laptop:
       # Key Location on Slave:

        The public key is copied into a file named authorized_keys within the .ssh directory in the slave computer's home directory.
        The full path to this file is typically ~/.ssh/authorized_keys
        To close an SSH connection in a terminal session, you can simply type exit and press Enter. Th

   #  3 Delete the Existing SSH Keys
       #  rm ~/.ssh/id_rsa
          rm ~/.ssh/id_rsa.pub


# Here are the detailed steps to run a Python big data application using PySpark on two Mac laptops as a cluster:
    # Install Java: PySpark requires Java. Install it on both laptops if it's not already installed.
                    Ensure both Macs have Java 8 or later installed
       brew install java

       /usr/local/opt/openjdk: This is the primary installation directory for OpenJDK when installed using Homebrew. It contains the essential files and executables        for running Java.
       Reference /usr/local/opt/openjdk for the active installation.
       sudo ln -sfn /usr/local/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk

       # OR
       sudo ln -sfn /opt/homebrew/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk
      
       this link documentation is part of brew installation.





       Benefits of Using Symlinks:

        Non-Destructive: They don't modify the original files, ensuring a safe and organized approach.
        System-Wide Visibility: Applications and tools that rely on the standard JDK path will now recognize OpenJDK.
        No Conflicts: It avoids potential conflicts with other Java versions or configurations.

       After running the command, verify by:

        Checking Symlink: Use ls -l /Library/Java/JavaVirtualMachines/openjdk.jdk to confirm the symlink's existence.
        Checking Java Version: Run java -version to see if the system correctly recognizes OpenJDK.
     # Install Pyspark
         # Create virtual env using poetry
           poetry init
           poetry shell
                   sameerchaudhari@Sameers-MBP dev % poetry shell
                    The currently activated Python version 3.12.1 is not supported by the project (3.9.6).
                    Trying to find and use a compatible version. 
                    Using python3 (3.9.6)
                    Creating virtualenv pyspark-bigdata-PP00zFBB-py3.9 in /Users/sameerchaudhari/Library/Caches/pypoetry/virtualenvs
                    Spawning shell within /Users/sameerchaudhari/Library/Caches/pypoetry/virtualenvs/pyspark-bigdata-PP00zFBB-py3.9
                    sameerchaudhari@Sameers-MBP dev % emulate bash -c '. /Users/sameerchaudhari/Library/Caches/pypoetry/virtualen
                    vs/pyspark-bigdata-PP00zFBB-py3.9/bin/activate'
            poetry install --no-root  : We are not trying to create package here
     # Install brew
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
   # Set Path for brew
   echo $SHELL
   vim ~/.zshrc
   export PATH="/opt/homebrew/bin:$PATH"









    #  Install Spark and PySpark: Download and install Spark on both machines. Ensure PySpark is installed using 
       pip install pyspark.









         
   


