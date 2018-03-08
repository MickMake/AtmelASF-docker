#
# Standard top level Makefile used to build a Docker container for MickMake projects.
# 

VERSIONS = DebianStretchBase 3.37

BASEDIR = $(shell pwd)

.PHONY: build push release clean list help

################################################################################
# Image related commands.

help:
	@cat README.md

build:
	@echo "Building for versions: $(VERSIONS)"
	$(foreach ver,$(VERSIONS), cd $(BASEDIR)/$(ver); make $@;)

push:
	@echo "Pushing to GitHub for versions: $(VERSIONS)"
	$(foreach ver,$(VERSIONS), cd $(BASEDIR)/$(ver); make $@;)

release:
	$(foreach ver,$(VERSIONS), cd $(BASEDIR)/$(ver); make $@;)

clean:
	@echo "Cleaning up for versions: $(VERSIONS)"
	$(foreach ver,$(VERSIONS), cd $(BASEDIR)/$(ver); make $@;)

list:
	@echo "Listing for versions: $(VERSIONS)"
	$(foreach ver,$(VERSIONS), cd $(BASEDIR)/$(ver); make $@;)

################################################################################
default: help

