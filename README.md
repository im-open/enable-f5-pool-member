# enable-f5-pool-member

An action that will enable an F5 pool member in a specific pool.
  
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
      
      - uses: im-open/enable-f5-pool-member@v1.0.0
        with:
          ltm-host-name: 'devlb.mycompany.com'
          ltm-username: 'operator-svc-dev'
          ltm-password: ${{ secrets.F5_PASSWORD }}
          ltm-pool-name: '/Dev/api.dev.mycompany.com.https.443'
          current-host: 'waq2-abcd'
```


## Code of Conduct

This project has adopted the [im-open's Code of Conduct](https://github.com/im-open/.github/blob/master/CODE_OF_CONDUCT.md).

## License

Copyright &copy; 2021, Extend Health, LLC. Code released under the [MIT license](LICENSE).
