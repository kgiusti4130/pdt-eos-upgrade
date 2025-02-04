###########################################
#     Run various Ansible playbooks       #
###########################################

.PHONY: help
help: ## Display help message
	@grep -E '^[0-9a-zA-Z_-]+\.*[0-9a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'

.PHONY: upgrade
upgrade: ## upgrade EOS
	ansible-playbook playbooks/eos_upgrade.yml

.PHONY: downgrade
downgrade: ## downgrade EOS
	ansible-playbook playbooks/eos_downgrade.yml

.PHONY: clean-flash
clean-flash: ## Remove all EOS image files other than the one currently running
	ansible-playbook playbooks/eos_clean_flash.yml
