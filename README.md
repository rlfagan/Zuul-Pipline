# FOSSA Analysis Zuul Job Example

This project includes a Zuul pipeline configuration for running FOSSA license compliance and vulnerability analysis.

## Overview

The `fossa-analyze` job is designed to install the FOSSA CLI tool and run an analysis on the project's dependencies to ensure compliance with open source licenses and check for vulnerabilities.

## Zuul Configuration

The Zuul job is defined in the `.zuul.yaml` file, which includes the job definition and the secret for the FOSSA API key.

## Running the Job

The job is automatically triggered by Zuul when changes are pushed to the repository. It can also be manually
# FOSSA Analysis Zuul Job Example

This project includes a Zuul pipeline configuration for running FOSSA license compliance and vulnerability analysis.

## Overview

The `fossa-analyze` job is designed to install the FOSSA CLI tool and run an analysis on the project's dependencies to ensure compliance with open source licenses and check for vulnerabilities.

## Zuul Configuration

The Zuul job is defined in the `.zuul.yaml` file, which includes the job definition and the secret for the FOSSA API key.

## Running the Job

The job is automatically triggered by Zuul when changes are pushed to the repository. It can also be manually triggered through the Zuul dashboard, if configured.

## Security

The FOSSA API key is stored as an encrypted secret in the Zuul configuration. Ensure you replace the placeholder in the `.zuul.yaml` with your actual encrypted FOSSA API key.

## Contributing

Contributions to improve the FOSSA analysis job or any other part of the project are welcome. Please submit a pull request or open an issue for discussion.
