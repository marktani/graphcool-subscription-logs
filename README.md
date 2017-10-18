# graphcool-subscription-logs

## Current Behaviour

Logs for subscription functions that return something else than an object containing the `data` or `error` key are not created.

## Reproduction

Deploy:

```sh
graphcool deploy
graphcool playground
```

Stream Logs:

```sh
graphcool logs -f logs --tail
graphcool logs -f no-logs --tail
```

Create a user:

```graphql
mutation {
  createUser(dateOfBirth: "2017" name: "Nilan") {
    id
  }
}
```

Observe that logs for function `logs` are created, but not for function `no-logs`.

## Expected behaviour

Logs for function `no-logs` should be created, too.
