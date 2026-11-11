# DJS91 Action Demo

This repository is a demo of a custom GitHub Action. The action greets a user
and generates a pseudo-random number to show how a composite action can accept
an input and return an output.

## Use the action

Use the published action in a workflow:

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

## Marketplace

This demo action is published to GitHub Marketplace as
[Random Number Generator Demo](https://github.com/marketplace/actions/random-number-generator-demo).
Version `v1.0.0` is the initial release.
