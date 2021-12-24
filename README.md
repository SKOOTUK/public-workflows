# public-workflows

public repo for defining reusable github actions and workflows.


## Python Linters

If you want to use the python linters workflow you can setup a github workflow (`.github/workflows/linting.yml`) in your repository root similarly to the following:

```
name: Lint
on:
  pull_request:
    branches:
      - main

jobs:
  call-linters:
    uses: SKOOTUK/public-workflows/.github/workflows/python_linters.yml@main
```

## Tree Planter

If you want to use the Tree Planter workflow you need to:
  1. Setup your account at https://eco.skoot.io/getting-started/ and get your key
  2. Setup your repository with the following secrets:
    * ECO_KEY: the key you've been assigned in the eco portal
    * QUANTITY: the quantity of trees to plant on each github event
  3. Setup the workflow in your repository similarly to the following:
  ```
  name: Plant Trees
  on:
    pull_request:
      branches:
        - main

  jobs:
    call-gardener:
      uses: SKOOTUK/public-workflows/.github/workflows/plant_trees.yml@main
      secrets:
        key: ${{ secrets.ECO_KEY }}
        quantity: ${{ secrets.QUANTITY }}
  ```
Done, you're ready to plant trees on PR merges (in this example)!

:warning: Warning :warning: - Be aware of the possibility of extra costs (beside the tree costs) when using actions. Look at [github official documentation](https://docs.github.com/en/billing/managing-billing-for-github-actions/about-billing-for-github-actions) for reference.