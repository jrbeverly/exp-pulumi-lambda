.DEFAULT_GOAL:=help
SHELL:=/bin/bash

.PHONY: help init deploy destroy

init: ## Initialize an instance of the stack
	pulumi stack init website-$(shell echo $$RANDOM)
	pulumi config set aws:region us-west-2

deploy: ## Spin up the pulumi stack
	pulumi up
	pulumi stack

destroy: ## Tear down the pulumi stack
	pulumi destroy --yes
	pulumi stack rm --yes

help: ## Display this help message
	@awk 'BEGIN {FS = ":.*##"; printf "\nUsage:\n  make \033[36m\033[0m\n"} /^[a-zA-Z_-]+:.*?##/ { printf "  \033[36m%-15s\033[0m %s\n", $$1, $$2 } /^##@/ { printf "\n\033[1m%s\033[0m\n", substr($$0, 5) } ' $(MAKEFILE_LIST)