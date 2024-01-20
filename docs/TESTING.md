# IaC Testing

Like any code, IaC changes can introduce errors, failures, or breaking changes. Automated tests are an essential component of IaC to ensure code quality and reduce the risk of deployment failures, downtime, and associated costs. By detecting errors, failures, or breaking changes early in the process, automated tests can improve the readiness of deployed resources and ensure better service stability.

Symphony offers samples that help to write and execute both module and end-to-end tests for IaC module code and demonstrate how the tests can be integrated into the symphony workflows.

## Module tests

Module tests ensure that module code/configuration will create the resources successfully.

- [X] Module tests deploy the module resources, then validate the deployed resources & configurations, and finally tear down any deployed resources.
- [X] Slow to execute, but can be executed in parallel.
- [X] Have no dependency on any resource other than the module under test resources.

## End to End tests

End to End tests ensure that all resources deployed by one or more modules are working as expected.

- [X] End to End tests validate already deployed resources for a long-lived environment e.g. development or production
- [X] Fast to execute, and can be executed in parallel.
- [X] Depend on multiple modules, and sometimes the entire system resources.

## Terraform

All below test examples have an assumption for the working directory - should be [IAC/Terraform/test/terraform](./../IAC/Terraform/test/terraform/)

### End to End tests with Terratest

[Terratest](https://github.com/gruntwork-io/terratest) is a Go library that makes it easier to write automated tests for your infrastructure code. It provides a variety of helper functions and patterns for common infrastructure testing tasks, and offers good support for the most commonly used Azure resources.

1. Ensure Go 1.16 is installed, and the [Terratest Go environment](https://github.com/gruntwork-io/terratest/blob/master/examples/azure/README.md) is properly configured.

1. Run the tests.

    ```bash
    go test -v -timeout 1000s --tags=e2e_test
    ```
