# Base44 notes
- Black is a CLI formatter with no web UI. The preview (port 3000) serves the Sphinx docs via sphinx-autobuild, which reloads when you edit `docs/`.
- `blackd` (the HTTP API) runs from `src/` on port 45484 and restarts on Python changes (watchfiles). Test it with `curl -XPOST --data 'x  =  1' localhost:45484/`.
- `SETUPTOOLS_SCM_PRETEND_VERSION` gets around the version lookup from git. The first boot installs dependencies into named volumes and takes a few minutes.
- Tests: `docker compose -f docker-compose.base44.yml exec blackd sh -c "/venv/bin/pip install -q --group tests && /venv/bin/pytest -n auto"`.
- No external secrets are needed.
