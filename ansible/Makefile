###########################################
#     Run various Ansible playbooks       #
###########################################

.PHONY: help
help: ## Display help message
	@grep -E '^[0-9a-zA-Z_-]+\.*[0-9a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'

.PHONY: upgrade
upgrade: ## upgrade EOS on standalone switches (no MLAG)
	ansible-playbook playbooks/eos_upgrade.yml --skip-tags mlag_odd,mlag_even

.PHONY: upgrade_odd
upgrade_odd: ## upgrade EOS - Odd MLAG pairs
	ansible-playbook playbooks/eos_upgrade.yml --skip-tags mlag_even

.PHONY: upgrade_even
upgrade_even: ## upgrade EOS - Even MLAG pairs
	ansible-playbook playbooks/eos_upgrade.yml --skip-tags mlag_odd

.PHONY: upgrade_all
upgrade_all: ## upgrade EOS - Upgrade standalone - MLAG odd and even pairs
	ansible-playbook playbooks/eos_upgrade.yml

.PHONY: downgrade
downgrade: ## downgrade EOS on standalone switches (no MLAG)
	ansible-playbook playbooks/eos_downgrade.yml --skip-tags mlag_odd,mlag_even

.PHONY: downgrade_odd
downgrade_odd: ## downgrade EOS - Odd MLAG pairs
	ansible-playbook playbooks/eos_downgrade.yml --skip-tags mlag_even

.PHONY: downgrade_even
downgrade_even: ## downgrade EOS - Even MLAG pairs
	ansible-playbook playbooks/eos_downgrade.yml --skip-tags mlag_odd

.PHONY: downgrade_all
downgrade_all: ## downgrade EOS - downgrade standalone - MLAG odd and even pairs
	ansible-playbook playbooks/eos_downgrade.yml

.PHONY: clean-flash
clean-flash: ## Remove all EOS image files other than the one currently running
	ansible-playbook playbooks/eos_clean_flash.yml

.PHONY: verify_mlag
verify_mlag: ## Verify MLAG peer link is up, connected, ports aren't errdisabled due to upgrade & no active-partial connections
	ansible-playbook playbooks/eos_mlag_verify.yml
