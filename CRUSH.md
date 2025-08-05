# CRUSH.md

## Build & Validation Commands

- Syntax check tasks/main.yml:
  ```bash
  ansible-playbook tasks/main.yml --syntax-check
  ```
- Lint everything:
  ```bash
  ansible-lint .
  ```
- Run full role tests:
  ```bash
  ansible-playbook -i tests/inventory tests/test.yml
  ```
- Run a single test file:
  ```bash
  ansible-playbook -i tests/inventory tests/test.yml --tags <tag_or_task_name>
  ```

## Code Style Guidelines

- Use YAML with 2-space indentation; avoid tabs.
- Keys should be lowercase, words separated by underscores.
- Role layout:
  - defaults/main.yml for defaults.
  - vars/main.yml for static variables.
  - tasks/main.yml as entrypoint, with include_tasks for others (ubuntu.yml, macos.yml, etc.).
  - handlers/, meta/ as standard.
- Imports:
  - Prefer `include_tasks` over `import_tasks` for dynamic use.
  - Use `vars:` and `defaults:` appropriately in includes.
- Naming conventions:
  - Task names should be human-readable and start with a verb.
  - Variables in snake_case.
  - Avoid hardcoding paths; use variables.
- Error handling:
  - Use `failed_when` and `register` to catch and handle errors.
  - Prefer idempotent tasks and check modes.
- Testing:
  - Tag tasks for targeted testing.
  - Use check mode (`--check`) where possible.

## Other Configuration

- No specific Cursor or Copilot rules detected.

*Generated for agentic code assistants.*