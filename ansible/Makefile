VENV ?= python_env
VDIR  = $(PWD)/$(VENV)

test: test_requirements
	ansible-lint *.yml

node-setup:
	ansible-playbook node-setup.yml

volume-setup:
	ansible-playbook volume-setup.yml

join-swarm:
	ansible-playbook join-swarm.yml

python_env: $(VDIR)/bin/python

test_requirements: python_env
	@echo "Installing test requirements"
	(. $(VDIR)/bin/activate && \
	 pip install -r requirements/common.txt)

$(VDIR)/bin/python:
	@echo "Creating virtual environment"
	virtualenv --system-site-packages $(VENV)
