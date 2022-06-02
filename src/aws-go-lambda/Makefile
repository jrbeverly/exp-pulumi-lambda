.DEFAULT_GOAL:=help
SHELL:=/bin/bash

.PHONY: help init deploy destroy

init: ## Initialize an instance of the stack
	pulumi stack init lambda-$(shell echo $$RANDOM)
	pulumi config set aws:region us-west-2

build:: ## Build the Lambda
	GOOS=linux GOARCH=amd64 go build -o ./handler/handler ./handler/handler.go
	zip -j ./handler/handler.zip ./handler/handler

deploy: build ## Spin up the pulumi stack
	pulumi up
	pulumi stack

invoke: ## Invoke the AWS Lambda
	aws lambda invoke \
		--function-name $(shell pulumi stack output lambda) \
		--region $(shell pulumi config get aws:region) \
		--cli-binary-format raw-in-base64-out \
		--payload '"foo"' \
		output.json
	@cat output.json

destroy: ## Tear down the pulumi stack
	pulumi destroy --yes
	pulumi stack rm --yes

help: ## Display this help message
	@awk 'BEGIN {FS = ":.*##"; printf "\nUsage:\n  make \033[36m\033[0m\n"} /^[a-zA-Z_-]+:.*?##/ { printf "  \033[36m%-15s\033[0m %s\n", $$1, $$2 } /^##@/ { printf "\n\033[1m%s\033[0m\n", substr($$0, 5) } ' $(MAKEFILE_LIST)

