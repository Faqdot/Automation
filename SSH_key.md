# Set Up SSH Key Authentication for GitHub on Linux

This guide explains how to configure SSH key authentication on a Linux
system so you can connect to GitHub without entering your GitHub
username and password for every Git operation.

## 1. Check for an existing SSH key

Open a terminal and run:

``` bash
ls -la ~/.ssh
```

Look for an existing Ed25519 key pair:

-   `id_ed25519` --- private key
-   `id_ed25519.pub` --- public key

If you already have a key you want to use, you can skip to **Step 3**.
Do not overwrite an existing key unless you are sure you no longer need
it.

## 2. Generate a new SSH key

Use the email address associated with your GitHub account:

``` bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

When asked where to save the key, press **Enter** to use the default
path:

``` text
/home/your-user/.ssh/id_ed25519
```

Choose a strong passphrase when prompted. A passphrase helps protect
your private key if someone obtains the file.

## 3. Start the SSH agent and add your key

Start the agent:

``` bash
eval "$(ssh-agent -s)"
```

Add the private key to the agent:

``` bash
ssh-add ~/.ssh/id_ed25519
```

If you used a different filename, replace `id_ed25519` with that
filename.

## 4. Add the public key to GitHub

Display your public key:

``` bash
cat ~/.ssh/id_ed25519.pub
```

Copy the entire output. It should begin with `ssh-ed25519`.

Then:

1.  Sign in to GitHub.
2.  Open [GitHub SSH and GPG keys](https://github.com/settings/keys).
3.  Select **New SSH key**.
4.  Enter a descriptive title, such as `Linux laptop`.
5.  Set the key type to **Authentication Key**.
6.  Paste the public key and select **Add SSH key**.

**Security note:** Share only the `.pub` public key. Never upload or
share the private key file (`~/.ssh/id_ed25519`).

## 5. Test the SSH connection

Run:

``` bash
ssh -T git@github.com
```

The first connection may ask you to confirm GitHub's host fingerprint.
Verify it against GitHub's published SSH key fingerprints before
accepting.

A successful authentication message looks similar to:

``` text
Hi YOUR-GITHUB-USERNAME! You've successfully authenticated, but GitHub does not provide shell access.
```

This message means SSH authentication works. It does not provide an
interactive shell.

## 6. Change an existing Git remote from HTTPS to SSH

From inside your local repository, inspect the current remote:

``` bash
git remote -v
```

For the repository `Faqdot/Automation`, set the SSH URL:

``` bash
git remote set-url origin git@github.com:Faqdot/Automation.git
```

Verify the change:

``` bash
git remote -v
```

Expected format:

``` text
origin  git@github.com:Faqdot/Automation.git (fetch)
origin  git@github.com:Faqdot/Automation.git (push)
```

## 7. Fetch, pull, and push

Fetch remote references:

``` bash
git fetch origin
```

List local and remote-tracking branches:

``` bash
git branch -a
```

Push the current branch and set its upstream:

``` bash
git push -u origin HEAD
```

For future updates, use:

``` bash
git pull
git push
```

If the GitHub repository is empty, create and commit at least one file
before the first push. For example:

``` bash
echo "# Automation" > README.md
git add README.md
git commit -m "Initial commit"
git push -u origin HEAD
```

## Troubleshooting

### `Permission denied (publickey)`

Check that:

-   The public key was added to the correct GitHub account.
-   The SSH agent is running and the key is loaded (`ssh-add -l`).
-   Your Git remote uses the SSH URL (`git remote -v`).
-   You are connecting as `git`, for example `git@github.com`.

To load the key again:

``` bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

### No remote branches appear

Check whether the GitHub repository has branches:

``` bash
git ls-remote --heads origin
```

If this prints no branch references, the remote repository may be empty
or may not have any branches yet. Confirm the repository contents and
permissions on GitHub.

### Check the SSH remote URL

``` bash
git remote get-url origin
```

For this example repository, it should be:

``` text
git@github.com:Faqdot/Automation.git
```

## Useful references

-   [GitHub: Connecting to GitHub with
    SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
-   [GitHub: Adding a new SSH key to your GitHub
    account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
-   [GitHub: Testing your SSH
    connection](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection)
