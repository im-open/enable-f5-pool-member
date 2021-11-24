# enable-f5-pool-member

An action that will enable an F5 pool member in a specific pool.

## Index

- [Inputs](#inputs)
- [Outputs](#outputs)
- [Example](#example)
- [Contributing](#contributing)
  + [Incrementing the Version](#incrementing-the-version)
- [Code of Conduct](#code-of-conduct)
- [License](#license)
   
## Inputs

| Parameter       | Is Required | Description                                        |
| --------------- | ----------- | -------------------------------------------------- |
| `ltm-host-name` | true        | The hostname of the Local Traffic Manager (LTM)    |
| `ltm-username`  | true        | Username of F5 LTM User                            |
| `ltm-password`  | true        | Password of F5 LTM User                            |
| `ltm-pool-name` | true        | The pool to enable the member in                   |
| `current-host`  | true        | The hostname of the current machine being deployed |

## Outputs
No Outputs

## Example

```yml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - run: ./deploy.sh 
      
      - uses: im-open/enable-f5-pool-member@v1.0.1
        with:
          ltm-host-name: 'devlb.mycompany.com'
          ltm-username: 'operator-svc-dev'
          ltm-password: ${{ secrets.F5_PASSWORD }}
          ltm-pool-name: '/Dev/api.dev.mycompany.com.https.443'
          current-host: 'waq2-abcd'
```


## Contributing

When creating new PRs please ensure:
1. For major or minor changes, at least one of the commit messages contains the appropriate `+semver:` keywords listed under [Incrementing the Version](#incrementing-the-version).
2. The `README.md` example has been updated with the new version.  See [Incrementing the Version](#incrementing-the-version).
3. The action code does not contain sensitive information.

### Incrementing the Version

This action uses [git-version-lite] to examine commit messages to determine whether to perform a major, minor or patch increment on merge.  The following table provides the fragment that should be included in a commit message to active different increment strategies.
| Increment Type | Commit Message Fragment                     |
| -------------- | ------------------------------------------- |
| major          | +semver:breaking                            |
| major          | +semver:major                               |
| minor          | +semver:feature                             |
| minor          | +semver:minor                               |
| patch          | *default increment type, no comment needed* |

## Code of Conduct

This project has adopted the [im-open's Code of Conduct](https://github.com/im-open/.github/blob/master/CODE_OF_CONDUCT.md).

## License

Copyright &copy; 2021, Extend Health, LLC. Code released under the [MIT license](LICENSE).

[git-version-lite]: https://github.com/im-open/git-version-lite
