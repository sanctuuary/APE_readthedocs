[![Documentation Status](https://readthedocs.org/projects/ape-framework/badge/?version=latest)](https://ape-framework.readthedocs.io/en/latest/?badge=latest)

# APE Readthedocs Repo

The repository is used to provide detailed documentation on how to use the [APE library](https://github.com/sanctuuary/APE). A running instance available [here](https://ape-framework.readthedocs.io/en/latest/?badge=latest).

## How to build the documentation locally

1. Clone the repository and navigate to the root directory

2. Install the required packages

    ```bash
    pip install -r ./requirements.txt
    ```

3. Build the documentation

    ```bash
    make html
    ```

4. The documentation will be available in the `./_build/html` directory. Open the `index.html` file in your browser to view the documentation.
