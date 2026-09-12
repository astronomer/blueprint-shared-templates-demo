# Blueprint shared templates demo

## Install shared templates

Install the shared-templates package in your Airflow project. Add to your `requirements.txt`:

```requirements
blueprint-shared-templates-demo @ https://github.com/astronomer/blueprint-shared-templates-demo/releases/download/v0.1.0/blueprint_shared_templates_demo-0.1.0-py3-none-any.whl
```

Or install using `uv`:

```bash
uv add "git+https://github.com/astronomer/blueprint-shared-templates-demo.git@v0.1.0"
```

And verify you see the example template:

```bash
uv run blueprint list            
                                            Available Blueprints                                             
┏━━━━━━━━━┳━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃ Name    ┃ Versions ┃ Description                                     ┃ Class   ┃ Location                 ┃
┡━━━━━━━━━╇━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━┩
│ example │ 1        │ Example Blueprint template from shared package. │ Example │ shared_templates.example │
└─────────┴──────────┴─────────────────────────────────────────────────┴─────────┴──────────────────────────┘
```

## Development

To work on this repository, install it in editable mode:

```bash
uv pip install -e .
```

The key to making Blueprint templates discoverable from an installed package is `"airflow_blueprint.blueprints"` in your pyproject.toml:

```toml
[project.entry-points."airflow_blueprint.blueprints"]
shared_templates = "shared_templates"
```

`[project.entry-points."airflow_blueprint.blueprints"]` advertises this package via [entry-points](https://packaging.python.org/en/latest/specifications/entry-points). The Blueprint loader scans the local path and every package discovered via `entry-points` for templates.

The goal is to keep this repository as simple as possible. A GitHub Action  Therefore, a GitHub release was created manually. 
