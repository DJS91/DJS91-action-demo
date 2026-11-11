# DJS91 Action Demo

This repository is a demo of a custom GitHub Action. The action greets a user
and generates a pseudo-random number to show how a composite action can accept
an input and return an output.

## Use the action

After this action has been published and tagged, use it in a workflow:

```yaml
steps:
  - name: Generate a random number
    id: random
    uses: DJS91/DJS91-action-demo@v1
    with:
      user-name: Developer

  - name: Show the number
    env:
      GENERATED_NUMBER: ${{ steps.random.outputs.generated-number }}
    run: echo "Generated number: $GENERATED_NUMBER"
```

`user-name` is optional and defaults to `Developer`. The action exposes the
generated value as `generated-number`. The number is for demonstration only;
it is not cryptographically secure and should not be used for security-sensitive
purposes.

## Test the action

The workflow in `.github/workflows/test-random-generator-action.yml` runs the
action and checks that its output contains only digits. It runs on pushes,
pull requests, and manual dispatch.

## Marketplace status

This repository is a demo project. The action is not published to GitHub
Marketplace until the repository is public and the action is submitted through
GitHub's Marketplace publishing flow.
