# MLE-US-Flights
To add Git credentials to the terminal in SageMaker Studio Classic, you need to configure Git to use your GitHub credentials. Here are the steps to achieve this:

### Step 1: Generate a Personal Access Token on GitHub

1. **Log in to GitHub**.
2. **Go to Settings**: Click on your profile icon in the upper-right corner and select "Settings".
3. **Developer settings**: In the left sidebar, click on "Developer settings".
4. **Personal access tokens**: Click on "Personal access tokens" and then on "Generate new token".
5. **Select Scopes**: Give your token a descriptive name and select the scopes or permissions you need (e.g., `repo` for full control of private repositories).
6. **Generate token**: Click on "Generate token" at the bottom of the page.
7. **Copy the token**: Make sure to copy the token now as you won’t be able to see it again.

### Step 2: Configure Git in SageMaker Studio Classic

1. **Open SageMaker Studio Classic**:
   - Navigate to the AWS Management Console.
   - Open the SageMaker service and launch SageMaker Studio Classic.

2. **Open a Terminal**:
   - In SageMaker Studio, click on the "File" menu and select "New" > "Terminal".

3. **Configure Git with Your Credentials**:

   **Method 1: Using Git Credential Helper**
   - Configure Git to use the credential helper:
     ```bash
     git config --global credential.helper store
     ```
   - When you clone a repository for the first time or perform any Git operation that requires authentication, Git will prompt you to enter your GitHub username and personal access token. Git will then store these credentials for future use.
   
   **Method 2: Manually Storing Credentials**
   - Create or edit the `~/.git-credentials` file:
     ```bash
     nano ~/.git-credentials
     ```
   - Add the following line to the file, replacing `YOUR_USERNAME` and `YOUR_ACCESS_TOKEN` with your GitHub username and personal access token:
     ```
     https://YOUR_USERNAME:YOUR_ACCESS_TOKEN@github.com
     ```
   - Save and close the file (`Ctrl + O`, `Enter`, `Ctrl + X`).
   - Configure Git to use this credentials file:
     ```bash
     git config --global credential.helper 'store --file ~/.git-credentials'
     ```

### Step 3: Clone the Repository and Use Git

1. **Clone your GitHub repository**:
   ```bash
   git clone https://github.com/YOUR_USERNAME/REPOSITORY_NAME.git
   ```

2. **Navigate to the cloned repository**:
   ```bash
   cd REPOSITORY_NAME
   ```

3. **Perform Git operations**:
   - You can now perform Git operations like `git pull`, `git push`, `git commit`, etc., without being prompted for your credentials each time.

### Optional: Verify Git Configuration

1. **Check Git configuration**:
   ```bash
   git config --global --list
   ```
   - This command will list your Git configuration settings, including the credential helper configuration.

By following these steps, you will have successfully added your GitHub credentials to the terminal in SageMaker Studio Classic, enabling seamless Git operations.
