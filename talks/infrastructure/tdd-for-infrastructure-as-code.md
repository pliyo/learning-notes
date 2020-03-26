# TDD for Infrastructure Code

[link](https://www.hashicorp.com/resources/tdd-for-infrastructure-code)

#

Tools for testing `Terraform`:

- `Terraform validate`: Your first step to prove that the syntax is fine. It's included in Terraform.
- `Terraform compliance`: focuses on negative testing by using BDD.
  For example by defining policies that your code must match. [See more](https://github.com/eerkunt/terraform-compliance)
- `Terratest`: Automated tests to verify that the plan works as expected. It will apply, test and destroy. Useful to test before you run it in production.
  [See more](https://github.com/gruntwork-io/terratest)

Conclusion: Still not enough testing tools for E2E.
