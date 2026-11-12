# GitHub SSH Key Authentication on Linux

This guide documents how to configure SSH authentication between a Linux
computer and GitHub, use an SSH remote URL, and push a local Git
repository.

The example repository used here is `Faqdot/Automation`, and the local
branch is `Master`.

## 1. Check for existing SSH keys

List the SSH directory:

``` bash
ls -la ~/.ssh/
```

The example system already had these files:

-   `id_ed25519` and `id_ed25519.pub` --- an Ed25519 private/public key
    pair
-   `github` --- an additional private key file
-   `config` --- SSH client configuration
-   `known_hosts` --- previously trusted SSH hosts

Use the key that your SSH configuration is set up to use. Do not
generate a new key if you already have a working one.

## 2. Display and register the public key

For the default Ed25519 key, display the public key:

``` bash
cat ~/.ssh/id_ed25519.pub
```

If your SSH configuration uses the key named `github`, display its
matching public key instead (if present):

``` bash
cat ~/.ssh/github.pub
```

Copy the complete public-key line. In GitHub:

1.  Open [GitHub SSH and GPG keys](https://github.com/settings/keys).
2.  Select **New SSH key**.
3.  Give it a recognizable title, such as `Linux laptop`.
4.  Choose **Authentication Key**.
5.  Paste the public key and save it.

**Security:** Only add or share the public key (`.pub`). Never share
your private key, such as `~/.ssh/id_ed25519` or `~/.ssh/github`.

## 3. Start the SSH agent and load the key

Start the agent:

``` bash
eval "$(ssh-agent -s)"
```

Load the key you intend to use. For example:

``` bash
ssh-add ~/.ssh/id_ed25519
```

If your SSH configuration uses `~/.ssh/github`, load that key instead:

``` bash
ssh-add ~/.ssh/github
```

Enter the key's passphrase when prompted. This is the passphrase
protecting your local private key; it is not your GitHub account
password.

## 4. Test SSH authentication

Run:

``` bash
ssh -T git@github.com
```

On first connection, SSH may ask you to verify GitHub's host
fingerprint. Check it against GitHub's published fingerprints before
accepting.

A successful authentication response looks similar to:

``` text
Hi YOUR-GITHUB-USERNAME! You've successfully authenticated, but GitHub does not provide shell access.
```

## 5. Configure the repository to use SSH

Go to your local repository:

``` bash
cd ~/Automation
```

Set the SSH remote URL:

``` bash
git remote set-url origin git@github.com:Faqdot/Automation.git
```

Verify it:

``` bash
git remote -v
```

Expected format:

``` text
origin  git@github.com:Faqdot/Automation.git (fetch)
origin  git@github.com:Faqdot/Automation.git (push)
```

If the URL starts with `https://`, the repository is still using HTTPS.
Change it with the command above.

## 6. Fetch and inspect remote branches

``` bash
git fetch origin
git branch -a
```

To check the branch references directly on GitHub:

``` bash
git ls-remote --heads origin
```

If the remote repository has no branches yet, the command may return no
output until the first push creates one.

## 7. Commit and push your work

Check the current branch and working-tree status:

``` bash
git status
git branch
```

Stage and commit files as needed:

``` bash
git add README.md SSH_key.md
git commit -m "Document GitHub SSH authentication"
```

Push the current branch and set its upstream:

``` bash
git push -u origin HEAD
```

For the example `Master` branch, this is equivalent to:

``` bash
git push -u origin Master
```

A successful first push can show output similar to:

``` text
To github.com:Faqdot/Automation.git
 * [new branch]      Master -> Master
branch 'Master' set up to track 'origin/Master'.
```

After the upstream is configured, future updates can usually be pushed
with:

``` bash
git push
```

## 8. Troubleshooting

### Git asks for a key passphrase

A prompt such as:

``` text
Enter passphrase for key '/home/your-user/.ssh/github':
```

means SSH is using an encrypted private key. Enter the passphrase you
created for that key. This is normal and does not mean Git is asking for
your GitHub username or password.

To avoid entering it repeatedly during an agent session, start
`ssh-agent` and add the key:

``` bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/github
```

Use the actual private-key filename configured on your system.

### `Permission denied (publickey)`

Check that:

-   The matching public key is added to the correct GitHub account.
-   SSH is using the matching private key.
-   The key is loaded in the agent (`ssh-add -l`).
-   The remote URL uses SSH (`git remote -v`).

For detailed connection diagnostics:

``` bash
ssh -vT git@github.com
```

Do not share diagnostic output without checking it for private paths or
other sensitive details.

### The upstream branch is gone

If Git reports that the upstream branch is gone, inspect the remote
branches:

``` bash
git fetch origin
git branch -r
```

If the remote branch exists and has the same name as your local branch,
set the upstream:

``` bash
git branch --set-upstream-to=origin/Master Master
```

If the remote branch does not exist yet, push the local branch:

``` bash
git push -u origin Master
```

## Useful GitHub documentation

-   [Connecting to GitHub with
    SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
-   [Adding a new SSH key to your GitHub
    account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
-   [Testing your SSH
    connection](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection)
