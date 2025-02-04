###########################################
#     Run various Ansible playbooks       #
###########################################

.PHONY: help
help: ## Display help message
	@grep -E '^[0-9a-zA-Z_-]+\.*[0-9a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'

.PHONY: upgrade_clean_flash
upgrade_clean_flash: ## upgrade EOS and clean up flash
	ansible-playbook playbooks/eos_upgrade.yml

.PHONY: upgrade_dont_clean_flash
upgrade: ## upgrade EOS and don't clean up space on flash
	ansible-playbook playbooks/eos_upgrade.yml --skip-tags flash-cleanup

.PHONY: downgrade_clean_flash
downgrade_clean_flash: ## downgrade EOS and clean up flash after but not beforehand
	ansible-playbook playbooks/eos_downgrade.yml

.PHONY: downgrade_dont_clean_flash
downgrade: ## downgrade EOS and don't clean up space on flash
	ansible-playbook playbooks/eos_downgrade.yml --skip-tags flash-cleanup
