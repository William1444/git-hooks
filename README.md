# pre commit hook: aws secrets
pre receive hook to check staged files for regex that match AWS SECRET ACCESS KEY and AWS_ACCESS_KEY_ID.

## usage

The recommended approach for sharing git hooks is to create a git hooks directory in the project:

```bash
mkdir .githooks
```

Drop the pre-commit hook file in this directory.

Configure the local repo to use the git hooks directory:

```bash
git config core.hooksPath .githooks
```

To configure this for all team members for a project, it is a good idea to add this to your build scripts.

For example, in `Nodejs` you can add a post-install step to your `package.json`:

```json
{
  "scripts": {
    "post-install": "git config core.hooksPath .githooks"
  }
}
```

## ignoring files

Files to ignore can be added in .secretignore in the root of the project. You will need to ensure they match 
exactly as they appear in the output of this command: 

```bash
git diff --cached --name-status --diff-filter=d | awk -F' ' '{print $2}'
```

This can be made more smart in the future!

## tbc

Expand to check for rsa keys etc
