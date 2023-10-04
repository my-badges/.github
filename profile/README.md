## My Badges

Here is how to add my badges to your profile:
- Star [my-badges](https://github.com/my-badges/my-badges) repository.
- Create `your-username/your-username` repository.
- In `README.md` add the following code:
```html
<!-- my-badges start -->
<!-- my-badges end -->
```
- Add the following workflow [`.github/workflows/my-badges.yml`](.github/workflows/my-badges.yml)
  to your repository.
```yaml
name: my-badges

on:
  workflow_dispatch:
  schedule:
    - cron: '0 0 * * *'

permissions:
  contents: write

jobs:
  my-badges:
    runs-on: ubuntu-latest
    steps:
      - name: Update My Badges
        run: npx update-my-badges {{github.repository_owner}} --repo=${{ github.repository }}
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
- Start `my-badges` workflow, or wait for it to run automatically.
