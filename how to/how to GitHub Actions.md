## on
name of the GitHub event that triggers the workflow
```yml
on:
	push:
		branches: [ "main" ]
	pull_request:
		branches: [ "main" ]
```

## jobs
Sequence of tasks. One job will run on a single server at a time. By default it'll run in parallel, can overwrite with `publish: needs: `
`uses` : selects an **actions** 
`run` : runs a command-line command
```yml
jobs:
	test:
		runs-on: ubuntu-latest
		steps:
		- uses: actions/checkout@v3
			
		- name: Set up Python 3.8
		  uses: actions/setup-python@v3
		  with:
			  python-version: "3.8"
			
		- name: Install dependencies
		  run: |
			pip install -U pip
			pip install .
			pip install .[dev]
			
		- name: Test with pytest
		  run: |
			pytest
			
		- name: Test Coverage
		  run: |
			coverage run -m pytest
			coverage report -m
```