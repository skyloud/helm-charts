# Common Helm Chart

The Common Helm Chart is an opinionated framework for deploying applications to Kubernetes. It provides a standardized structure and configuration options to streamline the deployment process.

## Features

- **Modularity**: The Common Helm Chart is designed to be modular, allowing you to easily add or remove components based on your application's requirements.
- **Configuration Management**: It provides a centralized configuration management system, allowing you to easily manage and override application-specific configurations.
- **Scalability**: The Common Helm Chart is built with scalability in mind, enabling you to effortlessly scale your application as your needs evolve.
- **Monitoring and Logging**: It includes built-in support for monitoring and logging, ensuring that you have visibility into the health and performance of your application.
- **Security**: The Common Helm Chart follows best practices for securing your application, including the use of secrets and RBAC (Role-Based Access Control).

## Getting Started

To get started with the Common Helm Chart, follow these steps:

1. Clone the repository: `git clone https://github.com/skyloud/helm-charts.git`
2. Customize the configuration: Modify the values in the `values.yaml` file to match your application's requirements.
3. Deploy the chart: Run `helm install common-chart charts/common` to deploy your application to Kubernetes.

For more detailed instructions and examples, please refer to the [documentation](https://github.com/skyloud/helm-charts).

## Contributing

We welcome contributions from the community! If you have any suggestions, bug reports, or feature requests, please open an issue or submit a pull request on our [GitHub repository](https://github.com/skyloud/helm-charts).

## License

The Common Helm Chart is released under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). Please refer to the [LICENSE](https://github.com/skyloud/helm-charts/blob/main/LICENSE.md) file for more information.

