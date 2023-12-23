# git-config

GitHub action to configure the git user corresponding to the `GITHUB_TOKEN` environment variable.

The action configures the git user name and email:

```
git config --global user.name <name>
git config --global user.email <email>
```

## Usage

Here's an example of how to use the action in a workflow to configure the git user.
After you configure the user, you can make changes and push them.

```yaml
jobs:
  my-job:
    name: My job
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4
      - name: Git config
        uses: MarcoIeni/git-config@v0.1
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      - name: Commit changes
        run: |
          echo "${{ steps.commit-author.outputs.email }}"
          echo "${{ steps.commit-author.outputs.name }}"
          touch new-file
          git add .
          git commit -m "My commit message"
          git push
```

<br>

<sup>
Licensed under either of <a href="LICENSE-APACHE">Apache License, Version 2.0</a>
or <a href="LICENSE-MIT">MIT license</a> at your option.
</sup>

<br>

<sub>
Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.
</sub>
