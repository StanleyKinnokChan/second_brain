
1. **Make Changes and Commit:**
First, you make your changes to your codebase, whether it's fixing bugs, adding features, or making other improvements. After making these changes, you commit them to your local Git repository using the following commands:
    
    ```
    git add .
    git commit -m "Description of changes"
    ```
    
    
2. **Create a Tag:**
After you've made and committed your changes and you're ready to create a new version or release, you can create a Git tag. The tag is created based on the specific commit that represents the state of your code at the time of the release. Here's how you can create a tag:
    
    ```
    // Replace **`v2.0`** with the version or tag name you want to use.
    git tag v2.0
    ```
    
3. **Push Changes and Tags to Remote:**
To make your commit and tag available on your remote repository (e.g., GitHub), you need to push them:
    
    ```
    git push origin main  # Push your commits
    git push origin v2.0  # Push your new tag
    ```
    
    The above example assumes you are pushing to the **`main`** branch. Adjust it accordingly if you are using a different branch.

# Add tag to old version

1. **Identify the Commit:**
Use the **`git log`** command to find the commit hash associated with the older version. Let's say the commit hash is **`abcdef123456`**.

2. **Create a Tag for the Old Version:**
Create a Git tag for the old version:
    
    ```
    git tag v1.0 abcdef123456
    ```
    
    Replace **`v1.0`** with your desired tag name and **`abcdef123456`** with the actual commit hash.
    
3. **Push the Tag to the Remote Repository:**
Finally, push the tag to your remote repository on GitHub:
    
    ```
    git push origin v1.0
    
    ```
    
    This will officially mark the old version as a release, and users can access it in the "Releases" section of your GitHub repository.


**git describe**
git describe can help to see the latest anchor point (tag)