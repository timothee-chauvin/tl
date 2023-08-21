# poetry

- initialize existing project:
`poetry init`

- add a dependency:
`poetry add {{package}}` 

- spawn a shell within the virtual environment:
`poetry shell`

- run a single command in the virtual environment:
`poetry run {{command}}`

- install dependencies from existing project:
`poetry install`

- configure virtualenvs to be within projects so IDEs can find them:
`poetry config virtualenvs.in-project true`

- show virtual environments:
`poetry env list`

- change python version:
<change version in pyproject.toml>
`poetry lock --no-update`
`poetry install`
