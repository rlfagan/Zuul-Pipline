# FOSSA Analysis Job Example

This project includes a Zuul pipeline configuration for running FOSSA license compliance and vulnerability analysis.

## Overview

The `fossa-analyze` job is designed to install the FOSSA CLI tool and run an analysis on the project's dependencies to ensure compliance with open source licenses and check for vulnerabilities.

## Zuul Configuration

The Zuul job is defined in the `.zuul.yaml` file, which includes the job definition and the secret for the FOSSA API key.

## Running the Job

The job is automatically triggered by Zuul when changes are pushed to the repository. It can also be manually

```YAML 	
# Fossa analysis
 
- job:
    name: fossa-analyze
    description: Analyze the project with FOSSA for license compliance
    run: playbooks/fossa-analyze.yaml
    secrets:
      - fossa_api_key

- secret:
    name: fossa_api_key
    data:
      fossa_api_key: !encrypted/pkcs1-oaep
        - <your encrypted FOSSA API key here>

```
```YAML
# Zuul pipeline configuration for running FOSSA license compliance and vulnerability analysis.

- hosts: all
  tasks:
    - name: Install FOSSA CLI
      shell: |
        curl -H 'Cache-Control: no-cache' https://raw.githubusercontent.com/fossas/fossa-cli/master/install-latest.sh | bash
      args:
        executable: /bin/bash

    - name: Run FOSSA Analyze
      shell: |
        FOSSA_API_KEY={{ fossa_api_key }} fossa analyze
      args:
        executable: /bin/bash
      environment:
        FOSSA_API_KEY: "{{ lookup('env', 'FOSSA_API_KEY') }}"

```
## Security

The FOSSA API key is stored as an encrypted secret in the Zuul configuration. Ensure you replace the placeholder in the `.zuul.yaml` with your actual encrypted FOSSA API key.

## Contributing

Contributions to improve the FOSSA analysis job or any other part of the project are welcome. Please submit a pull request or open an issue for discussion.

