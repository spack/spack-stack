include ../Make.user

CONFIG_DIR = $(STORE)/config

# These will be the prefixes of a bunch of GCCs, LLVMs and NVHPCs in the respective environments.
ALL_COMPILER_PREFIXES = $$($(SPACK) -e ../compilers/2-gcc find --format='{prefix}' gcc) $\
                        $$($(SPACK) -e ../compilers/3-llvm find --format='{prefix}' llvm nvhpc)

all: $(CONFIG_DIR)/compilers.yaml $(CONFIG_DIR)/upstreams.yaml

# Generate a compiler config file
$(CONFIG_DIR)/compilers.yaml:
	$(SPACK) compiler find --scope=user $(call compiler_bin_dirs, $(ALL_COMPILER_PREFIXES))

$(CONFIG_DIR)/upstreams.yaml:
	$(SPACK) config --scope=user add upstreams:system:install_tree:$(STORE)

include ../Make.inc
