# Makefile for common task execution
BASH_ALIASES_FILE := ~/.bash_aliases

# Aliases
# ll = ls -l
ALIAS_LL := ll

# la = ls -la
ALIAS_LA := la

# git-prune - removes all branches but master
ALIAS_GIT_PRUNE := "gitp"

# kubectl
ALIAS_KUBECTL := "k"

_bash_aliases_file:
	@if [ ! -f $(BASH_ALIASES_FILE) ]; then \
		echo "$(BASH_ALIASES_FILE) not found, creating..."; \
		touch $(BASH_ALIASES_FILE); \
	fi;

# checks if this alias is not in file and apply if needed
define _check_and_apply
	grep -qF ${1} $(BASH_ALIASES_FILE) || echo ${1} >> $(BASH_ALIASES_FILE)
endef

#
# Binding tasks
#
_bind_ll:
	@AL="alias $(ALIAS_LL)='ls -l'"; \
	$(call _check_and_apply, "$$AL");

_bind_la:
	@AL="alias $(ALIAS_LA)='ls -la'"; \
	$(call _check_and_apply, "$$AL");

_bind_git_prune:
	@AL="alias $(ALIAS_GIT_PRUNE)='git branch | grep -v "master" | xargs git branch -D'"; \
	$(call _check_and_apply, "$$AL");

_bind_kubectl:
	@AL="alias $(ALIAS_KUBECTL)='kubectl'"; \
	$(call _check_and_apply, "$$AL");

bind_aliases: _bash_aliases_file \
	_bind_ll \
	_bind_la \
	_bind_git_prune \
	_bind_kubectl \
